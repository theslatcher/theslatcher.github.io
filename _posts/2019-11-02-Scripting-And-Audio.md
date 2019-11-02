---
layout: post
title: Scripting, audio, and triggers
---

Scripting

So, one of the things I've been working on scripting support using sol3 to use lua as the scripting language. To do the C++<->lua binding I'm utilizing my meta tables, which previously only supported variables, so I had to implement functions too.

You bind Lua functions to C++ like this:

.h
``` c++
ScriptFunction myScriptUpdateFunction;
```

.cpp
``` c++
Class::Class()
: myScriptUpdateFunction(this, "Update")
{
}

void Class::RegisterMetaVariables()
{
	BindScriptFunction(myScriptUpdateFunction);
}
```

And then to call the functions you simply do this:

``` c++
void Class::Update(float anElapsedTime)
{
	myScriptUpdateFunction.Call(anElapsedTime);
	//or:
	myScriptUpdateFunction(anElapsedTime);
}
```

Meanwhile you bind C++ functions to lua like this:

``` c++
void Class::RegisterMetaVariables()
{
	MetaTableRegistry::RegisterMetaClassFunction<Class>(FUNCTION_BINDING(Class, Function));
}
```

And in Lua the function will be under both Class, and self, so you simply do this:

``` lua
function Class:Update(elapsedTime)
	self:Function()
end
```

---

Audio

``` c++
if (AudioCoreModule* audioCoreMan = AM_AppManager::GetInstance()->GetModule<AudioCoreModule>())
{
	AudioSound sound = audioCoreMan->CreateSound("MissionOver.wav");
	audioCoreMan->PlaySound(sound);
}
```

---

Triggers, and level changing

---

Unfinished.