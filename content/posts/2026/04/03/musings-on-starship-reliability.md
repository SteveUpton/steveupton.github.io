---
title: Musings on Starship Reliability
date: 2026-04-03
slug: musings-on-starship-reliability
Tags:
  - space
---

I’m a space nerd, and recently I’ve been thinking about the reliability of SpaceX’s Starship.

<!--more-->

> This is a departure from my usual travelogues, but if you’re reading this, I’m going to assume you’re a space nerd and have a basic familiarity with the Starship program so I won’t be explaining any of the technical terms.

> This was published on April 3rd, 2026 and the figures below are accurate _at time of publishing_.

## Starship vs Falcon 9

Starship is intended to be a two-stage, fully-reusable launch vehicle that will return both its first stage (booster) and second stage (ship) for a propulsive landing at the launch site and to be reflown. At a high level, the approach is similar to Falcon 9, where the first stage returns to the launch site (or a drone ship) for a propulsive landing and to be reflown, and SpaceX have been doing this very reliably for almost a decade now.

The two key differences in Starship’s approach are:
1. They also intend to recover the second stage (ship).
2. Recovering both the booster and the ship involves them being caught by a pair of arms attached to the launch tower (often referred to as a “tower catch”).

Recovering the second stage is new. A whole new set of challenges, with vastly higher energies to deal with. A significant challenge, but hey, that’s the nature of the game.

Recovering both stages with the “tower catch” is also new and SpaceX has demonstrated that they can do this (3 successful tower catches of boosters so far). The key difference here is that a failed tower catch has at least a chance of damaging launch infrastructure, which is not the case for Falcon 9, which lands on either a droneship or a dedicated landing zone. For Falcon 9, the worst case scenario for a failed landing is a crater in a landing zone or a destroyed droneship. For Starship, the worst case scenario for a failed landing is damaged launch infrastructure (pad, tower etc.) that cannot be used until it is repaired or rebuilt.

Another important difference between Falcon 9 and Starship is that Starship’s stated mission “to make life multiplanetary” (i.e. sending ships to the Moon and Mars), requires a mission architecture that involves several refuelling flights. These must happen within a given time window to meet transfer windows and to minimise fuel boil-off.

> The question I want to explore here is not whether _individual Starship flights can succeed_, but whether _entire launch campaigns can succeed reliably_ given their dependence on multiple tightly coupled launches and shared infrastructure.

## New Failure Modes

Looking at all of this together, I summarise a few key points:
1. Starship missions beyond LEO require multiple launches for refuelling to be successful (a launch campaign).
2. A launch campaign must be completed within a given time window.
3. Booster and Ship catch attempts have a chance of being aborted, leading to a loss of the vehicle.
4. Booster and Ship catch attempts have a chance of damaging launch infrastructure, possibly taking it out of action.
5. SpaceX has a finite number of launch pads (at least that they can build during a given launch campaign).
6. SpaceX has a finite number of starships and boosters (at least that they can build during a given launch campaign).

This leads to the conclusion that a Starship launch campaign has a few potential failure modes:
1. During the launch campaign, enough catch failures occur to cause enough launch infrastructure to be damaged, such that SpaceX cannot complete the campaign. (ie. run out of launch pads).
2. During the launch campaign, enough boosters are lost, such that SpaceX cannot complete the campaign. (ie. run out of boosters).
3. During the launch campaign, enough ships are lost, such that SpaceX cannot complete the campaign. (ie. run out of ships).

Failures and damage to infrastructure is always a risk, but with Starship, the risk is that too many things break before the campaign is done, a failure mode that isn’t really present in Falcon 9’s mission architecture.[^1]

Those points should be uncontroversial, but estimates for the specifics vary wildly.

## The Key Variables

### Launches per campaign

The number of launches required for a beyond LEO mission has been estimated at between 4 and 30+ flights. That’s a wide range, but several estimates from presumably well-informed sources at NASA and SpaceX seem to cluster around “high single digits to low double digits”.[^2]

### Booster catch reliability

How reliably the boosters can be caught by the tower is something we have actual data on. So far, of the 4 flights that had potential catch attempts in their mission plan, 3 have resulted in successful catches and 1 resulted in an off-shore divert, destroying the booster, but preventing damage to the launch infrastructure. The catches are impressive, but 4 flights is not a statistically significant sample size.

