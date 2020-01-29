---
permalink: /edtech/
title: "Educational Technology"
#excerpt: "This post should [...]"
---

According to Wikipedia, EdTech is defined as the following:

> Educational technology is the use of both physical hardware, software, and educational theoretic to facilitate learning and improving performance by creating, using, and managing appropriate technological processes and resources.

During my decade in IT support, I have spent a large amount of my time working on various different server and cloud based systems. This section of my site as well as blog posts will discuss various useful things I've worked on over the years.

# Server operating systems / technologies

* Various versions of [Ubuntu](www.ubuntu.com)
* Various versions of [Debian](www.debian.org)
* Various versions of MacOS server and the server app that was developed by Apple when they stopped producing the MacOS server product
* Various versions of [ESXi](https://www.vmware.com/uk/products/esxi-and-esx.html) and [VCenter](https://www.vmware.com/uk/products/vcenter-server.html)
Various versions of [Windows server](https://www.microsoft.com/en-gb/cloud-platform/windows-server)

My preference has always been for Linux based operating systems, but during the years in a school-based environment I have spent considerable time in a Windows based environment, so have learned a lot about this platform also!

# Communication systems

* [Microsoft Exchange](https://products.office.com/en-gb/exchange/microsoft-exchange-server) 2010
* Live@Edu and later Office 365
* In depth knowledge of GSuite and supporting tools, such as [GAM](https://github.com/jay0lee/GAM) and [GCDS](https://support.google.com/a/answer/6120989?hl=en) 

# GSuite for Education

Before I write any blogposts on GSuite, we have now deployed this for all schools within the MAT, which I work for. I have seen first hand the benefits of GSuite and the collaboration it enables.

I have seen staff video conference and work collaboratively on schemes of work, share completed resources with other users and use Google classroom for both lessons and revision materials. I have used Google Sites to publish resources from our annual conference to all staff.

These are small examples of what GSuite has been utilised for within our trust.

I strongly believe that GSuite can save staff valuable time, which allows them to do the most important things, which in turn improves the education provided to the students.

# Blog posts

EdTech related blog posts will be linked to below...

{% assign tags_max = 0 %}
{% for tag in site.tags %}
  {% if tag[1].size > tags_max %}
    {% assign tags_max = tag[1].size %}
  {% endif %}
{% endfor %}



{% for i in (1..tags_max) reversed %}
  {% for tag in site.tags %}
    {% if tag[1].size == i %}
    {% if tag[0] == "edtech" %}

<div class="entries-{{ page.entries_layout | default: 'list' }}">
          {% for post in tag.last %}
            {% include archive-single.html type=page.entries_layout %}
          {% endfor %}
</div>
<a href="#page-title" class="back-to-top">{{ site.data.ui-text[site.locale].back_to_top | default: 'Back to Top' }} &uarr;</a></section>
    {% endif %}
    {% endif %}
  {% endfor %}
{% endfor %}