---
title: What is AutoMorph
---

> [!CAUTION]
> AutoMorph is still in early beta. Expect breaking changes and limited features.

## What is AutoMorph?

**AutoMorph** is a [.NET Incremental Source Generator](https://github.com/dotnet/roslyn/blob/main/docs/features/incremental-generators.md) that automatically generates object mappers using **attributes**. Instead of manually writing boilerplate mapping code, simply annotate your types, and AutoMorph will generate optimized conversion methods at **compile time**.

### Why?
Many object-mapping generators exist, but I wanted to build one that I could fully design and control. Creating AutoMorph has been a learning experience—this is my second time developing a source generator, but my first time publishing one with complete documentation.

### Get started
Ready to start using AutoMorph? Head over to [Installation](installation.md) to begin your journey!

### Contribution
> [!WARNING]
> AutoMorph doesn't take Contributions yet.

AutoMorph’s mapper generation is primarily **StringBuilder-based**, reducing reliance on Roslyn’s `SyntaxFactory` for code generation.
However, a basic understanding of **Roslyn’s APIs** is still required for working with **symbol analysis** and **syntax trees**.

When contributions do open up, the focus will be on **extending and improving the existing token system** and **refining the generator logic**, rather than deeply interacting with Roslyn’s AST.

> `Create how to make contribution`

### End Goal
The ultimate goal of AutoMorph is the **learning experience** gained from creating and contributing to the project.