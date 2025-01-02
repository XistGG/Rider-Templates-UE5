# Rider Templates for UE5

Source: https://github.com/XistGG/Rider-Templates-UE5

When Rider first starts up, it reads `{UE5_Root}/Engine/Content/Editor/Templates/*.template` to initialize the
template files to use for UE5.

If you change the templates after Rider creates its `.idea` cache,
for changes to the templates to take effect, you need to clear out Rider's cache.

You can either remove the entire `.idea` directory and relaunch Rider, or you can see
[this forum post](https://rider-support.jetbrains.com/hc/en-us/community/posts/360010619699/comments/4410277434258)
for more details on how to clear only the template cache without losing other project settings.
*(Personally I just nuke `.idea`, there isn't anything very important there IMO).*

## Example Output

- {   [h](#actor-header)
  | [cpp](#actor-source)           } **Actor**
- {   [h](#actor-component-header)
  | [cpp](#actor-component-source) } **Actor Component**
- {   [h](#interface-header)
  | [cpp](#interface-source)       } **Interface**
- {   [h](#object-header)
  | [cpp](#object-source)          } **Object**

# Using this repo

To use this repo, after checking out the engine, and after downloading all of its content, replace the
`Engine/Content/Editor/Templates` directory with this repository.

As you change branches on the editor and re-download content for other branches, it may be necessary
to overwrite the changes with this repository multiple times.

Note however that Rider only looks ONCE for these files, then caches their values, so it should not technically
be required to constantly update this.

# Perforce Cheat Sheet

If you use Perforce, you can overwrite your existing Engine Templates like this:

```powershell
# Replace this with the location of this cloned repository:
$SourceDir = "D:/GitHub/Rider-Templates-UE5"

# Replace this with the location of your Engine dir:
$EngineTemplatesDir = "E:/UE_5.3/Engine/Content/Editor/Templates"

cd $EngineTemplatesDir

# Copy all *.template files from $SourceDir into the current dir ($EngineTemplatesDir)
Get-ChildItem -Path "$SourceDir" -Include "*.template" -Recurse `
	| %{ `
		p4 edit $_.Name; `
		cp $_.FullName $_.Name `
	}
```

# Sample Output

The Copyright and the `MY_API` would be replaced by your own project-specific settings.

## Actor

Creating a `MyActor` Actor will result in source like this:

- [Actor Header](#actor-header)
- [Actor Source](#actor-source)

### Actor Header

```c++
// Your copyright notice here

#pragma once

#include "GameFramework/Actor.h"
#include "MyActor.generated.h"

/**
 * MyActor
 */
UCLASS()
class MY_API AMyActor : public AActor
{
	GENERATED_BODY()

public:
	// Set Class Defaults
	AMyActor(const FObjectInitializer& ObjectInitializer = FObjectInitializer::Get());
};
```

### Actor Source

```c++
// Your copyright notice here

#include "MyActor.h"

// Set Class Defaults
AMyActor::AMyActor(const FObjectInitializer& ObjectInitializer)
	: Super(ObjectInitializer)
{
	// For performance reasons, don't tick actors unless you really need to
	PrimaryActorTick.bCanEverTick = false;
	PrimaryActorTick.bStartWithTickEnabled = false;
}
```

## Actor Component

Creating a `MyComponent` Actor Component will result in source like this:

- [Actor Component Header](#actor-component-header)
- [Actor Component Source](#actor-component-source)

### Actor Component Header

```c++
// Your copyright notice here

#pragma once

#include "Components/ActorComponent.h"
#include "MyComponent.generated.h"

/**
 * MyComponent
 */
UCLASS(meta=(BlueprintSpawnableComponent))
class MY_API UMyComponent : public UActorComponent
{
	GENERATED_BODY()

public:
	// Set Class Defaults
	UMyComponent(const FObjectInitializer& ObjectInitializer = FObjectInitializer::Get());
};
```

### Actor Component Source

```c++
// Your copyright notice here

#include "MyComponent.h"

// Set Class Defaults
UMyComponent::UMyComponent(const FObjectInitializer& ObjectInitializer)
	: Super(ObjectInitializer)
{
	// For performance reasons, don't tick components unless you really need to
	PrimaryComponentTick.bCanEverTick = false;
	PrimaryComponentTick.bStartWithTickEnabled = false;
}
```

## Interface

Creating a `MyInterface` Interface will result in source like this:

- [Interface Header](#interface-header)
- [Interface Source](#interface-source)

### Interface Header

```c++
// Your copyright notice here

#pragma once

#include "UObject/Interface.h"
#include "MyInterface.generated.h"

// This class does not need to be modified.
UINTERFACE()
class UMyInterface : public UInterface
{
	GENERATED_BODY()
};

/**
 * MyInterface Interface
 */
class MY_API IMyInterface
{
	GENERATED_BODY()

public:
	// Add public interface methods here
};
```

### Interface Source

```c++
// Your copyright notice here

#include "MyInterface.h"

// Add default functionality here for any IMyInterface functions that are not pure virtual.
```

## Object

Creating a `MyObject` Object will result in source like this:

- [Object Header](#object-header)
- [Object Source](#object-source)

### Object Header

```c++
// Your copyright notice here

#pragma once

#include "UObject/Object.h"
#include "MyObject.generated.h"

/**
 * MyObject
 */
UCLASS()
class MY_API UMyObject : public UObject
{
	GENERATED_BODY()

public:
	// Set Class Defaults
	UMyObject(const FObjectInitializer& ObjectInitializer = FObjectInitializer::Get());
};
```

### Object Source

```c++
// Your copyright notice here

#include "MyObject.h"

// Set Class Defaults
UMyObject::UMyObject(const FObjectInitializer& ObjectInitializer)
	: Super(ObjectInitializer)
{
}
```
