---
layout: default
title: "Israel Bustillos"
---

<div class="grid grid-cols-3 gap-12 my-4 md:my-8">
  {% for post in site.posts %}
    {% if forloop.index == 1 %}

        <div class="col-span-3 grid grid-cols-4 gap-4 md:gap-12">
          <div class="sm:col-span-3 h-44 col-span-4 bg-gray-900 rounded-md">
          <img class="h-44 w-full rounded-md object-cover" src="{{ site.baseurl }}/assets/images/{{ post.image }}">
          </div>
          <div class="sm:col-span-1 col-span-4 md:col-span-3">
            <div class="text-sm text-gray-500"><time datetime="{{ post.date | date: "%Y-%m-%d" }}">{{ post.date | date_to_long_string }}</time></div>
            <div class="text-3xl font-semibold mt-2">{{ post.title }}</div>
            <div class="mt-4">{{ post.content }}</div>
            <div class="flex space-x-2 mt-2">
              {% for tag in post.tags %}
                <div class="bg-gray-900 text-xs text-white p-1 rounded-md">{{ tag }}</div>
              {% endfor %}
            </div>
            <a href="{{ post.url }}" class="text-blue-500 text-small mt-2 block">
            Go to post
            </a>
          </div>
        </div>
    {% else %}
      <a href="{{ post.url }}" class="block col-span-3 md:col-span-1">
        <div class="bg-gray-900 h-44 rounded-md"></div>
        <div class="text-sm text-gray-500 mt-4"><time datetime="{{ post.date | date: "%Y-%m-%d" }}">{{ post.date | date_to_long_string }}</time></div>
        <div class="text-3xl font-semibold mt-2">{{ post.title }}</div>
        <div class="mt-2">{{ post.content }}</div>



        {% for tag in post.tags %}
          {% assign tag_slug = tag | slugify: "raw" %}
          <a class="tag-link"
            href={{ site.baseurl | append: "/tags/" | append: tag_slug | append: "/" }}
            rel="category tag">
            #{{ tag }}
          </a>
        {% endfor %}


      </a>
    {% endif %}

{% endfor %}

</div>
