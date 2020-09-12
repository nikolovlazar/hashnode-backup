## How to render your website

## A little history

Back in the days, rendering a website was simple. You needed a web server that served HTML files. Those were **static sites**. Then developers started using databases and authentication. To achieve that, they needed to manipulate the HTML file before serving it. That's how **server-side** rendering was born. Let's fast forward until 2010, when Backbone got released. The front-end got richer and more complex. Then the era of **client-side** applications begin. Developers migrated their data and routing logic to the client side. They could, because Google "understood" JavaScript. The servers became slimmer, but the websites became more complex. Yet, recently server-side rendering became a trend again. All thanks to React and its server-side hydration feature.

## Static sites

Static sites are the simplest way to render a website. You code your website in HTML/CSS, and serve those files from a web server. This is the simplest way to render your website, but it comes with pros and cons.


![Static Site Diagram](https://cdn.hashnode.com/res/hashnode/image/upload/v1599911023781/_11mpV_GL.png)

### Cons

Since they're static, you **cannot** have dynamic data. To update the data on your static site, you need to edit your HTML files, and deploy them again.

That also means that your visitors won't be able to "contribute" to the website data. They can't leave comments, or create their own posts, or "like" your content.

### Pros

But, since there's no "computation" in static sites, they are the fastest to render. The server serves the HTML file, and the browser starts "drawing" immediately. This gives your website **fast TTFB** (time-to-first-byte) **score**.

Another benefit that static sites have is the ability to host them on CDNs. A CDN (content delivery network) is a network of servers distributed around the world. Meaning, your website will "live" on **many servers at the same time**. Also, CDNs are **cheaper** than dedicated servers!

They're also **more secure**. There is no back-end. That means there's less room for your site to suffer an attack, or your database to get compromised.

So, if you need to create a website that doesn't update the data on a regular basis, static site might be the best for you. Your site will be **fast**, **cheap**, and **more secure**.

## Client-side rendering

Client-side apps are like static sites, but they use JavaScript to fetch their data. The server serves an HTML file with JavaScript inside, and the browser starts executing. This method also gives you a **fast TTFB score**, but the **TTI** (time to interactive) is slow, since there's no data right away.

![Client Side Diagram](https://cdn.hashnode.com/res/hashnode/image/upload/v1599911729267/IA0khVN4z.png)

### Cons

The TTI in this case depends on the user's internet speed and the amount of data requests. So, you need to be very careful when to trigger your data requests. But, there's nothing you can do about the user's internet speed.

Also, different browsers have different support for scripts. This means that you need to **invest more into testing** your CSA.

If a user decides to disable JavaScript, your website would be **blank**.

To fetch the data, you will need an API. That's an **extra responsibility**. When building APIs, you also need to think about **security** and **data access**. If you leave your API routes open without authentication, someone can make a mess.

### Pros

You have **dynamic data**! You won't need to edit files to update your website. Also, your website can be **interactive**. With dynamic data, you can make forums, social networks, tools, and all kinds of platforms.

You can implement authentication. With that, each user can have a **personalized experience** on your website.

Client-side apps can be **SPAs** (single page applications). That means the routing is completely on the client side, and it's instant! Because users don't have to wait for the server to respond when navigating between your pages.

## Server-side rendering

Server-side rendering is an old and mature way of rendering the websites. There are tons of tools to help you achieve SSR. It's like CSR, but the data and routing logic lives on the server. When requesting a page, the server fetches the data and inlines it in the HTML file. That file is then served to the user, and the browser starts rendering right away.

![Server Side Diagram](https://cdn.hashnode.com/res/hashnode/image/upload/v1599912119788/UgnjWZ4s-.png)

### Cons

The TTFB is **slower**. The browser needs to wait for the server to fetch the data and prepare the HTML for your page.

The server will also be **busier**. It needs to visit the database and prepare the HTML file every time a user navigates between your pages.

When navigating between pages a **full page reload** needs to happen.

### **Pros**

SSR websites are **SEO friendly**! The search engines can get and index your data without executing extra scripts. Also, they can get the localized version, so you have better SEO for your supported languages.

The content gets served **faster**. This is because usually the servers have better internet connection than the users. Also, servers are more performant than the users' machine.

The user's machine is **less busy**. The browser only needs to take care of rendering, not data fetching and executing scripts.

The SSR method can also **fix** the issues with social sharing and the OpenGraph system.

You also have **dynamic data**. Every time the user lands on your page, the server fetches and serves the freshest data.

## Bonus: Incremental Static Regeneration

This method gets the static site speed of rendering and the server-side data fetching. This is what [Next JS](https://nextjs.org/) introduced in [version 9.5](https://nextjs.org/blog/next-9-5#stable-incremental-static-regeneration). So ISR "builds" the static HTML files on build time, but then it rebuilds them every time there's traffic on the site. The rebuilding happens in the background. That means the users are immediately presented with a static HTML file. If the data changes, the server rebuilds that page and starts serving the new version from there on.

### Cons

The server has **less** load than SSR, but **more** load than CSA or Static. But you **can** configure this. The server rebuilds the page after a user requests it and there's new data. That happens on configurable intervals. You can tell the server to revalidate the page on X seconds. So, if you expect frequent data changes set the revalidation interval to a smaller value. If not, you can set the revalidation interval to be, for example, once per day.

### Pros

Well, you have **dynamic data** which gets served in a **static way**. You have **fast TTFB** score, but also **fast TTI**.

Because it's static, you get **great SEO** our of the box.

Next JS has a **fallback mechanism** for dynamic pages. Let's say you have a blog that's using the ISR method. Your posts route would be something like `/posts/[post-slug]`. When you write a new post and publish it, you will only need to open the URL and Next JS will render that post page static. When you open that post again, it will be served immediately.

There's **no full page reload** when navigating between pages. Next JS prefetches the data for the pages that can be accessed from the current page.

## Conclusion

The web development world has seen a significant change, and it will keep changing. In this post we got introduced to 4 methods of rendering websites. We explored the pros and cons and now have a good understanding of them. But, there is no holy grail. If you need to develop a very simple website, SSR or CSA will be an overkill, so you can use Static. If you need to develop a blog platform, or a forum, then SSR or CSA will be your best friend. Before deciding which method to use, write down the things that you need to have. Should your site have great SEO? Or dynamic data is the most important factor? Do you need to serve the website on a CDN? This list will help you choose the most suitable method.

---

> 
If you liked this article feel free to share it so more people can learn from it. 