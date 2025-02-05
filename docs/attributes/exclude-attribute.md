---
title: ExcludeAttribute
---
## Exclude Attribute

<div class="facts text-secondary">
    <p>Namespace: <code>AutoMorph.Abstractions.Attributes</code></p> 
    <p>Inheritance: <a href="../inherited-attribute-members.html">IExclude, IAttribute</a></p>
    <p>Attaches to: <code>Properties</code></p>
    <p>Analyzer Errors: No Analyzer Errors.</p>
</div> <br />

#### Overview
The `[Exclude]` attribute prevents a property from being mapped. <br />
It can exclude a property from **one or multiple mappers** based on the specified `Key`.

#### Class Definition
```csharp
public class ExcludeAttribute : Attribute, IExcludeAttribute, IAttribute
```

#### Properties

| Property | Description |
| -------- | ----------- |
| `Key` | Specifies which `[Include]` mappings the `[Exclude]` attribute applies to. <br /> • *If no key is set or the provided key doesn't match any `[Include]`, the exclusion applies to all mappings of this type.* |

#### Example Usage

```csharp
using AutoMorph.Abstractions.Attributes;

namespace AutoMorph.Sample;

[Mapper] // Marks this class as a source type for mapping
[Include<TargetClass>(MapperType.Standard, MappingStrategy.Normal)] // Defines normal object-object mapping from the source -> target.
public class SourceClass 
{
    public string Name { get; set; }

    [Exclude] // This property will NOT be included in any generated mappers.
    public int Age { get; set; }
}

public class TargetClass
{
    public string Name { get; set; }
    public int Age { get; set; } // This will NOT receive any mapped values.
}
```