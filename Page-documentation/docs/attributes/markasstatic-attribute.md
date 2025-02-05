---
title: MarkAsStaticAttribute
---

## MarkAsStatic Attribute

<div class="facts text-secondary">
    <p>Namespace: <code>AutoMorph.Abstractions.Attributes</code></p> 
    <p>Inheritance: <a href="../inherited-attribute-members.html">IMarkAsStaticAttribute, IAttribute</a></p>
    <p>Attaches to: <code>Class, Struct</code></p>
    <p>Analyzer Errors: No Analyzer Errors.</p>
</div> <br />

### Overview
The `[MarkAsStatic]` attribute forces all generated mappers to be **extension methods** instead of instance or partial methods.

> [!NOTE]  
> This **disables** any partial methods marked with `[Include]`, meaning they **won't be generated** when this attribute is present.

> [!NOTE]  
> Static partial methods are **not yet supported**, but will be added in the future.

#### Class Definition
```csharp
public class MarkAsStaticAttribute : Attribute, IMarkAsStaticAttribute, IAttribute
```

#### Properties

| Property | Description |
| -------- | ----------- |
| `Key` | *Not supported yet for this attribute.* |

#### Example Usage

```csharp
using AutoMorph.Abstractions.Attributes;

namespace AutoMorph.Sample;

[Mapper] // Marks this class as a source type for mapping
[Include<TargetClass>(MapperType.Standard, MappingStrategy.Normal)] // Defines normal object-object mapping from the source -> target.
[MarkAsStatic] // Ensures generated mappers are static extension methods.
public class SourceClass 
{
    public string Name { get; set; }

    public int Age { get; set; }
}

public class TargetClass
{
    public string Name { get; set; }
    public int Age { get; set; }
}
```