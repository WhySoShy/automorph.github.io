---
title: MapperAttribute
---

## Mapper Attribute

<div class="facts text-secondary">
    <p>Namespace: <code>AutoMorph.Abstractions.Attributes</code></p> 
    <p>Inheritance: <a href="../inherited-attribute-members.html">IMapperAttribute</a></p>
    <p>Analyzer Errors: No Analyzer Errors.</p>
</div> <br />

#### Overview
The `[Mapper]` attribute marks a type as a source for AutoMorph’s mapping system.  
However, it <u>does not generate a mapper</u> unless paired with the atleast one [`Include`](/attributes/include-attribute.md) attribute, which specifies the mapping target.

#### Class Definition
```csharp
public class MapperAttribute : Attribute, IMapperAttribute
```

#### Properties

| Property | Description |
| -------- | ----------- |
| `DefaultMapperName` | Sets a default mapper name for all mappers defined with the [Include Attribute](include-attribute.md). <br /> ***This can be overriden if:*** <br /> • The declared mapper is a **partial mapper**. <br /> • A specific name is explitcly defined in [Include Attribute](include-attribute.md).|

### Valid Source Types
> The behavior of the source types changes depending on what source they are attached to.

| Source Type | Behavior |
| ----------- | -------- |
| `Class, Struct, Record` | Generates all specified mappers based on **MapperType** <br /> ***This can be overriden if:*** <br /> • The mapper is explicitly defined in [Include Attribute](include-attribute.md). |
| `Abstract Types` *(Interfaces, Abstract Classes)* | Generates **generic mappers** constrainted to the source type. |

#### Example Usage

```csharp
using AutoMorph.Abstractions.Attributes;

namespace AutoMorph.Sample;

[Mapper] // Marks this class as a source type for mapping
public class SourceClass 
{
    public string Name { get; set; }
}
```