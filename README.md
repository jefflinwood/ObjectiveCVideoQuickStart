# Twilio Video Quick Start for Objective-C

## Get up and Running

1) Create a Twilio Account if you don't already have one

2) Download this project and run `pod install` to install the Twilio frameworks

3) Get an access token [Generate an Access Token](https://www.twilio.com/user/account/video/dev-tools/testing-tools)

4) Paste the access token into ConversationsViewController.m

5) Run your app (preferably on an iOS device, but could be on the Simulator)

6) Start up a video chat from the above web page!

## What is this project?

This quick start will help you get video chat integrated directly into your iOS applications using Twilio's Video SDK. This quick start is for Objective-C developers - if your app uses Swift, or if you are new to iOS, check out the Twilio Video Quick Start for Swift.

Inside this quick start project, you will find a Conversations View Controller that contains all of the functionality necessary to show two video streams on one iOS screen - one video stream for your phone's video camera, and one for a remote video stream.

You'll see how to set up key classes like TwilioAccessManager, TwilioConversationsClient, TWCLocalMedia, TWCConversation, and TWCCameraCapturer. All of these Twilio classes have related delegate protocols that the ConversationsViewController implements. This will get you all set up to implement a basic video chat in your own app.

## Prerequisites

This project uses Apple's Objective-C programming language for iOS, and the only supported way to develop iOS apps is on an Apple computer running OS X and XCode. We have tested this application with the latest versions of iOS (9.3.1) and XCode (7.3) at the time of this writing.

You do not need to have an Apple iPhone, iPod Touch, or iPad for testing. You can use the iOS Simulator that comes with XCode to do your testing, but the local video camera feed in the app will not work. If you have an iOS device, you can now run apps from XCode on your device without a paid developer account.

## Twilio Library Setup for the Project

You will need to add the Twilio Conversations Client library, and its dependency, the Twilio Commons library to your project for this quick start project to work. There are two different options for doing this:

1) Using the [Cocoapods](https://cocoapods.org/) dependency management system. 

2) Installing the Twilio frameworks yourself, using the directions on the [Twilio Video SDK Download Page](https://www.twilio.com/docs/api/video/sdks)

You only need to do one or the other, not both!

### Using Cocoapods

First, you will need to have Cocoapods installed on your Mac, so go ahead and do that if you haven't already - the directions are here: [Getting Started with Cocoapods](https://guides.cocoapods.org/using/getting-started.html). If you're not sure, type `pod --version` into a command line. 

Next, just run `pod install` from the command line in the top level directory of this project. Cocoapods will install the Twilio libraries and then set up a .xcworkspace file that you will use to run your project from now on. 

### Installing Twilio Frameworks

Download the latest versions of the Twilio Conversations and Twilio Commons frameworks from the [Twilio Video SDK Download Page](https://www.twilio.com/docs/api/video/sdks). After uncompressing those download files, drag and drop the frameworks (TwilioCommon.framework and TwilioConversationClient.framework) onto your project in XCode. Make sure that the checkbox next to the ObjCVideoQuickstart target is checked. You may want to copy the files if needed into your project as well, so you aren't referencing frameworks from your Downloads folder.

In addition to the Twilio frameworks, if you aren't using Cocoapods, you will have to add several iOS frameworks, as well as making one change to your linker flags. Let's set up the frameworks. In XCode, select your project, and then select the General tab. At the bottom is the Linked Frameworks and Libraries section, which you may need to expand with the black dropdown arrow. Use the + button below the two Twilio frameworks to add all of these frameworks:

AudioToolbox.framework
VideoToolbox.framework
AVFoundation.framework
CoreTelephony.framework
GLKit.framework
CoreMedia.framework
SystemConfiguration.framework
libc++.tbd

After adding those frameworks, there is another change we need to make on Build Settings. Select the Build Settings tab, and then find Other Linker Flags - you can type it into the search box to quickly narrow down the list.

Add -ObjC as a linker flag - select the blank values box, and type -ObjC into the box at the top of the popup. Be sure to hit the enter key to save it. You'll see -ObjC in bold as a linker flag after you've finished.

## Access Tokens and Servers

Using Twilio's Video client within your applications requires an access token. These access tokens can come from one of two places:

1) You can create a one-time use access token for testing on Twilio.com. This access token can be hard-coded directly into your mobile app, and you won't need to run your own server.

2) You can run your own server that provides access tokens, based on your Twilio credentials. This server can either run locally on your development machine, or it can be installed on a server. If you run the server on your local machine, you can use the ngrok utility to give the server an externally accessible web address. That way, you can run the quick start app on an actual device, instead of the iOS Simulator.

### Generating an Access Token

The first step is to [Generate an Access Token](https://www.twilio.com/user/account/video/dev-tools/testing-tools) from the Twilio developer console. Use whatever clever username you would like for the identity. You will get an access token that you can copy and paste into ConversationViewController.m - if you go down this path, be sure to follow the directions in the comments in the viewDidLoad() method at the top of the source file - you will need to uncomment one line, and comment out another.

Once you have that access token in place, scroll down to the bottom of the page and you will get a web-based video chat window in the Twilio developer console that you can use to communicate with your iPhone app! Just invite that identity you just named above!

### Setting up a Video Chat Web Server

If you want to be a little closer to a real environment, you can download one of the video quickstart applications - for instance, [Video Quickstart: PHP](https://github.com/TwilioDevEd/video-quickstart-php) and either run it locally, or install it on a server.

 You'll need to gather a couple of configuration options from your Twilio developer console before running it, so read the directions on the quickstart. You'll copy the config.example.php file to a config.php file, and then add in these credentials:
 
 Credential | Description
---------- | -----------
Twilio Account SID | Your main Twilio account identifier - [find it on your dashboard](https://www.twilio.com/user/account/video).
Twilio Video Configuration SID | Adds video capability to the access token - [generate one here](https://www.twilio.com/user/account/video/profiles)
API Key | Used to authenticate - [generate one here](https://www.twilio.com/user/account/messaging/dev-tools/api-keys).
API Secret | Used to authenticate - [just like the above, you'll get one here](https://www.twilio.com/user/account/messaging/dev-tools/api-keys).

#### A Note on API Keys

When you generate an API key pair at the URLs above, your API Secret will only
be shown once - make sure to save this in a secure location.

#### Running the Video Quickstart with ngrok

Because we suggest that you run your video chat application on actual iOS device so that you can use the camera on the device, you'll need to provide an externally accessible URL for the app (the iOS simulator will be fine with localhost). The [ngrok](https://ngrok.com/) tool creates a publicly accessible URL that you can use to send HTTP/HTTPS traffic to a server running on your localhost. Use HTTPS to make web connections that retrieve a Twilio access token.

When you get a URL from ngrok, go ahead and update ConversationViewController.m with the new URL. You won't need to comment or uncomment any lines out from the application, but you will need to update the code if your ngrok URL changes.

For this quick start, the Application transport security settings are set to allow arbitrary HTTP loads for testing your app. For production applications, you'll definitely want to retrieve access tokens over HTTPS/SSL.

## Have fun!

This is an introduction to Twilio's Video Conversations SDK on iOS. From here, you can start building applications that use video chat across the web, iOS, and Android platforms.