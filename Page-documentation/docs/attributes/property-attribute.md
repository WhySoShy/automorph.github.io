---
title: PropertyAttribute(string)
---

## Property Attribute

<div class="facts text-secondary">
    <p>Namespace: <code>AutoMorph.Abstractions.Attributes</code></p> 
    <p>Inheritance: <a href="../inherited-attribute-members.html">IPropertyAttribute, IAttribute</a></p>
    <p>Attaches to: <code>Properties</code></p>
    <p>Analyzer Rules: None.</p>
</div> <br />

### Overview
The `[Property]` attribute **remaps a property to a different target property name**.  
Instead of using the original property name, AutoMorph will use `nameOfTargetProperty` to find the corresponding property on the target type.

> [!TIP]
> Use `nameof(class.property)` instead of hardcoded strings to avoid errors and improve maintainability.

#### Class Definition
```csharp
public class PropertyAttribute(string nameOfTargetProperty) : Attribute, IAttribute, IPropertyAttribute
```

#### Properties

| Property | Description |
| -------- | ----------- |
| `Key`    | Used to bind to `Include` attribute. |

#### Parameters

| Parameter | Description |
| --------- | ----------- |
| `nameOfTargetProperty` | Specifies the target property name to map to, instead of using the attached property’s name. |

#### Example Usage

```csharp
using AutoMorph.Abstractions.Attributes;

namespace AutoMorph.Sample;

[Mapper] // Marks this class as a source type for mapping
[Include<TargetClass>(MapperType.Standard, MappingStrategy.Normal)] // Defines normal object-object mapping from the source -> target.
public class SourceClass 
{
    public string Name { get; set; }

    [Property(nameof(TargetClass.NewAge))] // This will map 'Age' to 'NewAge' in the target class.
    public int Age { get; set; }
}

public class TargetClass
{
    public string Name { get; set; }
    public int NewAge { get; set; }
}
```