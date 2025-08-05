---
layout: page
title: Team
permalink: /team/
sort_order: ["tao", "riku", "sasu", "jp", "alexis", "ashwin", "henri", "yongchao", "amy"]
past_order: ["joonas", yangli", "xinyang"]
---

<style>

.team-members {
    display: flex;
    align-items: flex-end; /* Align text at the bottom of image */
}

.image-cell {
    width: 30%;
}

.member-image {
    max-width: 100%; /* Ensures the image is responsive */
    height: 150px;
    width: auto; /* Maintain aspect ratio */   
    padding: 0px; 
    bottom: 0;
    object-fit: cover; /* or cover */
    vertical-align: bottom;
}
.member-info {
    vertical-align: bottom;
}
</style>

<h2>Our Team</h2>

<p> Our team consists of members from Aalto University, University of Helsinki, and VTT. </p>

<div id="team-members">
    {% assign ordered_members = "" | split: "" %}  <!-- Initialize an empty array -->
    {% for identifier in page.sort_order %} <!-- Add member to the array -->
        {% assign member = site.team | where: "identifier", identifier | first %}
        {% if member %}
            {% assign ordered_members = ordered_members | push: member %}  
        {% endif %}
    {% endfor %}
    <table>
        <tr>
        {% for member in ordered_members %}
        {% assign loopindex = forloop.index | modulo: 3 %}
        {% if loopindex == 1 %}
        </tr>
        <tr>
        {% endif %}
            <td class="image-cell">
                <img class="member-image" src="{{ member.img | prepend: '/team/' }}" alt="{{ member.title }}"><br/>
                <a href="{{ member.url }}">{{ member.title }}</a> 
                <p> {{ member.role }}, <br/> <em>{{ member.organization_full}}</em> </p>
            </td>
        {% endfor %}
        </tr>            
    </table>
</div>

<!-- <h2>All Team Members</h2>
<ul>
    {% for member in site.team %}
        <li>{{member.identifier}} - {{ member.title }} - {{ member.organization_full }}</li>
    {% endfor %}
</ul> -->
