---
title: Vulnerability Research Library
description: The research library is a repository of iOT and embedded devices availabale to be loaned for independent security research. Check out catalog below and request a device to collaborate on our research.
permalink: /library/

layout: post
sidenav: library
subnav:
  - text: Request Form
    href: '#request-form'
  - text: Video Encoders
    href: '#video-encoders'
  - text: Printers
    href: '#printers'


hero:
  image: /assets/uswds/img/camera.png
  callout:
    alt: "Obsrva"
    text: Vulnerability Research Library
  button:
    href: 
    text: 
    number: 
    enable: false
  link:
    text: Link to more about that priority
    href: /link/
  content: The research library is a repository of iOT and embedded devices availabale to be loaned for independent security research.
---

The research library is a repository of iOT and embedded devices availabale to be loaned for independent security research. Check out catalog below and request a device to collaborate on our research.


## Request Form 

If you're interested in using one of the devices in the library for research, please fill out the interest form below. Someone from Obsrva will contact you within 3-5 business days.  




 <form name="library" method="POST" data-netlify="true">
    <div class="mb-3">
      <label for="fname" class="form-label">Name</label>
      <input type="name" class="form-control" id="inputForName" placeholder="Tyler Butler" name="name">
    </div>
    <div class="mb-3">
      <label for="Email" class="form-label">Email</label>
      <input type="email" class="form-control" id="inputforEmail" placeholder="name@example.com"  name="email" >
    </div>
      <div class="mb-3">
      <label for="Device" name="device" class="form-label">Device</label>
      <input type="Device" class="form-control" id="inputforEmail" placeholder="TER-001">
    </div>
    <div class="mb-3">
      <label for="subject" class="form-label">Research Plan</label>
      <textarea  type="message" class="form-control" name="message"  id="inputforMessage" rows="3" placeholder="I'm interested in building upon previous work on CVE-2021-3441 in order to find pathways to escalate the vulnerability to RCE 🔥"></textarea>
    </div>
    <button type="submit" value="Submit" class="btn btn-primary mb-3">Submit</button>
  </form>

## Enviormental Monitors

### AKCP 

<div class="card mb-3 border-0" style="width: 100%;">
  <div class="row g-0">
    <div class="col-md-4">
      <img src="/assets/img/lib/sensorProbe2-demo.jpg" class="img-fluid rounded-start" alt="...">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title"><b>AKCP SensorProbe2 detector Sensor SP2 </b></h5>
        <p class="card-text">Vendor Description: The SP2 is an <a href="https://en.wikipedia.org/wiki/Simple_Network_Management_Protocol">SNMP</a> enabled and Web-Based Environmental Monitoring Device.</p>
        <p class="card-text">
        <ul class="list-group list-group-flush">
        <li class="list-group-item">Library ID: #AKC-001    </li>
        <li class="list-group-item">Point of Contact: <a href="mailto:contact@obsrva.org">contact@obsrva.org</a></li>
        <li class="list-group-item">Vendor Website: <a href="https://www.akcp.com/akcp-products/sensorprobe-series/sensorprobe2/">akcp.com</a></li>
        <li class="list-group-item">Obsrva Research: <a href="/2021/06/06/cve-2021-35956)">CVE-2021-35956</a></li>
        </ul>
        </p>
      </div>
    </div>
  </div>
</div>


## Printers

### HP Inc

<div class="card mb-3 border-0" style="width: 100%;">
  <div class="row g-0">
    <div class="col-md-4">
      <img src="/assets/img/lib/hp.png" class="img-fluid rounded-start" alt="...">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title"><b>HP Officejet 4630 e-All-in-One Printer series</b></h5>
        <p class="card-text">Vendor Description: The HP Officejet 4630 is a mid-range network enabled printer featuring an embedded webserver for print, scan, and maintenance activities</p>
        <p class="card-text">
        <ul class="list-group list-group-flush">
        <li class="list-group-item">Library ID: #HPX-001   </li>
        <li class="list-group-item">Point of Contact: <a href="mailto:contact@obsrva.org">contact@obsrva.org</a></li>
        <li class="list-group-item">Vendor Website: <a href="https://support.hp.com/us-en/product/hp-officejet-4630-e-all-in-one-printer-series/5305049/product-info">support.hp.com</a></li>
        <li class="list-group-item">Obsrva Research: <a href="/2021/08/22/cve-2021-3441">CVE-2021-3441</a></li>
        </ul>
        </p>
      </div>
    </div>
  </div>
</div>


## Video Encoders

### Teradek

<div class="card mb-3 border-0" style="width: 100%;">
  <div class="row g-0">
    <div class="col-md-4">
      <img src="/assets/img/lib/cube.jpg" class="img-fluid rounded-start" alt="...">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title"><b>Teradek Cube 305 Encoder</b></h5>
        <p class="card-text">Vendor Description: The Cube 555 is a camera-top wireless SD video encoder that works with composite cameras. The device streams via dual-band MIMO WiFi, Ethernet, or a single 3G/4G USB modem.</p>
        <p class="card-text">
        <ul class="list-group list-group-flush">
        <li class="list-group-item">Library ID: #TER-001  </li>
        <li class="list-group-item">Point of Contact: <a href="mailto:contact@obsrva.org">contact@obsrva.org</a></li>
        <li class="list-group-item">Vendor Website: <a href="https://www.teradek.com">teradek.com</a></li>
        </ul>
        </p>
      </div>
    </div>
  </div>
</div>



### Avigilon

<div class="card mb-3 border-0" style="width: 100%;">
  <div class="row g-0">
    <div class="col-md-4">
      <img src="/assets/img/lib/avigilon-analog-encoder.14b34950.png" class="img-fluid rounded-start" alt="...">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title"><b>Avigilon 4-Port H.264 Analog Video Encoder</b></h5>
        <p class="card-text">Vendor Description: Converts a standard analog video feed into a digital stream, enabling digital images to be sent over an IP network. You can then view live images on your IP network using video management software and add IP-based cameras as your budget allows.</p>
        <p class="card-text">
        <ul class="list-group list-group-flush">
        <li class="list-group-item">Library ID: #AVG-001  </li>
        <li class="list-group-item">Point of Contact: <a href="mailto:contact@obsrva.org">contact@obsrva.org</a></li>
        <li class="list-group-item">Vendor Website: <a href="https://www.avigilon.com/products/video-infrastructure/enc">avigilon.com</a></li>
        </ul>
        </p>
      </div>
    </div>
  </div>
</div>

