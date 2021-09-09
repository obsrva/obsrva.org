---
title: Vulnerability Advisories
layout: post
permalink: advisories

hero:
  image: /assets/uswds/img/camera.png
  callout:
    alt: "Obsrva"
    text: Vulnerability Advisories
  button:
    href: 
    text: 
    number: 
    enable: false
  link:
    text: Link to more about that priority
    href: /link/
  content: Obsrva coordinates with product vendors to publish vulnerability advisories on obsrva.org/advisories. Advisories allow customers, blue and red team operators, and the broader research community to access technical details and research methodology.
---

<section class="grid-container usa-section">
    <div class="grid-row grid-gap">
    <div class="tablet:grid-col-4">
        <h2 class="font-heading-xl margin-top-0 tablet:margin-bottom-0">All Advisories</h2>
    </div>
    <div class="tablet:grid-col-8 usa-prose">
    <!-- Start of Advisory Group -->
        <div class="accordion" id="accordionExample">
        <div class="accordion-item">
            <h2 class="accordion-header" id="headingOne">
            <button class="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#collapseOne" aria-expanded="true" aria-controls="collapseOne">
                <strong>[CVE-2021-3441]  </strong>  HP Officejet - ‘AirPrint’ Cross Site Scripting (XSS)
            </button>
            </h2>
            <div id="collapseOne" class="accordion-collapse collapse show" aria-labelledby="headingOne" data-bs-parent="#accordionExample">
            <div class="accordion-body">
                <br>
                <p><strong>Overview:</strong> Stored cross-site scripting (XSS) in the embedded webserver of certain HP OfficeJet Printers—including the 4630 e-All-in-One Printer and 7110 Wide Format ePrinter— enables remote unauthenticated attackers to introduce arbitrary JavaScript via the <code>printer name</code> and <code>printer location</code> fields.</p>
                <p> <strong>Credit: </strong> Tyler Butler</p>
                <p> <strong>Disclosure Date: </strong>2021-08-22</p>
                <p><strong> Advisory Link: </strong> <a href="/2021/08/22/CVE-2021-3441.html">CVE-2021-3441</a></p>
            </div>
            </div>
        </div>
        <div class="accordion-item">
            <h2 class="accordion-header" id="headingTwo">
            <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">
                <strong>[CVE-2021-35956]  </strong> AKCP sensorProbe - 'Multiple' Cross Site Scripting (XSS)
            </button>
            </h2>
            <div id="collapseTwo" class="accordion-collapse collapse" aria-labelledby="headingTwo" data-bs-parent="#accordionExample">
            <div class="accordion-body">
                <br>
                <p><strong>Overview:</strong> Stored cross-site scripting (XSS) in the embedded webserver of AKCP sensorProbe before SP480-20210624 enables remote authenticated attackers to introduce arbitrary JavaScript via the <code>Sensor Description</code>, <code>Email (from/to/cc)</code>, <code>System Name</code>, and <code>System Location</code> fields.</p>
                <p> <strong>Credit: </strong> Tyler Butler</p>
                <p> <strong>Disclosure Date: </strong> 2021-06-06</p>
                <p><strong> Advisory Link: </strong> <a href="/2021/06/06/CVE-2021-35956.html">CVE-2021-35956</a></p>
            </div>
            </div>
        </div>
        </div>
        <!-- End of Advisory Group -->
    </div>
    </div>
</section>