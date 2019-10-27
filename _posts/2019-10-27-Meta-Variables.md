---
layout: post
title: Meta Variables, Json, & Animations.
---

So, I've been working on Meta Variables to stop needing to create, & maintain CopyTo, & Serialize functions in classes all the time. The way it works is when defining an object it registers itself into the MetaTableRegistry, and then if the object has a RegisterMetaVariables() function, it is called to register its variables like so:

``` c++
void JSceneComponent::RegisterMetaVariables()
{
	MetaTableRegistry::RegisterMetaClassMember<JSceneComponent>(DATA_BINDING(JSceneComponent, myRelativeTransform));
	MetaTableRegistry::RegisterMetaClassMember<JSceneComponent>(DATA_BINDING(JSceneComponent, myAttachedParentIdx), JMetaVariableFlags::MVF_HideInEditor);
	MetaTableRegistry::RegisterMetaClassMember<JSceneComponent>(DATA_BINDING(JSceneComponent, myIsLocationAbsolute));
	MetaTableRegistry::RegisterMetaClassMember<JSceneComponent>(DATA_BINDING(JSceneComponent, myIsRotationAbsolute));
	MetaTableRegistry::RegisterMetaClassMember<JSceneComponent>(DATA_BINDING(JSceneComponent, myIsScaleAbsolute));
	MetaTableRegistry::RegisterMetaClassMember<JSceneComponent>(DATA_BINDING(JSceneComponent, myScale));
}
```

The meta variable data we keep is a pointer-to-member(char JObject::\*) to access the variable, its name, type info(class, type, if it's templated, etc.), memory offset, and size. Here the entity editor is using it for an entities' components:

![entity_editor_pic]({{ site.baseurl }}/images/20191027/EntityEditor.png "Entity Editor Picture")

I also implemented Json serialization to stop needing to version control my asset files when a variable we need to serialize is added to a class.

---

Another thing I've worked on is an Animation State Machine, which works like every other ASM: we have an entry state, and transitions between states dependant on the rules the transition has set(if we're in the falling state, you can transition to for example the walking state if we are on the ground). Next step when it comes to animations is implementing custom collision bodies(starting with only boxes) for our general collision, hitboxes, and hurtboxes. Here's the ASM in action with collision boxes rendering on([Using the Adventurer spritesheet by rvros over at itch.io](https://rvros.itch.io/animated-pixel-hero)):

![asm_pic]({{ site.baseurl }}/images/20191027/AnimationStateMachine.gif "Animation State Machine Gif")

The gif is a little stuttery, on my local computer it isn't, so must be github pages compressing it? Might need to check that out for future gifs.

And that's it for significant updates, bye for now!
/Marcus