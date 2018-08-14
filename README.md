**What is the Problems with plain proxy links?** They are very easy to block by governments.
What I propose make it significantly more difficult for blocking proxy server address, and also give us a more novel way to bypass censorship:

### one:

I want to publish this proxy to users: "server=s1.mymtproto.com&port=4780&secret=6a72b0db8bc5ebd815cc1c169b7ddf99", but i don't want to it gets block fast by government (users reporting it).
I propose telegram add this new proxy links mechanism. This will have to work **just on official apps**.
telegram in it's app uses some crypt method to:
```javascript
// this is a asymmetric (or symmetric) encryption algorithm , just offical clients has this key 
function proxyLinkToObscureurl('server=s1.mymtproto.com...', TELEGRAM_OFFICIAL_BUILD_KEY){
  give correct answer in official apps only
 ...
 return 'fM0W2Y5bOkhiLOYoCThoG8xi16XLyqakJa9OiFU3hcmBQGpnzK...'// this is obscured url of proxy
}

function proxyLinkFromObscureurl('fM0W...', TELEGRAM_OFFICIAL_BUILD_KEY) {
  ...
 return 'server=s1.mymtproto.com...'
}
```
Then users share this proxy: t.me/proxy?fM0W2Y...
when users click on this links they are asked if they want to set this proxy like current behavior but with difference that they don't see proxy actual address, just a obscure URl appear ('fM0W...') in proxy list.

### two:
another problem is sharing this urls, when they get reported to government they block it via looking at which server they connect to. this kind obscure links is at least better than those plain address, because even if they blocked, just one IP is get blocked and we can change the address at DNS level, so this is makes blocking address more problematic. In normal cases when we share a plain proxy url like de.myproto.com, even if they get block, and we change DNS, this mechanism of blocking static url address with changing server IP address can be fairly automated, an scrip can automatically, blocks this address periodically. But with obscure urls, this is much more harder, because only official telegram apps can decode this real urls address.

### three:
we want to write bots that give every 5,000 users an unique obscurer links address with unique IP, so if government can block one of this server IPs (via looking at network traffic), it will be just that one server ip address get's blocked not the shared obscure link, and because our bot give the same obscurer link to same user, government has limited ability to have thousands of telegram accounts to get all this obscurer urls of servers, and block them all, and our server address at DNS level is moving when they get blocked, via an automated process for checking blocked address and changing DNS.

### four:
Even an better mechanism for this bots is that, their obscurer links doesn't even shown to users, and cannot be shared to others (no share button on proxy list). bots just set an obscurer links, and in users proxy list section just some part of obscurer link is shown.
We want to this bots just work on official apps, so untrustworthy third party apps don't even collect our obscured links.
telegram can add one parameter to disable sharing button ex: t.me/proxy?...shareable=false

## some faq:
**why secret urls just on official apps:**
the whole point of secret urls is not get real proxy server address ,third party apps can collect this links.

**why this mechanism is needed?**
because this address report very fast and they get blocked within hours. with this mechanisms it is very hard for government to find this address, and in most cases scene impossible to find all this proxies.

**why not wait for TON proxy?**
this mechanism is very simple for telegram to implement, what i have described in here is just an _**effective technique, not a whole new technology, it is just big improvement that lower the ratio of blocking proxy links significantly, and make this proxies much more effective.**_
