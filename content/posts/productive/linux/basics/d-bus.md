---
title: "d-bus"
draft: false
---

# D-Bus (Desktop Bus)

At its core, d-bus is message bus system, a simple way to applications to communicate with each other. It is the standard **Inter-Process Communication (IPC)** mechnism used in linux and unix based systems. 

### Why do we need D-Bus.

Before D-Bus, if a music player wanted to pause when you receive VoIP call, the developers of the music player and VoIP app would have to agree on a specific, custom way to talk with each other. This way messy and unscaleable.

- D-Bus solves this by providing standardized channel.

#### The architecture.

D-Bus is three layer system.

1. **libdbus** : A library that allows two application to connect with each other and share messages.
2. **dbus-daemon** : An executable (background process) build on top of `libdbus`. It acts as a traffic router, passing messages from one processes to another.
3. **Wrapper libraries** :  High level libraries (like GDBus for GNOME/GTK or QTDBus for KDE/QT) that make using d-bus easier for programmers.

### The Two Buses

In typical linux setup, there isn't just one bus running around, but usually two distinct types running simultaneously.


#### 1. The system bus

Runs at the OS level. There is usually one System bus per computer dedicated to system-wide events and hardware abstraction.

Examples, 

- NetworkManager : Tells the system when you are connected to WiFi.
- Udev : Notify other apps, when new hardware are connected to your device.
- Systemd : Uses it to manage system and shut-down the system.


### 2. The Session Bus

Runs at the user level. Ther is one session Bus for user *logged* in, dedicated to desktop applications and user-specific data.

Examples,

- Clipboard : Mangaing copy/paste between apps.
- Notifications : An app sending "Task Completed" toaster popup.
- Media Players: MPRIS uses D-Bus so your keyboard "play/pause" buttons work on spotify,VLC or youtube.

