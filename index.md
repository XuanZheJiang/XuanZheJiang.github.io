---
layout: default
---

<body>
  <div class="index-wrapper">
    <div class="aside">
      <div class="info-card">
        <h1>Xuanzhe Jiang</h1>
        <a href="http://weibo.com/2414696153" target="_blank"><img src="/images/HomePic/weibo192.png" alt="" width="25"/></a>
        <a href="https://twitter.com/cocoJGCM" target="_blank"><img src="/images/HomePic/twitter192.png" alt="" width="25"/></a>
        
      </div>
      <div id="particles-js"></div>
    </div>

    <div class="index-content">
      <ul class="artical-list">
        {% for post in site.categories.blog %}
        <li>
          <a href="{{ post.url }}" class="title">{{ post.title }}</a>
          <div class="title-desc">{{ post.description }}</div>
        </li>
        {% endfor %}
      </ul>
    </div>
  </div>
</body>