There is a lot of speculation about the margins for error (vertical and horizontal position and velocity, angle, rotation etc.) and how both the vehicle and the tower arms can affect these.
[RyanHansenSpace has a great analysis of the mechanics of the catch](https://www.youtube.com/watch?v=ub6HdADut50), including the margins for error, and potential abort modes, but it’s still only part of the equation. We don’t know the service life of the vehicles or pad infrastructure, when maintenance would be required or how repeated use might influence their reliability.

### Ship catch reliability

How reliably the ship can be caught is more speculative. At the time of writing, Starship V1 has demonstrated the ability to accurately perform its flip manoeuvre multiple times, including after atmospheric re-entry, but has not yet attempted to be caught by the tower. Otherwise, a lot of the same speculation about booster catch reliability applies here.

### Potential damage to launch infrastructure

How much damage a starship or booster crashing into the launch pad would do is also fairly speculative. On one hand, during the catch, the vehicle is nearly empty of fuel, only firing 3 of its engines, and the launch pad is a pretty robust piece of infrastructure, explicitly designed to survive a launching starship (with 33 engines firing). On the other hand, there are thousands of moving parts essential for launch and recovery that presumably wouldn’t enjoy having a starship dropped on them. How long repairs would take is also unknown, though it’s interesting to note that construction of Pad 2 (from scratch) started in March 2022 and is expected to be complete some time in 2026.

Maybe a failed catch attempt would result in a few days of inspection and repair or maybe it would require a complete rebuild. Whatever the case, I don’t think a booster crashing into the launch infrastructure would be a good day for anyone at SpaceX.

### Number of launch pads

Even the number of launch pads has some uncertainty. Currently, SpaceX has 1 operational pad, is building 2 more and has formally planned for 4. They have also expressed interest in up to [2 dedicated “catch towers”](https://www.faa.gov/space/stakeholder_engagement/spacex_starship_ksc/SpaceX-SSH-at-LC-39A-Draft-EIS_Volume-I_Main-EIS.pdf), but only if space is available.

### Number of vehicles

The number of starships and boosters available at the start of a campaign is also uncertain. Musk has stated that [Starbase is (eventually) intended to produce 1000 ships per year](https://x.com/SpaceX/status/1928185351933239641), whether or not you think that’s realistic, a high enough production rate or fleet size would make losing a few boosters or ships a non-issue for campaign success (though it would add to the cost). For reference, the Falcon 9 booster fleet is currently around 24 boosters.

On top of all of those uncertainties, everything is a moving target. Currently all successful booster catches have happened with V1 of the booster, and V2 is planned to launch soon. Similarly, all successful starship reentries have happened with Ship V1 and V2, and Ship V3 is planned to fly soon. All flight tests so far have used Raptor 2, which will soon be replaced with Raptor 3, with promises to improve resilience, reusability, thrust and ISP. Even the design of the launch towers and pad infrastructure is changing as new pads and towers are built.

So, no matter how carefully you analyse the range of perspectives and data, everything could change. Predicting the future is a fool's game, so I’m not going to attempt it. Instead, I want to provide tools to play with the hypotheticals.

## Monte Carlo simulation

As the campaign level risk isn’t easy to reason about intuitively, I built a Monte Carlo simulation that allows you to input values for the key variables mentioned above and see how they affect the likelihood of a successful launch campaign. 

[You can play with the simulation here](https://steveupton.io/starship-monte-carlo-simulation/).

In short, it takes your input values for variables like number of launches, chance of attempting a catch and chance of a catch succeeding, then simulates 10,000 launch campaigns and displays the distribution of results, like how many campaigns resulted in a specific number of damaged pads or lost vehicles.

I intentionally kept the simulation simple, while still allowing you to experiment with the impact of important variables like Starship reliability and performance. The simulation page includes a more detailed description of how it works, its limitations and a few suggestions about interesting things to simulate. You can also [check out the code on GitHub](https://github.com/SteveUpton/starship-monte-carlo-simulation).

Everything is on the simulation page, so what are you waiting for? Go and simulate some Starship launch campaigns!

## Summary

This whole exercise started when I thought about the number of launches (and thus, number of catches) required for a single beyond LEO Starship mission and I found myself asking “how likely is it that all those catches succeed vs damaging some, or even all of their launch infrastructure?”. Since I couldn’t intuit an answer beyond “well, that seems kinda risky…”, I built the simulation to generate a more quantitative answer.

Often, when I stumble upon discussions of the Starship program, I’ve been disappointed to see a focus on specific technical challenges or achievements, and conflating program success with achieving certain technical milestones (like demonstrating tower catches). Starship's success won't just be determined by specific achievements; it will also need to succeed repeatedly and reliably, under time pressure, which is a much higher bar. I hope this simulation can be a more nuanced, probabilistic analysis, looking at how certain variables can impact the likelihood of overall mission success.

I’ve put a lot of focus on the risk to launch infrastructure, partially driven by [my talk on Falcon 9 development](https://www.youtube.com/watch?v=fl2USB1LUDQ), where I emphasised that every Falcon 9 landing attempt was safe to fail, as multiple landing failures did not impact overall mission or program success. While I understand the logic behind the tower catch, I also see it as a risk to mission success, particularly with a mission architecture that requires multiple launches. How much of a risk is an open question, and the goal of the simulation is to shed some light on that topic.

[^1]:
    Technically, a Falcon 9 could explode on the pad, causing damage to the launch infrastructure and preventing launches from that pad until repaired, but this is true of every launch vehicle, including Starship. The mission architecture of Starship, where multiple launches are needed within a specific time window for the mission to be a success, is also a key differentiator here. If a few Falcon 9 pads are destroyed, that would be bad, and likely lower launch cadence, but as long as each single Falcon 9 launch succeeds, the associated mission also succeeds. There is little to no coupling on other launches, so Falcon 9 requires 1 successful launch per mission, whereas a Starship mission may require multiple successful launches.

[^2]:
    While most estimates cluster around **~8–15 launches**, the range of estimates for the number of refuelling flights for a single HLS mission is wild:
    - In 2021, Elon Musk claimed it would take [4-8 refuelling flights](https://x.com/elonmusk/status/1425473261551423489)
    - In 2021, the GAO estimated [14 refuelling flights](https://www.gao.gov/products/b-419783%2Cb-419783.2%2Cb-419783.3%2Cb-419783.4)
    - In 2024, Jessica Jensen, Vice President of Customer Operations and Integration at SpaceX said it would take [“roughly 10-ish” refuelling flights](https://spacenews.com/spacex-targets-february-for-third-starship-test-flight/)
    - In a [2023 interview with Ars Technica](https://arstechnica.com/space/2023/11/what-nasa-wants-to-see-from-spacexs-second-starship-test-flight), Lisa Watson-Morgan, manager of NASA’s Human Landing System program, suggested the number of refuelling flights would be “high single digits to the low double digits”, while Lakiesha Hawkins, deputy associate administrator for NASA's Moon to Mars program office suggested a number in the "high teens"
    - In 2023, Space Policy Online reported that NASA stated [at least 15 Starship launches would be required for Artemis III lunar landing](https://spacepolicyonline.com/news/at-least-15-starship-launches-to-execute-artemis-iii-lunar-landing/)
    - In 2023, Destin Sandlin estimated between [12 and 28 refuelling flights](https://www.youtube.com/watch?v=OoJsPvmFixU&t=1746s)
    - In 2024, Elon Musk claimed it would take [5 to 6 refuelling flights](https://youtu.be/S6g73tO9E04?t=1623)

    While, in theory, you can easily derive the number of refuelling flights by knowing Tanker Payload to Orbit and Fuel Requirements of the beyond LEO Starship, the reality is we don’t know those figures because they are influenced by:
    - Starship and Raptor performance (Payload to Orbit, Dry Mass, ISP, Thrust etc.)
    - Specifics of the refuelling plan (dedicated fuel depots, schedule, boil-off-rate, refuelling in LEO vs MEO/HEO etc.)
    - DeltaV requirements and payload of the beyond LEO Starship (different for Mars and Lunar missions)
