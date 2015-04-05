---
layout: post
title: "YB3 vs Google location history"
date: 2015-04-05 14:40:00
comments: true
categories:
tags: data, maps
---

A couple of weeks ago, I travelled from London to Marrakech by train (and boat). You can read about the it [here]({% post_url 2015-03-31-steve-goes-to-marrakech %}). While travelling I carried a GPS tracker which fed a live map of my location for everyone to watch. It was a fun experiment. I also turned on location history for my Android phone and decided to compare the results of the two.

<!-- more -->

## Disclosure

To start off with, this isn't a review. Neither is it an in-depth technical comparison. At best, it's light writeup of my experiences using two different methods of location tracking. Also, have a friend who works at [YB Tracking](https://www.ybtracking.com/) and was able to lend me a tracker free of charge for the duration of the trip. Normally this would have cost me money, so it's probably worth disclosing that. Remember, this is about ethics in GPS journalism.

## The trackers

{% img /images/posts/yb3.jpg %}

The [YB3](https://www.ybtracking.com/products-yb3) is a hefty bit of kit. Ruggedised for mountaineering and boat races, it's total overkill for traipsing European capitals. It just about fit in the sunglasses pocket at the top of my [backpack](http://www.patagonia.com/us/product/refugio-pack-28-liters?p=47911-0) where it seemed to get good reception. The unit I received was set up to capture my position every 30 minutes, transmit that via [Iridium](http://en.wikipedia.org/wiki/Iridium_satellite_constellation) to YB Tracking who updated a live map with my position. This transmission works best when you have a clear line of sight to the sky. For the duration of the trip, I pointed [where.is.steveupton.io](http://where.is.steveupton.io/) to that map and shared the link with my friends and family (that link might show something else soon, so the original map is [here](http://yb.tl/steveupton)). It's fair to say they seemed to enjoy tracking me quite a bit as I received several comments and emails about my travels upon returning to my hostels. Entertaining if you're into that kinda thing and have friends as voyeuristic as mine.

I didn't use all the features of the YB3. You can send messages, mark waypoints on the map, log to file and even alert others of an emergency using a red button that took all my willpower not to press. The full specs and features are listed [here](https://www.ybtracking.com/products-yb3) if you're curious.

For Google location tracking, I turned on location history and enabled location tracking on my phone (a Nexus 5). The main difference between Google and YB tracking's solution is that Google devices can use Wifi and cell tower triangulation to augment their location tracking. The main downside (compared to YB Tracking) is that it will only upload this data when it has a data connection (not typical when I'm wandering around other countries) and won't put this in a publicly viewable place - I had to grab the data manually and put it in a map for everyone to see. Google used to provide something a bit closer to YB Tracking with it's short lived Latitude service, which provided stalker-tastic view of your friends locations. Interestingly, the KML files I grabbed from Google still reference Latitude - make no mistake, this is the same tech, it's just not making the data publicly viewable any more.

{% img center /images/posts/latitude.png %}

## The data

Right then, let's get started shall we? Here's a map showing the tracks produced by both methods.

<iframe width='100%' height='520' frameborder='0' src='http://steveupton.cartodb.com/viz/00fbf57c-db93-11e4-a11d-0e9d821ea90d/embed_map?center=[41,2]&zoom=4.5' allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>

Both are generated from KML. Google provides an option to download the KML for a particular date range and I just emailed someone at YB Tracking to get the data from them, though I understand they offer an API. I whacked the KML into CartoDB, munged the data a bit (see below) and generated the visualisations from there.

A couple of comments on the raw data. I preferred the KML provided by YB Tracking; it presented the data as list of points (rather than as a linestring, as Google does). This format includes metadata with each point like altitude, average course and speed which are entirely absent from the Google data. I needed to convert them into a linestring if I wanted to display them as a line rather than a collection of points, but that was easy to do with the sql below:

{% gist 50c3819056b4a33e39cb %}

I couldn't perform the opposite conversion (linestring to points) with the Google data, but that's probably because I'm bad at CartoDB/PostGIS, so don't read too much into that. The map above the result of overlaying 3 tables; the linestring from Google, the raw points from YB Tracking and the linestring generated from the YB data. Let's take a closer look at the maps shall we?

## Paris

<iframe width='100%' height='520' frameborder='0' src='http://steveupton.cartodb.com/viz/00fbf57c-db93-11e4-a11d-0e9d821ea90d/embed_map?center=[48.86,2.34]&zoom=13' allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>

Here we see the first instance of Google's location bug - jumping locations. According to the Google track, on my extended wander around the city, I would periodically teleport back to the hostel for a few minutes before jumping back to where I was. This is a known issue, often ascribed to multiple devices waking up to report their location from different places. In my case, the only device I left in the hostel locker was my iPad in airplane mode, so maybe it retroactively added it's last known position? Possibly, but it could just as easily be idiosyncrasies with location reporting on my phone - without more detailed data, it's difficult to know. Other than those oddities and the fact it completely missed my initial walk from the train station to the hostel, the Google data was pretty accurate. YB3 did a pretty good job too, catching some bits Google didn't but missing others.

## Madrid

<iframe width='100%' height='520' frameborder='0' src='http://steveupton.cartodb.com/viz/00fbf57c-db93-11e4-a11d-0e9d821ea90d/embed_map?center=[40.415,-3.70]&zoom=15' allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>

Both trackers failed to register my trip from Paris to Madrid, though Google did capture my 2 hour stop in Barcelona where I used McDonalds for the only thing they're good for - free toilets and Wifi. Similar story to Paris here, with Google edging out slightly as it grabbed my position indoors on a few occasions.

## Morocco

<iframe width='100%' height='590' frameborder='0' src='http://steveupton.cartodb.com/viz/00fbf57c-db93-11e4-a11d-0e9d821ea90d/embed_map?center=[33.6,-6.84]&zoom=7' allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>

I used the YB3 less around Tangier and Marrakech, tending to leave my bag at the hostel and only travel with cash and a phone. The high walled riads and souqs weren't particularly conducive to good satellite connections either, so I got some readings from the hostel roof terraces and left it at that. The YB3 did do an excellent job of tracking my crossing the Strait of Gibraltar and the train from Tangier to Marrakech, which my phone didn't catch at all.

On the penultimate day of the trip, I hiked through Ourika Valley, a beautiful river valley in the Atlas Mountains. As expected, the YB3 caught most (though not all) of the route I took, but with fairly high valley walls and occasional overhangs that's to be understood. More surprisingly, Google managed to grab some of the hike as well, helped along by a small Wifi equipped rest-stop at the top of the route.

Here, we can again see an issue with Google's location jumping back to my hostel. According to this, I quickly popped 30 km back to Marrakech before continuing us the river valley a few minutes later.

## Looking for some conclusions?

I was advised to deactivate the YB3 when going inside, which I ignored at first. It seems to spend up to 4 minutes trying to get a satellite lock, presumably cranking up the power if it can't connect (much like your mobile phone would in a poor reception area). Popping into a museum for an hour isn't a big deal as it'll only try and connect to Iridium in vain a few times. Leaving activated in a metal locker overnight is a very different matter. ~11 hours in a Faraday cage (~22 connection attempts) burned through almost 10% of it's battery. By comparison, a normal day wandering around would barely use 1%. Follow the instructions, kids.

Once I learned how it worked, I got better performance from the YB3. After a few days, I noticed its connection attempts happened on the hour and half past every hour. If I noticed I was near to one of these times, I would generally move to get a better view of the sky. Sometimes this was a minor thing (stepping out from under an arch etc.) and sometimes it meant taking it out of my bag and moving it next to a window on a train or bus (the difference between under a seat and next to a train window was enough to affect Iridium connections). On one hand, altering my behaviour, if only slightly, to assuage the GPS gods was a little odd, but it's also only really necessary when outside of the YB3s intended environment and not something I needed to think about when hiking in the mountains.

I was really impressed with the accuracy and amount of data provided by YB Tracking. Certain points lined up perfectly with my recollection and the metadata was useful, showing my trip up the Eiffel tower and my exact seat on the FRS ferry to name a few examples.

{% img /images/posts/eiffel.jpg %}

Bugs aside, Google location tracking on a phone does a pretty good job of tracking locations around a city. Even with Wifi mostly turned off, the ample cell towers and GPS gave a pretty good track of my movements. The YB3 did less well in the cities, where popping inside a building or even a narrow alley can result in location data never getting through, while my would phone diligently record and upload the data next time it could connect. This caching of stored points would be a nice feature for the YB3.

I was a little disappointed with the YB3's failure to connect for the Paris -> Madrid trains, despite being placed on a windowsill, but it was a fast train and (as with most of what I put it through) certainly not its intended environment. By comparison, it worked extremely well on the Tangier -> Marrakech train, where my phone failed to gather any data at all.

So which should you use?

* *Want detailed tracks of your movement around cities?* It's close, but Google wins here - their data, supplemented by Wifi and cell towers, tends to give greater detail with greater reliability than the YB3.
* *Want detailed tracks of your movement outside of cities?* Probably a YB3 - outside, away from cell towers or Wifi, it was more reliable.
* *Want your friends to virtually stalk your movements in real time?* YB3 here, obviously.

They both have their place and I'm glad I got to play around and compare them. I'd be keen to take a YB3 on a mountaineering or hiking trip but would think twice before taking one with me on a city break. I've always got my phone with me, so the only consideration there is handing over detailed location data to Google. Is it worth it? Well, I'm still getting targeted Google ads for McDonalds in Morocco, so judge for yourself.
