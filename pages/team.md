---
title: Our Team
layout: page
permalink: team

hero:
  image: /assets/uswds/img/camera.png
  callout:
    alt: "Obsrva"
    text: Research Team
  button:
    href: 
    text: 
    number: 
    enable: false
  link:
    text: Link to more about that priority
    href: /link/
  content: 
---

<div class="card mb-3 border-0" style="width: 100%;">
  <div class="row g-0">
    <div class="col-md-4">
      <img src="https://res.cloudinary.com/tbutler-org/image/upload/v1603912192/me_clgeva.jpg" class="img-fluid rounded-start" alt="...">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title"><b>Tyler Butler</b> | <small class="text-muted">Founder & Lead Researcher</small></h5>
        <!-- <i class="fab fa-linkedin-in"></i>
        <i class="fab fa-twitter"></i>
        <i class="fab fa-github"></i>
        <i class="fas fa-envelope-open"></i> -->
        <p class="card-text">Tyler gained his undergraduate degree in Security and Risk Analysis from The Pennsylvania State University and started his cyber security career at Deloitte where he served clients as a penetration tester and red team operator. Tyler currently holds the eWPT and eJPT certifications, is credited with several CVE's including CVE-2021-35956 and CVE-2021-3441, and was nominated to the Motorola Solutions Bug Bounty Hall of Fame.</p>
        <p><i>Recent Publications</i></p>
          <!-- {% for post in site.posts %}
          {% if post.author == 'Tyler Butler' %}
            <a href="{{post.url}}" style="color:black;">{{post.title}}</a>
            <br>
          {% endif %}
          {% endfor %} -->
          <div class="list-group border-0">
          {% for post in site.posts limit:5 %}
          {% if post.author == 'Tyler Butler' %}
          <a href="{{post.url}}" class="list-group-item list-group-item-action border-0" aria-current="true">
            <div class="d-flex w-100 justify-content-between border-0">
              <h5 class="mb-1"><strong>{{post.title}}</strong></h5>
              <small>{{post.date |  date: "%b %d, %y"}}</small>
            </div>
            <p class="mb-1">{{post.lead | truncate: 80}}</p>
          </a>
             {% endif %}
          {% endfor %}
        </div>
        <!-- <p class="card-text"><small class="text-muted">Joined September 2021</small></p> -->
      </div>
    </div>
  </div>
</div>