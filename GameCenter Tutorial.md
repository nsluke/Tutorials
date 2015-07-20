---
title: "GameCenter Integration in Swift"
slug: tutorial-page-1
---

#GameCenter Integration in Swift
###### Written by Luke Solomon

##Introduction
Gamecenter is a Framework that Apple has made available in iOS for developers to very easily track player progress, integrate leaderboards, and allows players to challenge one another (also known as matchmaking). 

This tutorial will show you how to easily add GameCenter into your game to add all these totally awesome and amazing features. I will use my own game, [Seige](http://www.github.com/ares42/seige) for this and several tutorials in the future. Feel free to clone or fork the repository on Github (but star it so that I can get magical internet points).


##Before We Begin
####Please Note: You must have a developer account! If you haven't signed up for one yet, [click here](https://developer.apple.com/programs/enroll/)! 

GameCenter integration is broken down into 3 steps:

1. [iOS Developer Center](https://developer.apple.com/membercenter/)
2. [iTunes Connect](https://itunesconnect.apple.com/)
3. XCode Implementation
	

##1. Developer Center
If you've never used the iOS developer center before, it can be a little intimidating. Don't fret, I'll carefully walk you through this trecherous, dated-looking website. Did I mention you should have a developer account by now? 

[Lets get started. Click here to go to the iOS Developer Center.](https://developer.apple.com/membercenter/)

![Login](Screenshots/iOS Developer Login.png)
Enter your credentials...

![iOS Developer Center](Screenshots/Screen Shot 2015-07-20 at 11.24.49 AM.png)
Click "Certificates, Identifiers, and Profiles"

![Certificates, ](Screenshots/Screen Shot 2015-07-20 at 11.24.58 AM.png)
Under iOS Apps, Click "Identifiers"

![](Screenshots/Screen Shot 2015-07-20 at 11.25.09 AM.png)
Click on the plus button in the top right corner

![](Screenshots/Screen Shot 2015-07-20 at 11.25.43 AM.png)
In the name box, enter the name of your app

</br> Under APP ID Suffix, choose Explicit App ID

</br> In the Bundle ID field, enter the bundle identifier of your app. This can be found in Xcode in the following location:
![](Screenshots/Screen Shot 2015-07-20 at 3.32.53 PM.png)


![](Screenshots/Screen Shot 2015-07-20 at 11.25.47 AM.png)
Make sure you have GameCenter selected before clicking continue. If you're going to be adding in any other 
features such as In-app purchases, click those.

![](Screenshots/Screen Shot 2015-07-20 at 11.25.54 AM.png)
Check to make sure that everything is how you want it, and click Continue.

Awesome! You're all done. Now let's move on to iTunes Connect.
	

##2. iTunes Connect
iTunes Connect has a much cleaner interface than the iOS Developer Center, and tends to be a much nicer experience to use, which is good because you should expect to use iTunes Connect much more often. Get started by following [this link.](https://itunesconnect.apple.com/)


![](Screenshots/Screen Shot 2015-07-20 at 4.30.18 PM.png)
Begin by signing into your Developer Account. (Yes, mine is fabio13. I made it in 2005. I was 15. It was middle school. Let's move on)

![](Screenshots/Screen Shot 2015-07-20 at 4.30.40 PM.png)
Click My Apps

![](Screenshots/Screen Shot 2015-07-20 at 4.31.11 PM.png)
Click the plus, then click New iOS App


![](Screenshots/Screen Shot 2015-07-20 at 4.32.26 PM.png)
Fill in the fields.

![](Screenshots/Screen Shot 2015-07-20 at 4.32.32 PM.png)
Click GameCenter

![](Screenshots/Screen Shot 2015-07-20 at 5.07.04 PM.png)
Enable GameCenter for a single game (unless you're feeling ambitious and have multiple games)

![](Screenshots/Screen Shot 2015-07-20 at 5.07.27 PM.png)
Add Leaderboard

![](Screenshots/Screen Shot 2015-07-20 at 5.09.00 PM.png)
Choose Single Leaderboard

![](Screenshots/Screen Shot 2015-07-20 at 5.10.37 PM.png)
Fill in the fields. For Score format point, it should be fairly straightforward which you should pick on your game, based on what your player earns in game (points, dollars, etc.)

![](Screenshots/Screen Shot 2015-07-20 at 5.12.39 PM.png)


![](Screenshots/Screen Shot 2015-07-20 at 5.19.54 PM.png)
