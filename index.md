# Table of Contents
- [1. Introduction](#1-introduction) 
   * [1.1 Purpose](#11-purpose)
   * [1.2 Scope](#12-scope)
   * [1.3 References](#13-references)
- [2. Decomposition Description](#2-decomposition-description)
   * [2.1 Module Decomposition](#21-module-decomposition)
   	 - [2.1.1 Framework Package Interactions](#211-framework-package-interactions)
	 - [2.1.2 Shout! Service Package](#212-shout!-service-package)
	 - [2.1.3 Shout! Model Class Diagram](#213-shout!-model-class-diagram)
	 - [2.1.4 Shout! App Package Diagram](#214-shout!-app-package-diagram)
	 - [2.1.5 Shout! App Views and Controllers Diagram](#215-shout!-app-views-and-controllers-diagram)
	 - [2.1.6 Shout! App Services Diagram](#216-shout!-app-services-diagram)  
 - [3. Interface Descriptions](#3-interface-descriptions)
   * [3.1 Colour Guidelines](#31-colour-guidelines)
   * [3.2 Font Guidelines](#32-font-guidelines)
   * [3.3 App Icons](#33-app-icons)
   * [3.4 iOS Module Interface](#34-ios-module-interface)
   	 - [3.4.1 Introduction View](#341-introduction-view)
	 - [3.4.2 Home View](#342-home-view)
	 - [3.4.3 Chat View](#343-chat-view)
	 - [3.4.4 Settings View](#344-settings-view)
	 - [3.4.5 Message Settings View](#345-message-settings-view)
	 - [3.4.6 Settings Report View](#346-settings-report-view)
	 - [3.4.7 Settings About View](#347-settings-about-view)
 - [4. Detailed Design](#4-detailed-design)
    * [4.1 Module Detailed Design](#41-module-detailed-design)
     
# 1. Introduction

It is assumed that all of the users devices are compatible with Bluetooth Low Energy (BLE) with core specification version 4.0 and higher. This includes all iPhones 4s and higher, iPads generation 3 and higher, and any android devices version 4.3 and higher.

The application will only function within the limitations of the device’s own capabilities. It is assumed that all users using Shout! need to be within at least 200 feet of at least one other person in order to engage in conversation.			
## 1.1 Purpose
						
This design document will describe the architecture and system design of Shout!

## 1.2 Scope

The intended audience for this document will be the developers. They will use this document as an aid in development and to see all of the software requirements for Shout!

## 1.3 References

- Software Requirements Specification document for Shout!
- Analysis document for Shout!
- IEEE. IEEE Std 1016-1998 IEEE Recommended Practice for Software Design Descriptions. IEEE Computer Society, 1998

## 1.4 Overview 

This document is written following the guidelines of the IEEE Recommended Practice for Software Design Descriptions. It outlines the module, process, and data dependencies, as well as their detailed design and decomposition.

# 2. Decomposition Description 
## 2.1 Module Decomposition

### 2.1.1 Framework Package Interactions 

This design shows how the user interacts with the front end of the app (GUI), and then how the front end interacts with the backend
<img src="https://cp317s18.github.io/design/topleveldiagram.png" align="left" hspace="70" />

### 2.1.2 Shout! Service Package 

### 2.1.3 Shout! Model Class Diagram

<iframe allowfullscreen frameborder="0" style="width:640px; height:480px" src="https://www.lucidchart.com/documents/embeddedchart/c69ce3f8-67ac-4a84-aca1-aacb30c9be36" id="YWMJamWYOgXw"></iframe>

### 2.1.4 Shout! App Package Diagram

### 2.1.5 Shout! App Views and Controllers Diagram

### 2.1.6 Shout! App Services Diagram 

# 3. Interface Descriptions
## 3.1 Colour Guidelines 

<img src="https://cp317s18.github.io/design/colourtable.PNG" align="left" hspace="150" />

## 3.2 Font Guidelines 

- iOS Apple: System Default (San Francisco)
- Android:
  - Username colour: web safe colours

## 3.3 App Icons

<img src="https://cp317s18.github.io/design/appIcon.PNG" align="left" hspace="150" />

## 3.4 iOS Module Interface 
### 3.4.1 Introduction View 

<img src="https://cp317s18.github.io/design/IntroView.PNG" align="left" hspace="20"/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>

### 3.4.2 Home View 

<img src="https://cp317s18.github.io/design/HomeView.PNG" align="left" hspace="20"/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>

### 3.4.3 Chat View 

<img src="https://cp317s18.github.io/design/ChatView1.PNG" align="left" hspace="20"/>
<img src="https://cp317s18.github.io/design/ChatView2.PNG" align="left" hspace="20"/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>
<br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>

### 3.4.4 Settings View

### 3.4.5 Message Settings View 

### 3.4.6 Settings Report View 

### 3.4.7 Settings About View 

# 4. Detailed Design
## 4.1 Module Detailed Design

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


