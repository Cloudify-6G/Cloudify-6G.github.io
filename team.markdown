---
layout: page
title: Team
permalink: /team/
sort_order: ["tao", "sasu", "riku", "jp", "alexis", "ashwin", "henri", "yongchao", "amy"]
past_order: ["joonas", yangli", "xinyang"]
---

<style>
.image-cell {
    width: 30%;
}

img {
    max-width: 60%; /* Ensures the image is responsive */
    height: auto; /* Maintains aspect ratio */
    object-fit: contain; /* or cover */
}
</style>

<script>
    function filterTeam(org) {
        console.log("Filtering Organization", org);
        const members = document.querySelectorAll('.team-member');
        console.log("Total members found:", members.length);

        members.forEach(member => {
            console.log("Checking member:", member.querySelector('h3').innerText); 
            if (org === 'all' || member.getAttribute('data-org') === org) {
                member.style.display = 'block';
                console.log("Showing member");
            } else {
                member.style.display = 'none';
                console.log("Hiding member");
            }
        });
    }

    document.addEventListener("DOMContentLoaded", function() {
        filterTeam('all');
    });
</script>

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
                <img class="member-image" src="{{ member.img | prepend: '/team/' }}" alt="{{ member.title }}">
                <h4><a href="{{ member.url }}">{{ member.title }}</a></h4> 
                <p> {{ member.role }}, <br/> {{ member.organization_full}}</p>
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
