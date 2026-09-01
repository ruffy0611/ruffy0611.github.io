---
layout: default
# dev posts list (category: dev)
---
{%- include multi_lng/get-pages-by-lng.liquid pages = site.posts -%}
{%- assign filtered_posts = lng_pages | where_exp: "post", "post.category == 'dev'" | sort: 'date' | reverse -%}

<div class="multipurpose-container">
  <h1>{{ site.data.lang[lng].dev.page_header }}</h1>
</div>

<div class="post-list-header"></div>
<div class="post-list-container">
  {% for post in filtered_posts -%}
    {% include post-list/post-thumbnail-data.liquid post = post -%}
    {% include post-list/post-thumbnail-html.html
      url = post_url
      image = image
      max_width = max_width
      display = display
      title = page_title
      title_sub = title_sub
      date = post_date
      read_time = read_time
      comment_style = comment_style
    %}
  {% else -%}
    <div class="multipurpose-container">
      <p>{{ site.data.lang[lng].dev.no_posts_text }}</p>
    </div>
  {% endfor -%}
</div>
