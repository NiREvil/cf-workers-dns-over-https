# cf-workers-dns-over-https
A very minimalist DNS-over-HTTPS proxy on Cloudflare Workers.

Sign up for a free [Cloudflare Workers](https://workers.cloudflare.com/) account, create a new worker, replace the Script with the content of [index.js](/index.js), deploy the worker, and you're done, use the address anywhere DoH is accepted (AdGuard, browsers secure DNS settings, YogaDNS, Intra, Nebulo etc). Feel free to replace the `doh` variable with [any DNS-over-HTTPS server you want](https://github.com/curl/curl/wiki/DNS-over-HTTPS). Confirmed to work with Cloudflare itself, Google, and NextDNS. The rarely supported [JSON API](https://developers.google.com/speed/public-dns/docs/doh/json) is available through the `dohjson` variable. Some providers use identical URL (Cloudlfare, NextDNS), some use `/resolve` instead of `/dns-query` for path (Google, AdGuard).

Why? In case ISPs start banning known DoH providers, you can use your own proxy. Even if they block workers.dev wholesale, you can use your own domain (it must be hosted on Cloudflare, add a CNAME record targeting anything and bind the route from your website Workers tab). If you want to use domain not hosted on Cloudflare, use [doh-cf-pages](https://github.com/tina-hello/doh-cf-pages) instead, where even CNAME records from [FreeDNS](https://freedns.afraid.org/) is enough for custom domain.

Daily request on free tier is limited to 100 thousands, should be enough for most personal use, or even a family.

Final address should be like:<br>
https://XXX.UserName.workers.dev/dns-query

Want more control of the filter? Use [serverless-dns](https://github.com/serverless-dns/serverless-dns) which powers [RethinkDNS](https://rethinkdns.com/)

Want to host on Google Cloud Function or see how this is implemented in .NET? Use my [doh-gcf](https://github.com/tina-hello/doh-gcf)
