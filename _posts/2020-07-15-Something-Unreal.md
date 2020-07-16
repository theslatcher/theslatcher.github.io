---
layout: post
title: Something Unreal
---

Long time no see since the last update, while I've been working on some minor, engine related, things on Janus, I've started another project that's using Unreal Engine 4, which is a monster raising simulator akin to "Digimon World" where you have a companion monster which you travel alongside, use to battle various monsters, and evolves into more powerful types depending on a multitude of factors.

Currently what I have is traveling between levels, a companion following the player, an enemy monster sitting patiently still until the player is in range, and combat initializing between your companion and an enemy monster once the latter has touched the player. The combat is making use of Gameplay Abilities through a standard Behavior Tree, a basic concept of it can be seen here:

{% youtube sN-Q3neZWOw %}