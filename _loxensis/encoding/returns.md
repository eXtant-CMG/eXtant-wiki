---
layout: default
title: Returns to leading edge
parent: The tags
grand_parent: Encoding manual
nav_order: 3
---

# Returns to the leading edge `<mod>` #

When to use the `<del>` element?

{: .no_toc }
When to use the `<add>`?  

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## Attributes ##
| Attribute        | Value          | Description |
|:-------------|:------------------|:------|
| `@seq`           | `seq="yyyymmddhhminminsecsec"` | The `@seq` attribute gives the value of the timestamp of the modification in the text  |
| `@type` |    | The `@type` attribute indicates the type of the modification  |
|            | `type="continue"`      | Indicates the return to the leading edge of the sentence   |
|            | `type="continue|continue"`      | Indicates that the continuation was interrupted by an immediate revision, without changing the cursor location, and is now continued   |
| `@evidence`          | `evidence="###"` | The `@evidence` attribute gives the value of the #id in the General Analysis of Inputlog  |


It occurs that sentences are not finished before modifications are performed elsewhere in the text. This can be described as ‘returns to the leading edge’. In the definition formulated by Lindgren et al. (2019)[^1], the leading edge is located “typically at the end of the text produced so far, but can also occur at the end of insertions within previously written text where a writer inserts new ideas (not only revises form)” (347). When the author returns to the sentence to finish it and starts to create new meaning there after a modification elsewhere in the text, this finishing of the sentence would not be an addition. Therefore, to distinguish these returns to the leading edge from ‘regular’ additions, these actions are classified with `<mod type="continue">`.  
In Example X, we already 

##### Example  #####
{: .no_toc }
{: .highlight}
	<seg><add seq="20230526083033" type="nt" evidence="1277-1293">My handwriting is </add><mod seq="20230526083139" type="continue" evidence="1362-1371">terrible.</mod></seg>

	<seg><add seq="20230526082028" type="pre-context" evidence="185-197">Finder, Cal<del seq="20230526082033" type="typo" evidence="198">a</del></add><add seq="20230526082033" type="pre-context|continue" evidence="199-235">endar, Safari, Microsoft Oulook, </add><add seq="20230526082014" type="nt" evidence="153-177">Microsoft Word, Notion, </add><mod seq="20230529082051" type="continue" evidence="240-250">Scrivener, <del seq="20230526082058" type="typo" evidence="255-257">ado</del></mod><mod seq="20230526082059" type="continue|continue" evidence="259-311">Adobe Acrobat Reader, the Downloads folder, Bin.</mod></seg>

----
[^1]:[Lindgren, Eva, Asbjørg Westum, Hanna Outakoski, and Kirk P.H. Sullivan. 2019. ‘Revising at the Leading Edge: Shaping Ideas or Clearing up Noise’. In Observing Writing, edited by Eva Lindgren and Kirk P.H. Sullivan, 346–65. Leiden: Brill.](https://doi.org/10.1163/9789004392526_017)