# Twilio Video Quick Start for Objective-C

## What is this project?

This quick start will help you get video chat integrated directly into your iOS applications using Twilio's Video SDK. This quick start is for Objective-C developers - if your app uses Swift, or if you are new to iOS, check out the Twilio Video Quick Start for Swift.

Inside this quick start project, you will find a Conversations View Controller that contains all of the functionality necessary to show two video streams on one iOS screen - one video stream for your phone's video camera, and one for a remote video stream.

You'll see how to set up key classes like TwilioAccessManager, TwilioConversationsClient, TWCLocalMedia, TWCConversation, and TWCCameraCapturer. All of these Twilio classes have related delegate protocols that the ConversationsViewController implements. This will get you all set up to implement a basic video chat in your own app.

## Prerequisites

This project uses Apple's Objective-C programming language for iOS, and the only supported way to develop iOS apps is on an Apple computer running OS X and XCode. We have tested this application with the latest versions of iOS (9.3.1) and XCode (7.3) at the time of this writing.

You do not need to have an Apple iPhone, iPod Touch, or iPad for testing. You can use the iOS Simulator that comes with XCode to do your testing, but the local video camera feed in the app will not work. If you have an iOS device, you can now run apps from XCode on your device without a paid developer account.

## Access Tokens and Servers

Using Twilio's Video client within your applications requires an access token. These access tokens can come from one of two places:

1) You can create a one-time use access token for testing on Twilio.com. This access token can be hard-coded directly into your mobile app, and you won't need to run your own server. 

2) You can run your own server that provides access tokens, based on your Twilio credentials. This server can either run locally on your development machine, or it can be installed on a server. If you run the server on your local machine, you can use the ngrok utility to give the server an externally accessible web addr ess. That way, you can run the quick start app on an actual device, instead of the iOS Simulator.sss

### Creating an Access Token


### Setting up a Video Server