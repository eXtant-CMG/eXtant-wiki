---
layout: default
title: Deletions
parent: The tags
grand_parent: Encoding manual
nav_order: 2
---

# Deletions `<del>` #

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
All the attributes listed below are **obligatory** when using `<del>` elements.

| Attribute        | Value          | Description |
|:-------------|:------------------|:------|
| `@seq`           | `seq="yyyymmddhhminminsecsec"` | The `@seq` attribute gives the value of the timestamp of the modification in the text  |
| `@type` |    | The `@type` attribute indicates the type of the addition  |
|            | `type="pre-context"`      | Indicates a deletion that was made _before_ the sentence was finished   |
|            | `type="context"`      | Indicates a deletion that was made after the sentence was finished   |
|            | `type="typo"`      | Indicates that the deletion was triggered by a typo   |
|            | `type="translocation"`      | Indicates that the deletion was part of a relocation of the text segment   |
|            | `type="previousType|continue"`      | Indicates that the deletion was interrupted by an immediate revision, without changing the cursor location, and is now continued   |
| `@evidence`          | `evidence="###"` | The `@evidence` attribute gives the value of the #id in the General Analysis of Inputlog  |

## `@seq` ##
The value of the `@seq` attribute should be the time indication of when the writing action was made. A good option is to take the time given in the [General Analysis](example/#Example%General%Analysis) in the 'Event StartClock'-column, in the format `hhmmss`. 
{: .warning }
You need to remove the colon's from the time, otherwise the TEI-XML encoding will not be valid!

- When encoding single-session writing processes, you can use just the time for the 'Event StartClock'. 
- When encoding multi-session writing processes, however, you can opt to encode the date of the writing session as well, in the format `yyyymmddhhmmss` (see Example 1).

Note that is it important that the value of the `@seq` attribute allows for listing the writing actions chronologically. When multiple writing actions are made at the same time, the order of the actions is determined by the order in which they appear in the XML tree. If another order is preferred, then change the time by adding one second to the writing action that should appear later. 



## `@type` ##
There are X different addition types.
#### New text ####
`<add type="nt">`: The use of a keystroke logger allows for an exact reconstruction of the textual development. This includes the moment a new sentence is produced. Therefore, the production of new sentences can also be incorporated in the encoding (`@type="nt"`), to be able to differentiate between “new” and “old” sentences, and to see when and where in the text new text was being produced.  
Every sentence that has not been written in the text before, is to be regarded as new text.  
In Example 1, the writer wrote the first sentence "The desktop: a wallpaper of a painting by Georgia O'Ke" after which she made a typo. The first part of this writing action is encoded with the `@type="nt"` (see Example 1).

##### Example 1 #####
{: .highlight}
	<seg><add seq="20230526081925" type="nt" evidence="16-75">The desktop: a wallpaper of a painting by Georgia O'Ke<del seq="20230526081948" type="typo" evidence="76-77">ff</del></add><add seq="20230526081948" type="nt|continue" evidence="78-82">effe.</add></seg>

After the immediate correction of the typo (deleting the 'ff'), the new text production is continued. Since the cursor was not relocated, the continuation of the text production is encoded with `<add type="nt|continue">`

#### Typo related addition ####
`<add type="typo">`: A large number of revisions in digital writing occur as a result of typographical errors. Within the scope of genetic criticism, such “typos” are not the most meaningful entities because they do not immediately affect the meaning of the text. Yet, the revision of typographical errors can also break the flow in writing and therefore influence the writing process. In order to be able to distinghuish between revisions and typos, every typo is encoded with `@type="typo"`.[^1]  
There are two ways typos can be corrected: 
1. immediately using the backspace-key: in this case, only a typo-related deletion occurs, after which the author continues writing. 
2. at a later moment: in this case, both a deletion and an addition occur. The deletion of the wronlgy typed character and the addition of the correct one (see ).

There are thus two types of __typo related deletions__, but they are encoded in the same way.

##### Example 2 #####
{: .no_toc }
{: .highlight}
	<seg><add seq="20230526082627" type="nt" evidence="922-931"><del seq="20230526082633" type="typo" evidence="935">h</del><add seq="20230526082633" type="typo" evidence="937">H</add>e says: </add>

#### Pre-contextual deletion ####
##### Example  #####
{: .highlight}
	<seg><add seq="20230526082028" type="pre-context" evidence="185-197">Finder, Cal<del seq="20230526082033" type="typo" evidence="198">a</del></add><add seq="20230526082033" type="pre-context|continue" evidence="199-235">endar, Safari, Microsoft Oulook, </add><add seq="20230526082014" type="nt" evidence="153-177">Microsoft Word, Notion, </add><mod seq="20230529082051" type="continue" evidence="240-250">Scrivener, <del seq="20230526082058" type="typo" evidence="255-257">ado</del></mod><mod seq="20230526082059" type="continue|continue" evidence="259-311">Adobe Acrobat Reader, the Downloads folder, Bin.</mod></seg>

#### Contextual deletion ####
##### Example  #####
{: .highlight}
	<seg><add seq="20230526082146" type="nt" evidence="342-377">The Print Layout, <add seq="20230526083451" type="context" evidence="1844-1848">just </add>imitating paper.</add></seg>

#### Translocation related deletion ####
`<add type="translocation">`: 
##### Example  #####
{: .no_toc }
{: .highlight}
	<seg><add seq="20230526083311" type="translocation" evidence="1636">CTRL+S.</add></seg>


## `@evidence` ##
The value of the `@evidence` attribute should (at least) be the number of the 'Event id' of first pressed key. 

----

[^1]: Typing errors can be hard to distinguish from spelling errors. In the encoding of the typing errors, I therefore used a list of criteria (developed by Stevenson, Schoonen, and Glopper 2006) for distinguishing typing revisions from spelling revisions. According to the checklist developed by Stevenson et al., a revision can be identified as a typing revision, if one or more of the following applies: “a. the pre-revision form does not conform to the orthographic rules of the language; b. the pre-revision form involves a letter string which does not conform to a likely pronunciation of the word; c. the semantic context indicates that the pre-revision form could not have been intended; d. the same word is written correctly at an earlier point in the text; e. a letter is replaced by an adjacent letter on the keyboard” (Stevenson, Schoonen, and Glopper 2006, 232).
