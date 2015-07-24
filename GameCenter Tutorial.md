# GameCenter Integration in Swift
###### Written by Luke Solomon

## Introduction
Gamecenter is a Framework that Apple has made available in iOS for developers to very easily track player progress, integrate leaderboards, and allows players to challenge one another (also known as matchmaking). 

This tutorial will show you how to easily add GameCenter into your game to add all these totally awesome and amazing features. I will use my own game, [Seige](http://www.github.com/ares42/seige) for this and several tutorials in the future. [Feel free to clone or fork the repository on Github](http://www.github.com/Seige) (but star it so that I can get magical internet points).


## Before We Begin
#### ProTip: You must have a developer account! If you haven't signed up for one yet, [click here](https://developer.apple.com/programs/enroll/)! 

GameCenter integration is broken down into 3 steps:

1. [iOS Developer Center](https://developer.apple.com/membercenter/)
2. [iTunes Connect](https://itunesconnect.apple.com/)
3. XCode Implementation
	

##1. Developer Center
If you've never used the iOS developer center before, it can be a little intimidating. Don't fret, I'll carefully walk you through this trecherous, dated-looking website. Did I mention you should have a developer account by now? 

#### Please Note: If you've already set up your app in the iOS Developer Center, feel free to skip to the next section.

[Lets get started. Click here to go to the iOS Developer Center.](https://developer.apple.com/membercenter/)

### 1.
Enter your credentials...
![Login](Screenshots/iOS Developer Login.png)

### 2.
Click "Certificates, Identifiers, and Profiles"
![iOS Developer Center](Screenshots/Screen Shot 2015-07-20 at 11.24.49 AM.png)

### 3.
Under iOS Apps, Click "Identifiers"
![Certificates, ](Screenshots/Screen Shot 2015-07-20 at 11.24.58 AM.png)

### 4.
Click on the plus button in the top right corner
![](Screenshots/Screen Shot 2015-07-20 at 11.25.09 AM.png)

### 5.
In the name box, enter the name of your app
</br> Under APP ID Suffix, choose Explicit App ID
![](Screenshots/Screen Shot 2015-07-20 at 11.25.43 AM.png)
</br> In the Bundle ID field, enter the bundle identifier of your app. This can be found in Xcode in the following location:
![](Screenshots/Screen Shot 2015-07-20 at 3.32.53 PM.png)

### 6.
Make sure you have GameCenter selected before clicking continue. If you're going to be adding in any other features such as In-app purchases, click those.
![](Screenshots/Screen Shot 2015-07-20 at 11.25.47 AM.png)


### 7.
Check to make sure that everything is how you want it, and click Submit.
![](Screenshots/Screen Shot 2015-07-20 at 11.25.54 AM.png)
Awesome! You're all done. Now let's move on to iTunes Connect.
	

##2. iTunes Connect
iTunes Connect has a much cleaner interface than the iOS Developer Center, and tends to be a much nicer experience to use, which is good because you should expect to use iTunes Connect much more often. Get started by following [this link.](https://itunesconnect.apple.com/)

### 1.
Begin by signing into your Developer Account. (Yes, mine is fabio13. I made it in 2005. I was 15. It was middle school. Let's move on)
![](Screenshots/Screen Shot 2015-07-20 at 4.30.18 PM.png)


### 2.
Click My Apps
![](Screenshots/Screen Shot 2015-07-20 at 4.30.40 PM.png)


### 3.
Click the plus, then click New iOS App
![](Screenshots/Screen Shot 2015-07-20 at 4.31.11 PM.png)


### 4.
Fill in the fields.
![](Screenshots/Screen Shot 2015-07-20 at 4.32.26 PM.png)


### 5.
Click Game Center
![](Screenshots/Screen Shot 2015-07-20 at 4.32.32 PM.png)


### 6.
Enable GameCenter for a single game (unless you're feeling ambitious and have multiple games)
![](Screenshots/Screen Shot 2015-07-20 at 5.07.04 PM.png)

### 7.
Add Leaderboard
![](Screenshots/Screen Shot 2015-07-20 at 5.07.27 PM.png)

### 8.
Choose Single Leaderboard
![](Screenshots/Screen Shot 2015-07-20 at 5.09.00 PM.png)

### 9.
Fill in the fields. 
![](Screenshots/Screen Shot 2015-07-20 at 5.10.37 PM.png)

### 10.
Here you should fill in your 
Language, 

Name of the Leaderboard,

For Score format point, it should be fairly straightforward which you should pick on your game, based on what your player earns in game (points, dollars, etc.)

Score Format Suffixes,

and an optional image.
![](Screenshots/Screen Shot 2015-07-20 at 5.12.39 PM.png)

### 11.
The choice you make here should match how you are storing the user's score. 
![](Screenshots/Screen Shot 2015-07-20 at 5.19.54 PM.png)

##3. XCode

### 1.
The next step is to add the GameKit framework into your app. Start by clicking on your Project in XCode, then on your App Target, and select Build Phases. Now click Link Binary with Libraries.
![](Screenshots/Screen Shot 2015-07-21 at 8.47.21 AM.png)

### 2.
Click the plus button next to "Drag to reorder frameworks."
![](Screenshots/Screen Shot 2015-07-21 at 8.47.34 AM.png)

### 3.
Type GameKit into the search box, select it, and click add. 
![](Screenshots/Screen Shot 2015-07-21 at 8.47.45 AM.png)

### 4. 
This next part requires some decision on your part. Import GameKit into whichever scene that you want to present your High Score table. If you want to present it when a user taps a specfic button, you'll put the showLeaderboard() method into the selector for that button that we'll create below.
![](Screenshots/Screen Shot 2015-07-21 at 8.47.58 AM.png)

### 5. 
Now, we're going to add the following code as an extension to your class. You have the option to simply make your class a GKGameCenterControllerDelegate where you define your class, but by scrolling to the bottom of your class and putting your extension and all methods associated with the GKGameCenterControllerDelegate at the bottom, it really helps to clean your code up. It's also a snazzy new feature in Swift, so why not use it?

	// MARK: Game Center Handling
	extension Gameplay: GKGameCenterControllerDelegate {

	    func showLeaderboard() {
	        var viewController = CCDirector.sharedDirector().parentViewController!
	        var gameCenterViewController = GKGameCenterViewController()
	        gameCenterViewController.gameCenterDelegate = self
	        viewController.presentViewController(gameCenterViewController, animated: true, completion: nil)
	    }
	    
	    // Delegate methods
	    func gameCenterViewControllerDidFinish(gameCenterViewController: GKGameCenterViewController!) {
	        gameCenterViewController.dismissViewControllerAnimated(true, completion: nil)
	    }
    
	}
These are methods that we inherit from the GKGameCenterControllerDelegate. 

![](Screenshots/Screen Shot 2015-07-21 at 8.48.56 AM.png)

### 6.
Next, go to File->New->File. Now select iOS Source->Swift File-> Next. Save the file in your source folder, and erase the contents of the file, and replace them with the following code.

	//
	//  GameCenterInteractor.swift
	//  GameKitInteraction
	//
	//  Created by Stuart Breckenridge on 19/11/14.
	//  Copyright (c) 2014 Stuart Breckenridge. All rights reserved.
	//

	import UIKit
	import GameKit

	protocol GameCenterInteractorNotifications
	{
	    func willSignIn()
	    func didSignIn()
	    func failedToSignInWithError(anError:NSError)
	    func failedToSignIn()
	}


	class GameCenterInteractor: NSObject {
	    
	    // Public Variables
	    let localPlayer = GKLocalPlayer.localPlayer()
	    var delegate: GameCenterInteractorNotifications?
	    var callingViewController: UIViewController?
	    
	    // Singleton
	    class var sharedInstance : GameCenterInteractor {
	        struct Static {
	            static let instance : GameCenterInteractor = GameCenterInteractor()
	        }
	        return Static.instance
	    }
	    
	    //MARK: 1 Check authentication status
	    /**
	    This is the public method that begins the authentication process for the local player.
	    */
	    func authenticationCheck()
	    {
	        if (self.localPlayer.authenticated == false)
	        {
	            //Authenticate the player
	            println("The local player is not authenticated.")
	            self.authenticateLocalPlayer()
	        } else
	        {
	            println("The local player is authenticated")
	            // Register the listener
	            self.localPlayer.registerListener(self)
	            
	            // At this point you can download match data from Game Center.
	        }
	    }
	    
	    //MARK: 2 Authenticate the Player
	    /**
	    This is a private method to authenticate the local player with Game Center.
	    */
	    private func authenticateLocalPlayer()
	    {
	        self.delegate?.willSignIn()
	        
	        self.localPlayer.authenticateHandler = {(viewController : UIViewController!, error : NSError!) -> Void in
	            
	            if (viewController != nil)
	            {
	                dispatch_async(dispatch_get_main_queue(), {
	                    self.showAuthenticationDialogueWhenReasonable(presentingViewController: CCDirector.sharedDirector().parentViewController!, gameCenterController: viewController)
	                })
	            }
	                
	            else if (self.localPlayer.authenticated == true)
	            {
	                println("Player is Authenticated")
	                self.localPlayer.registerListener(self)
	                self.delegate?.didSignIn()
	            }
	                
	            else
	            {
	                println("User Still Not Authenticated")
	                self.delegate?.failedToSignIn()
	            }
	            
	            if (error != nil)
	            {
	                println("Failed to sign in with error:\(error.localizedDescription).")
	                self.delegate?.failedToSignInWithError(error)
	                // Delegate can take necessary action. For example: present a UIAlertController with the error details.
	            }
	        }
	    }
	    
	    //MARK: 3 Show Authentication Dialogue
	    /**
	    When appropriate, this function will be called and will present the Game Center login view controller.
	    
	    :param: presentingViewController The view controller that will present the game center view controller.
	    :param: gameCenterController     The game center controller.
	    */
	    func showAuthenticationDialogueWhenReasonable(#presentingViewController:UIViewController, gameCenterController:UIViewController)
	    {
	        presentingViewController.presentViewController(gameCenterController, animated: true, completion: nil)
	    }
	}

	extension GameCenterInteractor:GKLocalPlayerListener
	{
	    // Add functions for monitoring match changes.
	}

### 7.	
Now it's time to add the code that authenticates the user into GameCenter. First things first, I want you to pick up your iPhone/iPod/iPad and press the home button. Now go to Settings->GameCenter->Developer and turn Sandbox on.

![](Screenshots/IMG_6848.jpg)

### 8. 
If you've been wildly copying code and haven't been doing much thinking, now is the time to slow down.

    func didLoadFromCCB() {
        setUpGameCenter()
    }
    
    func setUpGameCenter() {
        
        let gameCenterInteractor = GameCenterInteractor.sharedInstance
        gameCenterInteractor.authenticationCheck()
        
    }

Did you wildly copy those methods into your code? Well I hope you're enjoying the errors you probably have. 

Now is the time for you to take this code I've written and understand it. In your didLoadFromCCB class, you should put the line 

	setUpGameCenter() 
	
Which is a method that you should have written in your class extension (remember that thing we did up above?) 

setUpGameCenter() is a function that authenticates your user. What the lines     
	
	let gameCenterInteractor = GameCenterInteractor.sharedInstance
    gameCenterInteractor.authenticationCheck()

do is access the Singleton class that we created above (GameCenter Interactor). Don't know what a Singleton is? Don't worry too much, it'll be covered in a later tutorial. [If you're really curious, here's a link to some reading about Singletons.](https://thatthinginswift.com/singletons/)

Once this code is functional, here's the popup that should appear when you run your game:
![code](Screenshots/IMG_6857.jpg)

If you're noticing that the game is crashing when you try to run the app, or that the GameCenter popup isn't appearing, try checking the console. You may need to sign into GameCenter on your device.


### 9.
Now we need to access the High Score table. Go to whichever scene you are deciding to show your  leaderboard in (in Seige, this scene is my Store.swift file) and make sure you have the code from the extension above. Now, all you need to do is call the showLeaderboard() method from that extension as shown below.

	    func openGameCenter() {
	        showLeaderboard()
	    }
	    
	}

	// MARK: Game Center Handling
	extension Store: GKGameCenterControllerDelegate {
    
	    func showLeaderboard() {
	        var viewController = CCDirector.sharedDirector().parentViewController!
	        var gameCenterViewController = GKGameCenterViewController()
	        gameCenterViewController.gameCenterDelegate = self
	        viewController.presentViewController(gameCenterViewController, animated: true, completion: nil)
	    }
	    
	    // Delegate methods
	    func gameCenterViewControllerDidFinish(gameCenterViewController: GKGameCenterViewController!) {
	        gameCenterViewController.dismissViewControllerAnimated(true, completion: nil)
	    }
    
	}

I seriously hope for your sake you're not just blindly copying every piece of code. Does it work? Does your leaderboard look like this? If you're having trouble, check out my Store.swift file to see how I did it.
![code](Screenshots/IMG_6858.jpg)

Well, that was cool...but there's no scores. Let's start sending high scores to GameCenter!

Head to your GameOver Scene.

First, you want to check to make sure that your user has set a new high score. For me, I'm using a method called checkForNewHighScores to check whether the data store in NSUserDefaults is higher than the current score. 
    
    func checkForNewHighScores(){
        
    }
    
If the current score is higher than what is saved as the previous high score in NSUserDefaults, i'll call the sharedInstance of my GameCenterInteractor class to call the reportHighScoreToGameCenter() Method.

    func reportHighScoreToGameCenter(){
        var scoreReporter = GKScore(leaderboardIdentifier: "YOUR LEADERBOARD IDENTIFIER GOES HERE")
        scoreReporter.value = Int64(GameStateSingleton.sharedInstance.score)
        var scoreArray: [GKScore] = [scoreReporter]
        
        GKScore.reportScores(scor4eArray, withCompletionHandler: {(error : NSError!) -> Void in
            if error != nil {
                println("Game Center: Score Submission Error")
            }
        })
    }

Here's where you'll have to do some more thinking. You'll have to make sure you load from your score singleton (or NSUserDefaults) and send that value into the scoreReporter variable, and then the GKScore.reportScores method will send the score off to GameCenter! Awesome.



