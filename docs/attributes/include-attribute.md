---
title: IncludeAttribute<T>(MapperType, MappingStrategy)
---

## Include Attribute

<div class="facts text-secondary">
    <p>Namespace: <code>AutoMorph.Abstractions.Attributes</code></p> 
    <p>Inheritance: <a href="../inherited-attribute-members.html">IIncludeAttribute, IAttribute</a></p>
    <p>Attaches to: <code>Class, Struct, Record, Interface, Method</code></p>
    <p>Analyzer Errors: No Analyzer Errors.</p>
</div> <br />

#### Overview
Specifies the target type for mapping and defines how the mapper should be generated for the source type.

#### Class Definition
```csharp
public class IncludeAttribute<T>(MapperType type, MappingStrategy strategy) : Attribute, IIncludeAttribute, IAttribute
```

#### Attachable Types
When attached to different types, the attribute will act accordingly.

| Type | Behavior |
| ---- | -------- |
| `Class, Struct, Record` | Generates an **extension method** for mapping. <br /> • *If a partial method is used, the mapper is generated as a regular method inside the class.* |
| `Interface` | Generates a **generic mapper**, constrained to the source or target type depending on the [MapperStrategy](). |
| `Method` | Generates a **partial method** <br /> • *Both the type and method must be `partial`* <br /> *Read [Partial Mappers]()*|

#### Type Parameters

`T`
> The target type to map to.

#### Parameters

| Parameter | Type |
| --------- | ---- |
| `type`    | [MapperType]() |
| `strategy` | [MapperStrategy]() | 


#### Properties

| Property | Description |
| -------- | ----------- |
| `Key` | Used to bind additional attributes (`Exclude`, `Property`) to a specific mapping instance. |
| `IsGeneric` | Forces the mapper to be generated as a generic mapper, constrained based on [MapperStrategy](). |
| `MapperName` | Explicitly sets the generated mapper's name. <br /> • *If attached to a partial method, the method's name is used instead.* |

#### Example Usage

```csharp
using AutoMorph.Abstractions.Attributes;

namespace AutoMorph.Sample;

[Mapper] // Marks this class as a source type for mapping
[Include<TargetClass>(MapperType.Standard, MappingStrategy.Normal)] // Defines object-object mapping.
public class SourceClass 
{
    public string Name { get; set; }
}

public class TargetClass
{
    public string Name { get; set; }
}
```