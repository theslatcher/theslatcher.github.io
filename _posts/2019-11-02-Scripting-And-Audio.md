---
layout: post
title: Scripting, audio, and triggers
---

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
```

``` c++
void Class::RegisterMetaVariables()
{
	BindScriptFunction(myScriptUpdateFunction);
}
```

``` c++
void Class::RegisterMetaVariables()
{
	MetaTableRegistry::RegisterMetaClassFunction<JPlayerPawn>(FUNCTION_BINDING(JPlayerPawn, MainAttack));
}
```

``` c++
void Class::Update(float anElapsedTime)
{
	myScriptUpdateFunction.Call(anElapsedTime);
	//or:
	myScriptUpdateFunction(anElapsedTime);
}
```

``` lua
function Class:Update(elapsedTime)
	self:MainAttack()
end
```

---

``` c++
if (AudioCoreModule* audioCoreMan = AM_AppManager::GetInstance()->GetModule<AudioCoreModule>())
{
	AudioSound sound = audioCoreMan->CreateSound("MissionOver.wav");
	audioCoreMan->PlaySound(sound);
}
```

Unfinished.