## From Pet Project to Production

Back in October 2020 I decided to start a pet project with a goal to learn a new technology. I noticed people on Twitter were saying how much they like the Developer Experience of Blitz JS so I decided to use it in this pet project.

But then I thought, this pet project could be something useful to our employees. So, after a little research I decided to build an Absence Tracker, so we can ditch the Telegram group where we reported our absences.

## The Inception
I decided to use [Chakra UI](http://chakra-ui.com/) along with [Blitz JS](http://blitzjs.com/), because it's rich with components and it allows me to quickly build the UI. And it looks 😍. I did a little planning and Database Design in [diagrams.net](https://diagrams.net) and started to layout the pages.

One month in I decided to stream the whole development process on  [Twitch](https://twitch.tv/nikolovlazar)! That was one of my best decisions. I've met a lot of cool folks on my streams and they gave me some interesting ideas regarding the implementation. All of my streaming archive can be found on my [YouTube channel](https://www.youtube.com/channel/UCTexaJMnN_Pv6TVueQ61-oQ).

## The Challenges
One of the challenges was keeping up with the changes of Blitz JS. When I started the project Blitz was still in alpha. And as we all know, alpha software tends to change and it's totally normal. Blitz JS is maturing in a great way, but keeping track of the changes did require a lot of release notes reading and checking out past PRs.

Another challenge was using Chakra UI with an experimental version of React (default by Blitz JS). I couldn't find a good workaround, so I decided to use the stable version of React. The drawback of that was disabling the Concurrent mode of React, even though I really liked that feature.

## The Benefits
This tech stack grew to be my favourite. It really allows you to build your app in a record time! I really like the DX of Blitz JS and Chakra UI and their intuitive APIs. I'll definitely use these technologies for my future projects too.

As I mentioned, streaming on Twitch was one my best decision. I've gotten a lot of followers and met a lot of cool folks that hung around my streams. I've also gotten the attention of Chakra UI! They liked my streams and invited me to join the [core team](https://chakra-ui.com/team) 🤩

## The Finale
I decided to bring my colleague @[Ilija Boshkov](@boshkov) as a guest to my live stream where we Dockerized the app and deployed it on our company servers. There was a readymade Docker image for Blitz JS, but we decided to build our own. It wasn't complicated at all. After we set up everything in a Docker Compose network, the deployment was a single line command.

Next on our list is to onboard all of the employees, synchronise the old data with the new platform and officially start using the new platform. It started off as a pet project, a "placeholder" for me to learn a new technology, but it grew into a cool usable app that will make our lives easier. It's been a wild ride, but I'd do it all over again without thinking.