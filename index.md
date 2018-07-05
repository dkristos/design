# Table of Contents
- [1. Assumptions and Dependencies](#1-assumptions-and-dependencies) 
   * [1.1 End User Characteristics](#11-end-user-characteristics)
   * [1.2 End User Constraints](#12-general-constraints)
   * [1.1 Goals and Guidelines](#13-goals-and-guidelines)  
- [2. Architectural Strategies](#2-architectural-strategies)
   * [2.1 Reuse](#21-reuse)
   * [2.2 Currently](#22-currently)
   * [2.3 Future](#23-future)  
 - [3. Interfaces](#3-interfaces)
   * [3.1 User Interfaces](#31-user-interfaces)
   * [3.2 Software Interfaces](#32-software-interfaces)
   * [3.3 Communication Mechanisms](#33-communication-mechanisms)
 - [4. System Architecture](#4-system-architecture)
   * [4.1 Top Level Diagram](#41-top-level-diagram) 	
     
# 1. Assumptions and Dependencies 

It is assumed that all of the users devices are compatible with Bluetooth Low Energy (BLE) with core specification version 4.0 and higher. This includes all iPhones 4s and higher, iPads generation 3 and higher, and any android devices version 4.3 and higher.

The application will only function within the limitations of the device’s own capabilities. It is assumed that all users using Shout! need to be within at least 200 feet of at least one other person in order to engage in conversation.			
## 1.1 End User Characteristics
						
The application should eventually allow for upgrades, ie. features that can send gifs, and pictures
- Back-end migration abilities between iOS and Android 
- Clean and fast message updates, minimal lagging
- Buffers in place when there is an overflow of activity
- Easy to understand structure and design 
- Must work with no wifi or data connection

## 1.2 General Constraints

Shout is intended to allow people in close vicinity to chat to each other anonymously. This means that it must:
- Work on most modern smartphones, both Android and iOS
- Provide a secure enough connection to prevent data leakage from device to device

## 1.3 Goals and Guidelines

All design and code must be implemented and tested within the month-long deadline. All material that has been worked on, will be documented accordingly. Corresponding diagrams must be accurate and complete.

# 2. Architectural Strategies 
## 2.1 Reuse

There are no existing code components being used in this project.

## 2.2 Currently

Shout will make full use of Bluetooth Mesh Libraries rather than assembling each packet ourselves.

## 2.3 Future 

The application is versatile in its ability to update, enhance and create new features. The code should be primarily self-sufficient so maintenance should not be difficult. 

# 3. Interfaces 
## 3.1 User Interfaces

- Due to the fact that we only have one class of user, there will only be one interface
- All users will have the ability to set and change their username
- Error messages will show for usernames that are past the character limit or contain unsupported characters and prevent them from setting their name to that
- All users will have the ability to join the livechat and send and receive messages
- Error messages will show for all messages that are beyond the character limit and prevent the user from sending that message
- A warning message will show for users approaching to message frequency limit and upon hitting it, their message sending capabilities will be put on cooldown.

## 3.2 Software Interfaces

- Our software will be downloadable from the Google Play Store as well as the iOS App Store. 
- The application will run on the Android and iOS operating systems

## 3.3 Communication Mechanisms 

The system does not rely on a external database but rather it holds temporary, local data in the form of messages. While a user is connected to the chat, they are connected via a Bluetooth mesh to all other devices in the chat. Each time a user sends a message, that message is communicated to all other devices on that mesh. Each device’s ledger of events (temporary data) is updated with the new message. Once a chat is left the connection loop is disabled and their ledger is not longer updated.

# 4. System Architecture 
## 4.1 Top Level Diagram 

