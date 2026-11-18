# LightLayer review: is $4/month real, which $24.99/year plan is worth it, and what the fine print says (plans, port speeds, test results)

LightLayer's cheapest cloud VPS is **$4.00/month** in Los Angeles: 1 vCPU, 1 GB RAM, 50 GB SSD, a 100 Mbps unmetered port on the Global network. Its annual plan is **$24.99/year** for the same 1 vCPU / 1 GB / 50 GB hardware, which works out to about **$2.08/month**. Both prices are current and both are genuinely cheap.

The catch isn't in the price. It's in the port. The same $24.99 buys a 200 Mbps unmetered port in Los Angeles or a 5 Mbps port in Taiwan, and one Los Angeles variant gives you 20 Mbps because it rides the CN2 route to mainland China. You're choosing a network class and a bandwidth cap; the CPU is identical across all of them.

That single fact decides whether LightLayer is a bargain or a waste of $25 for you, so this review leads with it, then covers the full plan list, the terms nobody quotes (there is no refund window at all), and what independent tests actually measured.

## Quick verdict

> **Most readers should take the Los Angeles Global annual plan: $24.99/year, 1 vCPU / 1 GB / 50 GB, 100–200 Mbps unmetered.** Buy the Premium variants only if your users are in mainland China and you can live with 5–20 Mbps. Before paying, know that LightLayer does not refund orders, and a credit can only become a non-withdrawable account balance.
>
> 👉 [See the current $24.99/year configurations](https://account.lightlayer.net/?affid=74)

## Every LightLayer plan on the price list

LightLayer sells three product lines: cloud VPS, dedicated servers, and GPU servers. The cloud VPS side comes in four shapes.

| Plan | Specs | Port / network | Price | Order |
| --- | --- | --- | --- | --- |
| Startup | 1 vCPU / 1 GB / 50 GB SSD | 100 Mbps unmetered, Global | $4.00/mo | [Order Startup](https://account.lightlayer.net/?affid=74) |
| Pay As You Go | 2+ vCPU / 2 GB+ / scalable storage | 200 Mbps+, Standard | from $5.60/mo | [Configure PAYG](https://account.lightlayer.net/?affid=74) |
| Mid-Tier | 4 vCPU / 4 GB / 80 GB SSD | 200 Mbps unmetered, Standard or Premium | roughly $11–18/mo | [Order Mid-Tier](https://account.lightlayer.net/?affid=74) |
| Business | up to 32 vCPU / 32 GB / scalable | 200 Mbps unmetered, Premium | $53.60/mo | [Order Business](https://account.lightlayer.net/?affid=74) |
| Dedicated (dual E5-2660) | 16 cores / 64 GB / 1 TB SSD / 5 IPs | 50 Mbps, Premium | $150/mo | [Order dedicated](https://account.lightlayer.net/?affid=74) |
| Dedicated (2× EPYC 7502) | 64 cores / 256 GB / 2×240 GB SSD + 2×4 TB NVMe | 100 Mbps, Premium | $900/mo | [Order dedicated](https://account.lightlayer.net/?affid=74) |
| GPU (RTX 4090) | 1 to 8 cards, Dallas | quoted per config | contact sales | [Ask about GPU](https://account.lightlayer.net/?affid=74) |

The Mid-Tier number moves because the order form prices cores, RAM, and storage independently; $11–18/month is the range that configuration lands in, not a fixed SKU. Pay As You Go works the same way and is the only route to something between 4 and 32 cores without jumping straight to the Business tier.

Dedicated inventory rotates. A Hong Kong E3-1230 box has been listed around $56/month during promotions, and the RTX 4090 machines are quoted by sales rather than priced on the page.

### The annual lineup is where the real decision lives

Every annual plan is the same 1 vCPU / 1 GB / 50 GB instance at **$24.99/year**. What changes is the network class and the port speed attached to it.

| Annual variant | Port | Data | Price | Order |
| --- | --- | --- | --- | --- |
| Los Angeles, Global | 200 Mbps | 1 TB/mo | $24.99/yr | [Order LA Global](https://account.lightlayer.net/?affid=74) |
| Los Angeles, Global | 100 Mbps | unmetered | $24.99/yr | [Order LA Global](https://account.lightlayer.net/?affid=74) |
| Los Angeles, Standard | 50 Mbps | unmetered | $24.99/yr | [Order LA Standard](https://account.lightlayer.net/?affid=74) |
| Los Angeles, Premium (CN2) | 20 Mbps | unmetered | $24.99/yr | [Order LA Premium](https://account.lightlayer.net/?affid=74) |
| Taiwan, Premium (CN2) | 5 Mbps | unmetered | $24.99/yr | [Order Taiwan](https://account.lightlayer.net/?affid=74) |
| Manila, Premium or Global | set at checkout | set at checkout | $24.99/yr | [Order Manila](https://account.lightlayer.net/?affid=74) |

A word on the price: some reviews still quote Los Angeles annual at $29.99, $39.99, and $49.99 depending on route. The configuration we could verify prices the Los Angeles variants at $24.99 like everything else, with the trade happening in port speed and data allowance instead. The vendor's 2024 launch page also listed 1 Gbps variants at $41.99/year (Global, 1 TB) and $83.99/year (Standard, 1 TB), so a faster port does exist at a higher price when it's in stock. Read the cart line before you pay, because that line is the only price that binds.

## Global, Standard, Premium: the three networks, and why Premium is slower

LightLayer defines all three classes in its Terms of Service, which is more than most budget hosts do.

- **Global**: international BGP only. Built for overseas and US-local traffic. This is where the widest ports live, up to 200 Mbps unmetered on the annual plan.
- **Standard**: mainland China BGP plus international BGP, without CN2. Reaches Chinese carriers directly at 50–100 Mbps on the annual tier.
- **Premium**: CN2 GIA plus CMIN2, the paid transit paths into China Telecom and China Mobile. Lowest latency to mainland China, and the narrowest port of the three.

The counterintuitive part: Premium costs you bandwidth. On the annual plan, a Taiwan Premium instance ships with a **5 Mbps** port and a Los Angeles Premium instance with **20 Mbps**, while the same $24.99 buys 200 Mbps on Los Angeles Global. On the monthly $4.00 entry, the same pattern repeats: Premium is capped at 20 Mbps where Standard starts at 50 Mbps for the same money.

That's not a pricing error. CN2 capacity is expensive, so the vendor rations it by port speed rather than by sticker price. If you're serving a blog, a bot, or an API for a handful of users in Shanghai, 20 Mbps is plenty. If you're pushing files, streaming, or syncing backups, Premium will strangle you and Global will not.

Test before you buy. LightLayer publishes test IPs per location: **128.241.250.254** for Los Angeles Premium and **156.245.234.254** for Hong Kong Premium. Ping and traceroute from the network your users are actually on, at the hour they actually use it. Five minutes of that beats a month of regret, especially since there's no refund.

## What $24.99 a year actually costs

$24.99/year is $2.08/month, and the renewal price is the price you paid. The Terms of Service state that price changes apply only to new orders, so a plan you bought at $24.99 renews at $24.99 unless you change it yourself.

Everything else in the terms is less friendly, and none of it appears in the affiliate write-ups that rank for this provider.

**No refunds.** The clause reads: "Lightlayer does not support refunds for reasons not attributable to the company, including but not limited to regular-priced and promotional products." There is no 7-day or 30-day window. If the route is bad for your users, that's your loss.

**Credits aren't money.** "Account balances can be used for purchases of all Lightlayer products, but cannot be withdrawn." Even when the company does issue a credit, it goes back into your LightLayer balance, not to your card.

**Network faults aren't compensated.** The terms exclude service interruptions from carrier cutovers, data center power events, large-scale network failures, and short maintenance windows. There is no SLA credit mechanism.

**A blocked IP stays blocked.** "If a user's IP is blocked or flagged due to their business activities, we will not provide IP replacement services." If your IP gets flagged, you buy a new plan or you move.

**Resources can be reclaimed.** LightLayer reserves the right to reclaim IPs, bandwidth, and server hardware when upstream operators or its own business调整 require it.

**Reinstalls are free once a month, then 30 yuan.** The penalty schedule is denominated in US dollars; the reinstall fee is not.

**Abuse handling is fast and one-sided.** A first complaint can suspend a cloud instance, with a $50 per-IP penalty for infringement-type reports and $20 for phishing or fraud, and you have 6 hours to respond. Servers under an abuse complaint are not eligible for early termination or refund during the process.

Read that list once more and treat the $24.99 as money already spent. At that price it's still a reasonable gamble for a personal project. It's a bad structure for anything you'd have to explain to a client.

👉 [Check the plan you picked against the cart total](https://account.lightlayer.net/?affid=74)

## What independent tests measured

The routing claims hold up better than the disk performance.

**San Jose route test (V2EX, 14 July 2026, 25 minutes).** China Telecom reached 31 of 31 provinces at an average **157.9 ms** with 99.7% success. China Mobile hit 31 of 31 at **176.4 ms**, 96.8%. China Unicom managed 28 of 31 at **195.9 ms**, 82.6%. Return paths were CN2 GIA for Telecom, CMIN2 for Mobile, and 4837 for Unicom. International throughput to Los Angeles measured **820.6 / 772.0 Mbps** on a 1 Gbps port, and of 439 DNS blacklists checked, 412 were clean, 25 flagged, 2 blacklisted. One reply in that thread warned Hubei Unicom users off entirely.

**San Jose $9.9/month (meowvps, 18 July 2026).** Intel Xeon Platinum 9242, sysbench single-core 1133. Disk: **fio 4K read 3.71 MB/s (908 IOPS), write 3.75 MB/s (916 IOPS)**, which the tester compared to a USB 2.0 card reader. Streaming checks passed Netflix Originals only; Disney+ and Reddit were not unlocked. That page's conclusion is blunt: some products have severe I/O limits and weak hardware, and are not suitable for databases, high-frequency I/O, or heavy workloads. The same review confirmed Telecom CN2 on the outbound and CN2 GIA (59.43.x) on the return.

**Hong Kong annual at $24.99/year (itbulu, 23 September 2026).** Ping **53 ms**, jitter 3.57 ms, download about 11.9 Mbps and upload about 12.9 Mbps. Those speeds are the 10 Mbps port doing exactly what it says, not a fault.

**San Jose "Lite" (zhujiceping, 26 September 2026).** FIO 4K around **48 MB/s**, average ping **174 ms**, a Seychelles-registered IP that unlocked TikTok, ChatGPT, and Claude but not Gemini, and no IPv6.

Read those four together and the pattern is clear. The China routes are real and the latency is competitive at this price. Disk I/O varies wildly by node, with at least one $9.9/month machine performing at USB 2.0 speeds, so anything with a database, a write-heavy application, or an index rebuild is a gamble you shouldn't take here.

## Who should not buy LightLayer

Skip it if you need managed services. There are none, the control panel is functional rather than polished, and documentation thins out on complex setups.

Skip it if you need compensation for downtime. The terms exclude network faults from liability, and no SLA credit exists to claim.

Skip it if the box is a production system you'll be paged about. No refund window, no IP replacement, and a first abuse complaint can suspend an instance combine into a risk profile that doesn't belong under anything revenue-critical.

Skip it if you're running MySQL, Postgres, Redis with persistence, or heavy build workloads. The fio numbers above are disqualifying on their own.

If your reason for looking at LightLayer is China-optimized routing with an SLA and a refund structure, DMIT sells CN2 plans with a published 99% SLA and a refund policy. If you want the cheapest annual box and don't care about the route to China, RackNerd's 2 GB / 5 TB plan runs $35.99/year with no China-route promise at all. If you want a short trial window, ZgoCloud offers a 3-day refund, though its acceptable-use policy bans proxy use. None of the three is a substitute for LightLayer's $24.99 global-bandwidth offer; they're what you buy when one of the disqualifiers above applies to you.

## FAQ

**Can I get a refund if I don't like it?**
No. The terms exclude refunds for anything not attributable to the company, including promotional plans. The only path back is account balance, which cannot be withdrawn.

**Will the renewal price go up?**
The Terms of Service state that price changes apply only to new orders, so an existing plan isn't repriced at renewal. Screenshot your cart at checkout anyway. That's cheap insurance anywhere.

**What's the difference between the $4/month plan and the $24.99/year plan?**
They're the same hardware class. $4.00/month is monthly billing, Los Angeles, Global network, 100 Mbps unmetered. $24.99/year is annual prepay at roughly $2.08/month, with the port speed depending on which network variant you select. Annual billing is where the discount is; the network selection is where the trap is.

**Is CN2 worth paying for?**
On this price list, CN2 doesn't cost more, it costs port speed: 20 Mbps on Los Angeles Premium against 200 Mbps on Los Angeles Global, both $24.99/year. It's worth it when your users are in mainland China and your traffic fits in 20 Mbps. For a 200 MB site with a few hundred daily visitors, it fits comfortably. For anything that streams or syncs, it doesn't.

**How do I test before I order?**
Ping and traceroute the published test IPs (128.241.250.254 for Los Angeles Premium, 156.245.234.254 for Hong Kong Premium) from the network your users are on, during their peak hours. Ask for the Standard and Global test IPs if you're buying those variants, since Premium and Global take different paths.

**Are the promo codes still valid?**
Codes from 2025 campaigns (2025TKYCH30OFF, 2025MNLDS30OFF, HKC2M, LAC2M, LONC2M, and the holiday codes) circulate widely. We can't confirm any of them still apply at checkout today, so treat them as something to try, not something to count on when comparing prices.

## Picking your plan

The decision tree is short.

Serving users in mainland China, low traffic, no streaming: **Los Angeles Premium annual at $24.99/year**, and accept the 20 Mbps port. Taiwan Premium at 5 Mbps only makes sense if latency to Taiwan itself is the point.

Serving anyone else, or needing throughput: **Los Angeles Global annual at $24.99/year**, 200 Mbps unmetered. This is the plan the price list is actually built around.

Want a dev box without a year's commitment: **Startup at $4.00/month**, Global network, 100 Mbps. Cancel by not renewing, because there's no other exit.

Need 4 or more cores: **Pay As You Go**, and price the exact config in the order form before comparing it to anyone else's list.

Two things to confirm on the final screen: the port speed and data allowance on the line item (that's the variant you're buying), and that you're comfortable writing off the full amount, since no refund exists.

👉 [Compare the annual port options before you pay](https://account.lightlayer.net/?affid=74)
