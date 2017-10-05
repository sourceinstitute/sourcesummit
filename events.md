---
layout: page
cover: '/img/Stuttgart3_022.jpg'
navigation_title: Events
permalink: /events/
---


<div class="home">

    {% capture currentDate %}{{'now' | date: '%s' }}{% endcapture %}

    <div class="clearfix">

      <h2 class="event-time-heading fix-top">Future {% if site.event_label %} {{site.event_label}} {% else %} Events {% endif %} </h2>

      {% for post in site.posts reversed %}

        {% capture blogDate %}{{post.date | date: '%s' }}{% endcapture %}
        {% if blogDate >= currentDate %}
          <a href="{{ post.url | prepend: site.baseurl }}">
            {% if post.cover %}
            <div class="event-sqaure" style="background-image:url({{post.cover}});">
            {% else %}
            <div class="event-sqaure" style="background-image:url(img/Stuttgart3_022.jpg);">
            {% endif %}
            {% if post.scheduled %}
              <h2>{{ post.title }} <span>{{ post.date | date: "%b %-d, %Y" }}</span></h2>
            {% else %}
              <h2>{{ post.title }}</h2>
            {% endif %}
               <div class='event-square-overlay'></div>
            </div>

          </a>
        {% endif %}
      {% endfor %}
    </div>

    <div class="clearfix">

      <h2 class="event-time-heading">Past {% if site.event_label %} {{site.event_label}} {% else %} Events {% endif %} </h2>
      {% for post in site.posts %}

        {% capture blogDate %}{{post.date | date: '%s' }}{% endcapture %}

        {% if blogDate < currentDate and post.scheduled == true %}

          <a href="{{ post.url | prepend: site.baseurl }}">
            {% if post.cover %}
            <div class="event-sqaure" style="background-image:url({{post.cover}});">
            {% else %}
            <div class="event-sqaure" style="background-image:url(http://app-beacon.com/wp-content/uploads/2015/05/events.jpg);">
            {% endif %}
              <h2>{{ post.title }} <span>{{ post.date | date: "%b %-d, %Y" }}</span></h2>
              <div class='event-square-overlay'></div>
            </div>

          </a>

        {% endif %}

      {% endfor %}
    </div>

</div>
