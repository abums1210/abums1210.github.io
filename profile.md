---
layout: default
title: Profile
permalink: /profile/
---

<div class="profile-page-container">
  <div class="profile-card">
    <div class="profile-avatar-wrap">
      <img src="{{ site.avatar }}" alt="{{ site.name }}" class="profile-avatar" />
    </div>
    <h1 class="profile-name">{{ site.name }}</h1>
    <p class="profile-bio">{{ site.description }}</p>
    
    <div class="profile-support-badges">
      <a href="https://ko-fi.com/abums1210" target="_blank" rel="noopener" class="support-badge kofi-badge" title="Support on Ko-fi">
        <svg class="badge-icon" viewBox="0 0 24 24" width="18" height="18" fill="currentColor">
          <path d="M23.881 8.948c-.773-4.085-4.859-4.593-4.859-4.593H.723c-.604 0-.679.798-.679.798s-.082 7.324-.022 11.822c.164 2.424 2.586 2.672 2.586 2.672s8.267-.023 11.966-.049c2.438-.426 2.683-2.566 2.683-2.566l.035-1.921s3.784-.047 5.068-.85c1.284-.803 1.521-5.309 1.521-5.309zm-5.069 3.018s-.035 1.059-.723 1.059c-.688 0-4.032-.012-4.032-.012l-.014-3.834s3.784-.035 4.39.024c.606.059.379 2.763.379 2.763zM5.597 12.392c.604-.847 2.16-2.563 2.16-2.563s1.556 1.716 2.16 2.563c.604.847.452 1.834-.239 2.375-.691.541-1.688.389-1.921-.102-.233.491-1.23.643-1.921.102-.691-.541-.843-1.528-.239-2.375z"/>
        </svg>
        <span>Support on Ko-fi</span>
      </a>
      <a href="https://patreon.com/cw/abums1210" target="_blank" rel="noopener" class="support-badge patreon-badge" title="Support on Patreon">
        <svg class="badge-icon" viewBox="0 0 24 24" width="18" height="18" fill="currentColor">
          <path d="M15.386.524c-4.764 0-8.64 3.876-8.64 8.64 0 4.75 3.876 8.613 8.64 8.613 4.75 0 8.614-3.864 8.614-8.613C24 4.4 20.136.524 15.386.524M.003 23.5h4.22V.524H.003"/>
        </svg>
        <span>Support on Patreon</span>
      </a>
    </div>

    <div class="profile-social-section">
      {% include social_cards.html %}
    </div>

    <div class="profile-about-section">
      <h2 class="profile-section-title">About this Blog</h2>
      <ul class="profile-about-list">
        <li>Just read through First Drops, you might have an idea about what's going on here.</li>
        <li>There is no particular genre I am trying to fulfill here. All kinds of stuff will be tried out.</li>
        <li>Since this is a blog, of all sites.</li>
        <li>Blog hosted on GitHub Pages and runs on Jekyll, which generates static sites from Markdown language.</li>
        <li>Based on a tweaked template of Jekyll called <a href="https://github.com/barryclark/jekyll-now" target="_blank" rel="noopener">jekyll-now</a> by Barry Clark. Further added CSS enhancments with Antigravity IDE.</li>
        <li>Posts will be on both Tamil and English.</li>
      </ul>
    </div>
  </div>
</div>
