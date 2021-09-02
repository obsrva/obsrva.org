---
layout: cve
title:  "MonkeyType.com Vulnerability Disclosure"
date: 2021-08-22 09:34:43 -0400
categories: "About"
author: Tyler Butler
img: /assets/img/posts/2021-09-01-MONKEYTYPE/preview.png
description: Obsrva disclosed a stored cross-site scripting vulnerability in the tribe chat option of dev.monkeytype.com, allowing malicious users to inject arbitrary JavaScript script via (1) message and (2) name parameters in the chat room.
lead: Obsrva disclosed a stored cross-site scripting vulnerability in the tribe chat option of dev.monkeytype.com, allowing malicious users to inject arbitrary JavaScript script via (1) message and (2) name parameters in the chat room.
tag: featured
advisory: 

hero:
  image: /assets/uswds/img/camera.png
  callout:
    alt: "MonkeyType.com"
    text: "Stored Cross-Site Scripting"
  button:
    href:
    text:
    number:
    enable: false
  link:
    text: Link to more about that priority
    href: /link/
  content: Obsrva disclosed a stored cross-site scripting vulnerability in the tribe chat option of dev.monkeytype.com, allowing malicious users to inject arbitrary JavaScript script via (1) message and (2) name parameters in the chat room.
---  

# Executive Overview

