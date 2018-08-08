# Table of Contents
- [1. Introduction](#1-introduction) 
   * [1.1 Purpose](#11-purpose)
   * [1.2 Scope](#12-scope)
   * [1.3 References](#13-references)
- [2. Planned Implementation](#2-planned-implementation)
   * [2.1 Choice of Language](#21-choice-of-language)
   * [2.1.2 Previously Planned Language](#212-previously-planned-language)
- [3. Decomposition Description](#3-decomposition-description)
   * [3.1 Module Decomposition](#31-module-decomposition)
   	 - [3.1.1 Framework Package Interactions](#311-framework-package-interactions)	 
	 - [3.1.2 Shout! Model Class Diagram](#312-shout!-model-class-diagram)
- [4. Interface Descriptions](#4-interface-descriptions)
   * [4.1 Colour Guidelines](#41-colour-guidelines)
   * [4.2 Font Guidelines](#42-font-guidelines)
   * [4.3 App Icons](#43-app-icons)
   * [4.4 Module Interface](#44-module-interface)
   	 - [4.4.1 Bluetooth View](#441-bluetooth-view)
	 - [4.4.2 Home View](#442-home-view)
	 - [4.4.3 Chat View](#443-chat-view)
	 - [4.4.4 Settings View](#444-settings-view)
	 - [4.4.5 Notification View](#445-notification-view)
	 - [4.4.6 Report View](#446-report-view)
	 - [4.4.7 About View](#447-about-view)
 - [5. Detailed Design](#5-detailed-design)
    * [5.1 Module Detailed Design](#51-module-detailed-design)
 - [6. Maintenance](#6-maintenance)
    * [6.1 Corrective](#61-corrective)
    * [6.2 Perfective](62-perfective)
    * [6.3 Adaptive](#63-adaptive)
     
# 1. Introduction

It is assumed that all of the users devices are compatible with Bluetooth Low Energy (BLE) with core specification version 4.0 and higher. This includes all iPhones 4s and higher, iPads generation 3 and higher, and any android devices version 4.3 and higher. The application will be available for download on the Apple App store and Anroid Play Store for free.

The application will only function within the limitations of the device’s own capabilities. It is assumed that all users using Shout! need to be within at least 200 feet of at least one other person in order to engage in conversation.	

## 1.1 Purpose
						
This design document will describe the architecture and system design of Shout!

## 1.2 Scope

The intended audience for this document will be the developers. They will use this document as an aid in development and to see all of the software requirements for Shout!

## 1.4 References

- Software Requirements Specification document for Shout!
- Analysis document for Shout!
- IEEE. IEEE Std 1016-1998 IEEE Recommended Practice for Software Design Descriptions. IEEE Computer Society, 1998

## 1.4 Overview 

This document is written following the guidelines of the IEEE Recommended Practice for Software Design Descriptions. It outlines the module, process, and data dependencies, as well as their detailed design and decomposition.

# 2. Planned Implementation
## 2.1 Choice of Language

On the iOS side of *Shout!*, Swift is used to implement the app. Both Swift and Objective-C are the only languages that have been used to develop iOS applications in terms of compatibility. Swift is used as the main language as it was specifically designed by Apple, making it compliant with the standards that Apple has set. Objective-C is sparsely used in order to implement operational functions not available in the current version of Swift. 

For the Android side of *Shout!*, Java is used to implement the app. It is the the primary development language for Android. As such, there are numerous of resources available for reference and support. Since this application will be running on different hardware platforms (Pixel, Samsung Galaxy, HTC), Java is the most efficient language to compile on these different platforms. 

## 2.1.2 Previously Planned Language

Flutter is an open-source application used to develop apps for both iOS and Android using one language called Dart, making it very portable. This way, applications are consistent on both types of devices. Since Shout! was intended to be created on both platforms, Flutter was the initial plan in terms of app development. This suggestion was later dismissed as there were several issues in using this method. Installation was slow and hard to understand, there weren’t many resources on several topics such as layout, or functionality and the capabilities of the application did not meet our needs. For instance, bluetooth integration was difficult to pursue. It was also discovered that certain methods or plugins had to be rewritten in Dart, which would have made the process more time consuming than it needed to be. Using each platform’s native development software, Android Studio and XCode, was chosen instead, as outlined in 3.1.

# 3. Decomposition Description 
## 3.1 Module Decomposition

### 3.1.1 Framework Package Interactions 

This design shows how the user interacts with the front end of the app (GUI), and then how the front end interacts with the backend
<img src="https://cp317s18.github.io/design/topleveldiagram.png" align="left" hspace="70" />

### 3.1.2 Shout! Model Class Diagram

<iframe allowfullscreen frameborder="0" style="width:640px; height:480px" src="https://www.lucidchart.com/documents/embeddedchart/c69ce3f8-67ac-4a84-aca1-aacb30c9be36" id="YWMJamWYOgXw"></iframe>

### Android

<iframe allowfullscreen frameborder="0" style="width:640px; height:480px" src="https://www.lucidchart.com/documents/embeddedchart/5fbcf4b6-55c7-4a11-ac40-b141330de8d4" id="X0cWvJwv3wnA"></iframe>

# 4. Interface Descriptions
## 4.1 Colour Guidelines 

<img src="https://github.com/CP317S18/design/blob/master/ColourGuidelines.png" align="left" hspace="50" />

## 4.2 Font Guidelines 

- iOS: System Default (San Francisco)
- Android: Roboto
- Username colour: Web Safe Colours

## 4.3 App Icons

<img src="https://cp317s18.github.io/design/appIcon.PNG" align="left" hspace="150" />

## 4.4 Module Interface 
### 4.4.1 Bluetooth View 

<img src="https://github.com/CP317S18/design/blob/master/BluetoothID.png" align="left" hspace="20"/>

| Field | Type | Description | Gesture | 
| ----- | ---- | ----------- | ------- |
|lblChat|Label|Describes purpose of application||
|imgBluetooth|Image|Visualization of the Bluetooth symbol||
|btnStart|Button|Allows entrance to application only after bluetooth has been enable. |→  Home View|

### 4.4.2 Home View 

<img src="https://github.com/CP317S18/design/blob/master/HomeID.png" style="width:2000px" align="left" hspace="20"/>

| Field | Type | Description | Gesture | 
| ----- | ---- | ----------- | ------- |
|imgLogo|Image|Application logo||
|lblNumber|Label|Dynamic number displaying the amount of reachable people from user current position||
|lblNearby|Label|Describes the purpose of the number||
|lblDisclaimers|Label|A disclaimer statement | → Terms of Service |
|btnEnter|Button|Allows entrance to Chat View only after a username has been submitted |→ Chat View |
|btnSettings|Button| Brings user to the Settings View where they can change preferences | → Setting View |
|txtfieldUsername | Text Field | Required username input before entrance to Chat View This is how the user will be identified in the chat. Must be distinct and 15 characters in length| |

### 4.4.3 Chat View 

<img src="https://github.com/CP317S18/design/blob/master/ChatID.png" align="left" hspace="20"/>

| Field | Type | Description | Gesture | 
| ----- | ---- | ----------- | ------- |
|lblNumber|Label|Dynamic number displaying the amount of reachable people from user current position||
|txtfieldInput|Text Field|User enters message to be sent to other reachable users||
|btnBack|Button|Navigation Bar: Brings user back to Home View|→ Home View|
|btnRefresh|Button|Navigation Bar: Refresh the Chat View|→ Chat View|
|tableChat|Table|Displays the messages sent and received by application users. <p><p>Username Column: Colour is randomly assigned from web safe colour collection. Randomization is local to the user application. </p></p> <p>Message Column: Display message sent by users. Message gets text wrapped if length exceeds one line</p>||


### 4.4.4 Settings View

<img src="https://github.com/CP317S18/design/blob/master/SettingID.png" size="200" align="left" hspace="20"/>

| Field | Type | Description | Gesture | 
| ----- | ---- | ----------- | ------- |
|btnBack|Button|Navigation Bar: Brings user back to Home View|→ Home View|
|btnNotif|Button|Brings user to Notification View <p><p>Within a table with two columns: image and label</p></p> |→ Notification View|
|btnReport|Button|Brings user to Report View <p><p>Within a table with two columns: image and label</p></p> |→ Report View|
|btnAbout|Button|Brings user to About View <p><p>Within a table with two columns: image and label</p></p> |→ About View|

### 4.4.5 Notification View 

<img src="https://github.com/CP317S18/design/blob/master/NotificationID.png" size="200" align="left" hspace="20"/>

| Field | Type | Description | Gesture | 
| ----- | ---- | ----------- | ------- |
|btnBack|Button|Navigation Bar: Brings user back to Settings View|→ Setting View|
|toggleShow|Toggle Button|Turns on/off application notification alerts <p><p>Within a table with two columns: label and toggle button</p></p> ||
|toggleSound|Toggle Button|Turns on/off application notification sound alerts <p><p>Within a table with two columns: label and toggle button</p></p> ||
|toggleVibrate|Toggle Button|Turns on/off application notification vibrate alerts <p><p>Within a table with two columns: label and toggle button</p></p> ||
|btnReset|Button|Resets options to default settings||

### 4.4.6 Report View 

<img src="https://github.com/CP317S18/design/blob/master/ReportID.png" size="200" align="left" hspace="20"/>

| Field | Type | Description | Gesture | 
| ----- | ---- | ----------- | ------- |
|btnBack|Button|Navigation Bar: Brings user back to Settings View|→ Setting View|
|btnSend|Button|Sends user report to the developer’s team email. Internet connection is required. If there is no access to the internet, a pop-up alert will tell user to turn on their WiFi connection. | |
|lblDescribe|Label|Instructs user how to send the report.| |
|txtfieldReport|Text Field|User inputs the message they want to send to the developer team. <p><p>If report is successfully received, text field will be cleared of the messaged typed.</p></p>|

### 4.4.7 About View 

<img src="https://github.com/CP317S18/design/blob/master/AboutID.png" size="200" align="left" hspace="20"/>

| Field | Type | Description | Gesture | 
| ----- | ---- | ----------- | ------- |
|btnBack|Button|Navigation Bar: Brings user back to Settings View|→ Setting View|
|btnTOS|Button|Brings user to terms of service and privacy policy documents. <p><p>Within a table: label and arrow button</p></p>|→ Terms of Service and Privacy Policy documents|
|btnSources|Button|Brings user to Sources View with that credits all the third-party sources that were used to create the application <p><p>Within a table: label and arrow button</p></p>|→ Sources View|
|btnTeam|Button|Brings user to Team View with details about the developer team <p><p>Within a table: label and arrow button</p></p>|→ Team View|

# 5. Detailed Design
## 5.1 Module Detailed Design

setUsername()
 1. takes the user created string
 2. new everytime the user re-enters the chat (temporary)

joinChat()
 1. allows user to join chat using encryption key
 2. automatically creates a Message object 
 3. user now sees all the chats from all connecting nodes, within range 
 
leaveChat()
 1. user now leaves the message loop
 2. they no longer recieve updates from the chat

receiveMessage()
 1. application of chat interface
 2. using the mesh network and BLE, this enables the chat to accept and view messages from other users (nodes)

sendMessage()
 1. application of chat interface 
 2. using the mesh network and BLE, this enables the chat to send their message to all connected users (nodes)

# 6. Maintenance
## 6.1.1 Corrective

A feature on *Shout!* allows users to report bugs or issues regarding the functionality of the app. Shout! aims to use this information to perform corrective maintenance by receiving these requests, analyzing how it would be solved, and documenting all fixes implemented.

## 6.1.2 Perfective

Due to the time constraint, the development of the app was simplified to the necessary features needed in order to ensure the application is executable. New features and capabilities are to be implemented once the application is reliable and complete through perfective maintenance.

Additional features or ideas will be taken from popular requests from users, new or existing features on other messaging platforms and more. Some examples of features that is on the shortlist to be implemented in the application is listed below:
* Sharing Location/Viewing the distance of people connected
* Add a time-out interval to prevent spam of messages from certain user
* Adding the ability to filter the messages through the use of hashtag
* Adding additional colour schemes for the app (themes)
* Adding the ability to change the application icon

## 6.1.3 Adaptive

As iOS and Android versions are updated, *Shout!* will be updated as necessary to adapt to the changing compatibilities though adaptive maintenance. 
