---
title: "06-CDN"
draft: false
---

Tags: #system-design #cdn

# CDN - Content Delivery Networks

A cdn is a globally distributed of proxies servers, serving content to users from nearest data center. Generally static files like html/css/js,photos and videos are serverd  from CDNs. 

Serving content from CDN, improve website performace two ways:- 

- Users receive content from data center nearest to them.
- Your servers do not have to serve requests that the CDN fulfills.

### Pull CDN

Pull CDNs grab new content from your server when the first user requests for content.You leave the server and rewrite url to point to the CDNs. This results  are slower until the contents are cached on the CDNs 

- A TTL(time to live) determines how long the content is cached. 
- Pull CDN minimize storage space on the CDN, but can create redandent if files expire and pull before they have actually changed.  
- Sites with heavy trafic works well with Pull CDN. 
- Example, Site with dynamic content(news sites, blogs)

- First time content fetching can be slow(cache miss).

### Push CDN

Push CDNs receive new content whenever changes occurs on your server. You take full responsbility  for providing content, uploading directly to the cdn and rewriting url's point to the CDN. 

- You can configure when content expires, and when it is updated. 
- The CDN serves content directly without fetching from the origin. 
- Ensures instant availbility of content.

- Wastes storage if unused content is pushed.








