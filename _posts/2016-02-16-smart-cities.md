---
layout: post
title: Big Data and Smart Cities
excerpt: By 2050, 75 percent of the world's population will live in cities. How can data and technology optimize city services and improve quality of life?
---

I've always been interested in urbanization and how cities can support their residents. I wrote my undergraduate thesis on [informal community planning in Dharavi](https://drive.google.com/file/d/0B4gJbxu8oVBVMXVYMHM3MkhlSzQ/view), one of the largest slums in the world. Before Metis, I worked at an economic development, public policy, and urban planning consulting firm, where I was able to work on several game-changing urban planning initiatives, including the Mayor's most recent [OneNYC](http://www1.nyc.gov/html/onenyc/index.html) plan.

When you think of city services, you don't necessarily think of the latest, cutting edge advances in technology. While this might hold true in the majority of cities, there are several cities in the world that are embracing data and technology to increase the efficiency and improve the quality of services, while increasing citizen engagement--better known as the "smart cities" movement. As the world continues to urbanize, these new technologies are becoming ever more critical to manage growth.

Some of my favorite examples:

**Traffic monitoring in Los Angeles, CA**  
Los Angeles is known for its terrible traffic. What many don't know is that it could be worse! Since the late 1980s, LA has been implementing an Automated Traffic Surveillance and Control system (ATSAC) to measure and improve traffic flow. There are about 18,000 sensors installed underneath roadways in the city along with about 400 cameras at critical intersections. These sensors collect data on traffic flow, which then triggers different behaviors from traffic lights to optimize traffic conditions.

For example, sensors in bus lanes can detect when a bus is running behind schedule, and traffic lights in the bus lane will stay green longer to expedite bus traffic. Another cool thing they've done is program sundown times into walk signals in predominantly Jewish neighborhoods so that people are better able to move around while observing the Sabbath.

Overall, the city estimates that these measures have reduced traffic times by about 15 percent. Probably not a noticeable difference if you're in gridlock traffic every day, but definitely a start.

Read more [here](http://trafficinfo.lacity.org/about-atsac.php).

**Citizen engagement in Uganda through U-report**  
U-report is a citizen engagement initiative run in Uganda by UNICEF in partnership with IBM. The program aims to get feedback from teenagers about all sorts of civic-related uses through a SMS system. Typically, a poll question is sent out and responses are collected, but users can also text suggestions to the main U-report line.

The system uses a Naive Bayes text classifier to classify the subject matter and relevance of each text. Once the texts are processed, they're sent over to the relevant city agency, which is then able to address the issue as needed.

U-report has engaged about 200,000 users, who send approximately 100,000 messages per week. Since its inception U-report has alerted officials to an ebola outbreak, allowed aid workers to direct youth concerned about AIDS/HIV to get (confidentially) tested at local clinics, and alerted UNICEF to dispatch assistance following a flood instance.

Read more about the program and the text classification algorithm [here](http://prem-melville.com/publications/unicef-kdd2013.pdf).

**Integrated sensor systems in Santander, Spain**  
The city of Santander, Spain (population < 200,000) is one of the leaders in implementing an integrated smart city system. Since 2009, over 12,500 sensors have been planted across Santander's downtown (think under asphalt, on cars/buses, and on lamp posts). These sensors collect anything from air quality metrics to stats on the fullness of trash cans to traffic condition data, which are then used to streamline city services.

For example, sensors in trash cans can measure how full they are, and trash collection routes can be optimized to only go to trash cans that need servicing. The city estimates that they've reduced their waste collection costs by about 20 percent because of this system.

Another cool feature that I wish we had in New York City is parking space counters. In Santander, there are magnetic sensors underneath parking spaces. When a car parks in a space, the sensor knows that its occupied, and then automatically updates the free parking count in that location. Data is aggregated for multiple parking locations and broadcasted on signs across the city that direct you to the nearest available parking spaces.

Read more [here](http://www.governing.com/topics/urban/gov-santander-spain-smart-city.html).

**So what about New York?**  
As a lifelong New Yorker, I've been waiting for the city to catch up on these new technologies. With the announcement of the first "quantified community" at Hudson Yards, a planned 28-acre mixed-use development on Manhattan's west side, I think we're getting close!

From Hudson Yards:

```
"Hudson Yards will harness big data to innovate, optimize, enhance and personalize the employee, resident and visitor experience ... to create the most efficiently navigated and environmentally attuned neighborhood in New York."
```

Not only will Hudson Yards monitor the standard signals of pedestrian activity, air quality, waste creation, and others that are prevalent in existing smart cities, it will be the first smart city that will be built from the ground up; that is--the sensors and resulting smart systems will be integrated into the way buildings and infrastructure are built.

The plan is to use the data collected from Hudson Yards to not only improve services on site, but also to study the ecosystem of residents and the built environment, which may inform the management of other cities in the future.

Of course, with all of this data collection comes a lot of privacy concerns. Most data that's currently being collected is related to monitoring the environment--impersonal, anonymized metrics such as air quality and waste levels. As with new companies like [Placemeter](http://placemeter.com) that are using computer vision to analyze videos of street activity, I suspect that future advancements of smart city technology will start becoming more personally identifiable. I'm not sure which side will win out, but I'm excited to be part of the conversation.
