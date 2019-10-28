---
layout: post
title: Hit-, Hurtboxes, and death.
---

A small update today of something I've been working on: hit, and hurtboxes for a sprite frame in an animation. Every frame has the option to have a collision box(in case they want to overlap/block entities), and have lists of hitboxes, and hurtboxes. In the below image the green rectangle is a hurt box, blue the collision box, and red a hitbox for the current frame.

![animation_editor_pic]({{ site.baseurl }}/images/20191028/AnimationEditor.png "Animation Editor Picture")

And then a small gif with it in action with collision boxes renderer, where we kill the other entity in one strike:

![attack_animation_gif]({{ site.baseurl }}/images/20191028/AttackAnimation.gif "Attack Animation")

Looking pretty neat, doesn't it?

/Marcus