---
layout: page
title: Team
permalink: /team/
sort_order: ["tao", "sasu", "riku", "jp", "alexis", "yongchao", "ashwin"]
past_order: ["joonas", yangli", "xinyang"]
---

<style>
.image-cell {
    width: 20%;
}
.text-cell {
    width: 80%;
}
img {
    max-width: 100%; /* Ensures the image is responsive */
    height: auto; /* Maintains aspect ratio */
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
    {% for identifier in page.sort_order %}
        {% assign member = site.team | where: "identifier", identifier | first %}
        {% if member %}
            {% assign ordered_members = ordered_members | push: member %}  <!-- Add member to the array -->
        {% endif %}
    {% endfor %}
    
    <table>
    {% for member in ordered_members %}
    <tr>
        <div class="team-member" data-org="{{ member.organization }}" data-org-name="{{ member.organization_full}}" >
            <td class="image-cell"> 
                <img class="member-image" src="{{ member.img | prepend: '/team/' }}" alt="{{ member.title }}">
            </td>
            <td class="text-cell">    
            <div class="member-details">
                <h3><a href="{{ member.url }}">{{ member.title }}</a></h3> 
                <p> {{ member.role }}, {{ member.organization_full}}</p>
                <p> {{member.bio_brief}} </p>
            </div>
            </td> 
        </div>
    </tr>    
    {% endfor %}
    </table>
</div>
<!-- <h2>All Team Members</h2>
<ul>
    {% for member in site.team %}
        <li>{{member.identifier}} - {{ member.title }} - {{ member.organization_full }}</li>
    {% endfor %}
</ul> -->



<!-- <h2>All Team Members</h2>
<ul>
    {% for member in site.team %}
        <li>{{member.identifier}} - {{ member.title }} - {{ member.organization_full }}</li>
    {% endfor %}
</ul> -->



