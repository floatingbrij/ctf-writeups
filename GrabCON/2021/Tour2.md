---
author: "Brij"
title: "Tour (2) - GrabCON CTF"
date: "2021-09-05"
description: "This is my write-up for the ‘Tour (2)’ Challenge in GrabCON CTF 2021"
tags: ["GrabCON","osint","2021","ctf"]
categories: ["GranCON","writeup","osint"]
---

<!-- gist of the writeip -->
## Description
- Can you find the flight number and the flight operator of the last flight that took her to the final destination?

- E.g. `GrabCON{AF226_Air_France}`

<!-- analysis/detailed explanation split into sections -->
## Given information

We have been given social media info in [Tour (1)](https://1nf1n1ty.team/blog/posts/writeups/grabcon/2021/thetour1/).

- <https://mastodon.social/@w0nd3r50uL>  
- We have to find out what flight she took, it's departure & arrival and also the flight number.
<!-- if you need a horizontal divider line -->
---

## Solution

Upon Investigating the `Mastadon` user profile, the latest post is of her *flight ticket*!


<img style = "display:block;margin-left:auto;margin-right:auto;width:50%;" src="https://i.imgur.com/oO7SAaf.png" width="250">

Everything has been censored but the boarding pass code was untouched!

- After googling a bit we find out that boarding pass codes are encoded in `pdf417`.
- It's worth mentioning that every boarding pass follows the **IATA guidelines** for making the barcode.
- Upon scanning the barcode in [inlite Online scanner](https://online-barcode-reader.inliteresearch.com/) we get:

<img style = "display:block;margin-left:auto;margin-right:auto;width:50%;" src="https://i.imgur.com/PHlYTPX.png" width="250">

* We see that the "BEGIST" is the codes for departure airport & arrival airport.
  * BEG = Departure Airport: `Belgrade Nikola Tesla Airport (BEG)`
  * IST = Arrival Airport: `Istanbul Airport (IST)`
* JU 0802: Flight code

Googling the flight code, we find the flight carrier: `Air Serbia`!

---
<!-- end with the flag -->
## Flag

The flag thus obtained is: `GrabCON{JU802_Air_Serbia}`

*Thank you for reading! Happy hacking!* ~ Brij
