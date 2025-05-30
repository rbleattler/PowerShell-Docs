---
description: How to add notes to a cmdlet help topic
ms.date: 07/10/2023
title: How to add notes to a cmdlet help topic
---
# How to add notes to a cmdlet help topic

[!INCLUDE [use-platyps](../../../includes/use-platyps.md)]

This section describes how to add a **NOTES** section to a PowerShell cmdlet Help topic. The
**NOTES** section is used to explain details that don't fit easily into the other structured
sections, such as a more detailed explanation of a parameter. This content could include comments on
how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or
ways to avoid possible error conditions.

The **NOTES** section is defined using a single `<maml:alertset>` node. There are no limits to the
number of notes that you can add to a Notes section. For each note, add a pair of `<maml:alert>`
tags to the `<maml:alertset>` node. The content of each note is added within a set of `<maml:para>`
tags. Use blank `<maml:para>` tags for spacing.

```xml
<maml:alertSet>
  <maml:title>Optional title for Note</maml:title>
  <maml:alert>
    <maml:para>Note 1</maml:para>
    <maml:para>Note a</maml:para>
  </maml:alert>
  <maml:alert>
    <maml:para>Note 2</maml:para>
  </maml:alert>
</maml:alertSet>
```