In May 2021, independent security researcher Tyler Butler found several critical vulnerabilities in [monkeytype.com](https://monkeytype.com), a popular open-source typing-test application with a booming community of over 100k daily unique visitors. The vulnerabilities included stored cross-site scripting and user impersonation in the tribe chat room feature, as well as an authentication bypass vulnerability enabling any user to set arbitrary test scores and jump to the top of the leaderboard. Tyler engaged the site developer on discord and github, ultimately confirming all vulnearbilities were triaged. The developer was an excpetional partner in addressing the concerns, and even allowed a pull request to add a [security policy](https://monkeytype.com/security-policy) and [security.txt](https://monkeytype.com/.well-known/security.txt) file.   


**Index**   

+  Executive Overview 
+  About the Vendor 
+  Coordinated Disclosures 
    +  Stored Cross-Site Scripting via Tribe Chat 
    +  User Impersonation via Tribe Chat 
    +  Authenticated ByPass 
+  Drafting a Security Policy 
+  Bug Bounty with Huntr.Dev  
+  Wrapping Up  


# About the Vendor  

[Monkeytype](https://monkeytype.com) is a popular typing-test application with a growing online community. Started in early 2020, it’s quickly become one of the top typing test applications, boasting over 40 million page views. In late May, the lead developer announced some pretty impressive statistics for the site,

- 100k daily unique visitors  
- 228k registered accounts  
- 139 million started tests  
- 54 million completed tests  
- 2.22 billion seconds which is around 70 years of typing  

# Coordinated Disclosures 

*The following section details each vulnerability found includnig a proof of concept, statement addressing impact, and mitigation steps taken by the application developer.*

## Stored Cross-Site Scripting via Tribe Chat  

![](/assets/img/posts/2021-09-01-MONKEYTYPE/tribe_stored_xss.gif)  

**Disclosure Method**: According to the bug report [policy](https://github.com/Miodec/monkeytype) at the time of discovery, I engaged the application developer on [Discord Chat](https://discord.com/channels/713194177403420752/713196019206324306/847508937129590784) (also [here](https://discord.com/channels/713194177403420752/802651050099474532/847516976041820181)) and opened a [Github Issue](https://github.com/Miodec/monkeytype/issues/1476).  

**Vulnerability**: The monkeytype [Tribe Chat](https://dev.monkeytype.com/tribe) is vulnerable to stored cross-site scripting via the (1) message and (2) name parameters. While client side validation as implemented, it fell short of protecting malicious payloads that were injected directly in modified socket requests. To be exploited, a malicious user could create or join a chat room, send a normal message, intercepted the socket request and inject a payload into the name or message fields.

**Proof of Concept**: 


+ Configure [BurpSuite](https://portswigger.net/burp) to intercept browser traffic  
+ Navigate to https://dev.monkeytype.com/tribe  
+ Click on "create room"  
+ Turn on BurpSuite proxy interception  
+ Enter a new chat string  
+ Intercept the web socket traffic, and change the chat string to an XSS payload, example below.
+ Stop intercepting traffic, browse the chat room. The payload will execute. In this example, the payload will execute onclick  

*Shown below, a raw socket message is intercepted and modified by adding an svg alert message payload*  

![](/assets/img/posts/2021-09-01-MONKEYTYPE/tribe_xss.png)  


**Impact**: The impact of stored XSS in a chat room is **severe**. Once injected, the payload would be executed in the context of other user’s browsers who were within the same room. These payloads could be used to steal users authentication tokens, allowing complete account takeover. Making the vulnerability worse is the fact that tribe allows users to invite other’s to specefic chat rooms. Once a room has been successfully exploited with a XSS payload, a malicious user could then share the link to the specific chat room to others, increasing the number of potential victims.

**Mitigation**: The monkeyType developer eventually added client and serverside input validation to mitigate the impact of the vulnerability. 

```javascript
function sanitize(string) {
  const map = {
      '&': '&amp;',
      '<': '&lt;',
      '>': '&gt;',
      '"': '&quot;',
      "'": '&#x27;',
      "/": '&#x2F;',
  };
  const reg = /[&<>"'/]/ig;
  return string.replace(reg, (match)=>(map[match]));
}
```  

![](/assets/img/posts/2021-09-01-MONKEYTYPE/xss_mitigation.png)

## User Impersonation via Tribe Chat  

![](/assets/img/posts/2021-09-01-MONKEYTYPE/tribe_chat_impersonation.gif)

**Disclosure Method**: According to the bug report [policy](https://github.com/Miodec/monkeytype) at the time of discovery, I engaged the application developer on [Discord Chat](https://discord.com/channels/713194177403420752/802651050099474532/849819342615085116) and opened a [Github Issue](https://github.com/Miodec/monkeytype/issues/1503)   

**Vulnerability**:  User messages in the Tribe Chat can be impersonated due to improper authorization in the socket.io implementation. Malicious users can abuse current socket message authentication measures to create messages that appear to come from other users or system.

**Proof of Concept**: 

+  Go to a tribe chat room, ex: https://dev.monkeytype.com/tribe_1d849e  
+  Send a message, capturing the socket.io message.  

`42["mp_chat_message",{"isSystem":false,"isLeader":true,"message":"Hey this is still alice","from":{"id":"UocD_4qRZiXGbXf8AA-n","name":"alice"}}]`  
+  Modify the name parameter, and re-send  

`42["mp_chat_message",{"isSystem":false,"isLeader":true,"message":"Hey this is still alice","from":{"id":"UocD_4qRZiXGbXf8AA-n","name":"bob"}}]`  


**Impact**: Malicious users can impersonate others in the chat room, which could enable abusive behavior negatively affecting users.

**Mitigation**: At the time this vulnerability was discovered, the application developer had already addressed the issue in a not yet released patch. On June 3rd, the patch was merged into the developmenet site at dev.monkeytype.com (see issue [1503](https://github.com/Miodec/monkeytype/issues/1503))


## Authenticated ByPass    
  
![](/assets/img/posts/2021-09-01-MONKEYTYPE/inject_scores.png)    
*Shown above, the leaderboard is spoofed using a crafted request seen here being sent in BurpSuite*  


**Disclosure Method**: For the first time, I submitted this vulnerability through [huntr.dev](https://huntr.dev/bounties/1-other-Miodec/monkeytype/), a bug bounty platform that rewards developers and bug hunters for traiged vulnerabilities in open-source software. 

**Vulnerability**:  Users can bypass leaderboard controls and inject any object they want into the leaderboard by spoofing post requests to /checkLeaderboards. Malicious users can send specially crafted post requests and inject any user they want to the top of the leaderboard with any value words per minuet they want. Server does invalidate requests with cross-site scripting (XSS) payloads, therefore I believe this is not vulnerable to XSS.

**Proof of Concept**:  The following request will overwrite the leaderboard, injecting the user pwnville_foo into position 9 with a faked wpm of 200.  

```yaml
POST /checkLeaderboards HTTP/2
Host: us-central1-monkey-type.cloudfunctions.net
Content-Length: 750
Sec-Ch-Ua: " Not A;Brand";v="99", "Chromium";v="90"
Authorization: Bearer [redacted]
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.212 Safari/537.36
Content-Type: application/json
Accept: */*
Origin: https://monkeytype.com
Sec-Fetch-Site: cross-site
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://monkeytype.com/
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
Connection: close

{"data":{"uid":"aXi5udatSndUhoQR5pUtR6GpvGF3","lbMemory":{"time15":{"global":null,"daily":null},"time60":{"global":null,"daily":null}},"name":"pwnville_foo","banned":null,"verified":null,"discordId":null,"result":{"wpm":200.00,"rawWpm":200.00,"correctChars":250,"incorrectChars":6,"allChars":250,"acc":92,"mode":"time","mode2":15,"quoteLength":-1,"punctuation":false,"numbers":false,"timestamp":1622147912060,"language":"english","restartCount":0,"incompleteTestSeconds":0,"difficulty":"normal","testDuration":15.001134999999515,"afkDuration":0,"blindMode":false,"theme":"9009","tags":[],"consistency":83.22,"keyConsistency":45.56,"funbox":"none","bailedOut":false,"customText":null,"uid":"aXi5udatSndUhoQR5pUtR6GpvGF3","id":"vZkPA1dmzeUvaGQPkE4Z"}}}
```  

*Shown below, the fake user is now a top leader in words per minuete*  

![](/assets/img/posts/2021-09-01-MONKEYTYPE/leader.png)

**Impact**:  Using this vulnerability, malicious users can overwrite the entire leaderboard with username strings of their choosing, which could be used to deface the website.

**Migitaion**:  On the huntr.dev submission for this issue, the developer stated he is "Looking into moving to a token-based auth system for this endpoint. All the other cloud functions will be moved to the token system after this has been solved since the publicity of this (having the ability to alter public leaderboards) takes priority"  

# Bug Bounty with Huntr.Dev 

# Wrapping Up    


