---
title: Vulnerability Advisories
layout: post
permalink: advisories
---


<section class="grid-container usa-section">
    <div class="grid-row grid-gap">
    <div class="tablet:grid-col-4">
        <h2 class="font-heading-xl margin-top-0 tablet:margin-bottom-0">Latest Products</h2>
    </div>
    <div class="tablet:grid-col-8 usa-prose">
        {% for post in site.posts %}
        {% assign foo = post.tag %}
        {% if post.tag == 'cve' %}
        <div class="card border-light mb-3" style="width: 100%;">
            <div class="card-header">
            <a href="{{post.url}}" style="color:black;">{{ post.title }}</a>
            </div>
            <div class="card-body">
            <!-- <p class="card-text"><i>{{post.author}} | published {{post.date | date: "%b %d, %y" }}</i></p> -->
            <p class="card-text">{{ post.lead }}</p>
            <p class="card-text"><small class="text-muted">{{post.author}} | Published {{post.date | date: "%b %d, %y" }}</small></p>
            </div>
        </div>
        <br>
        {% endif %}
        {% endfor %}
    </div>
    </div>
</section>