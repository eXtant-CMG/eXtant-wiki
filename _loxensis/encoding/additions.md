---
layout: default
title: Additions
parent: The tags
grand_parent: Encoding manual
nav_order: 1
---

# Additions `<add>` #
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## Attributes ##
The `<add>` element is used to encode different types of insertions: __textual__ additions to the digital document.  
There are three attributes that are **obligatory** when using `<add>` elements: `@seq`, `@type`, and `@evidence`.

| Attribute        | Value          | Description |
|:-------------|:------------------|:------|
| `@seq`           | `seq="yyyymmddhhminminsecsec"` | The `@seq` attribute gives the value of the timestamp of the modification in the text  |
| `@type` |    | The `@type` attribute indicates the type of the addition  |
|            | `type="nt"`      | Indicates new text production   |
|            | `type="pre-context"`      | Indicates an addition that was made _before_ the sentence was finished   |
|            | `type="context"`      | Indicates an addition that was made after the sentence was finished   |
|            | `type="typo"`      | Indicates that the addition was triggered by a typo   |
|            | `type="translocation"`      | Indicates that the addition was part of a relocation of the text segment   |
|            | `type="previousType|continue"`      | Indicates that the addition was interrupted by an immediate revision, without changing the cursor location, and is now continued   |
|            | `type="source"`      | Indicates that text was added by pasting directly from a digital source (e.g. website, other digital document)   |
| `@evidence`          | `evidence="###"` | The `@evidence` attribute gives the value of the #id in the General Analysis of Inputlog  |

The following attributes are **optional** when using `<add>` elements.  

| Attribute        | Value          | Description |
|:-------------|:------------------|:------|
| `@ana`           | `ana="#"` | The `@ana` attribute links to the related editor's note listed in `<p type="notes">` (see [Editor notes](editor%notes)) |

### `@seq` ###
The value of the `@seq` attribute should be the time indication of when the writing action was made. A good option is to take the time given in the [General Analysis](example/#Example%General%Analysis) in the 'Event StartClock'-column, in the format `hhmmss`. 

{: .warning }
You need to remove the colon's from the time, otherwise the TEI-XML encoding will not be valid!

- When encoding single-session writing processes, you can use just the time for the 'Event StartClock'. 
- When encoding multi-session writing processes, however, you can opt to encode the date of the writing session as well, in the format `yyyymmddhhmmss` (see Example 1).

Note that is it important that the value of the `@seq` attribute allows for listing the writing actions chronologically. When multiple writing actions are made at the same time, the order of the actions is determined by the order in which they appear in the XML tree. If another order is preferred, then change the time by adding one second to the writing action that should appear later. 



### `@type` ###
There are **6** different addition types: adding new text, typo related additions, pre-contextual additions, contextual additions, additions related to a translocation, and copied text from digital sources.  
#### New text ####
`<add type="nt">`: The use of a keystroke logger allows for an exact reconstruction of the textual development. This includes the moment a new sentence is produced. Therefore, the production of new sentences can be incorporated in the encoding (`@type="nt"`), to be able to differentiate between “new” and “old” sentences, and to see when and where in the text new text was being produced. Every sentence that has not been written in the text before, is to be regarded as new text.  

In Example 1, the writer wrote the first sentence "The desktop: a wallpaper of a painting by Georgia O'Ke" after which she made a typo. The first part of this writing action is encoded with the `@type="nt"`.

##### Example 1 #####
{: .no_toc }  

{: .example }
> <div markdown="block">
`<add seq="20230526081925" type="nt" evidence="16-75">The desktop: a wallpaper of a painting by Georgia O'Ke<del seq="20230526081948" type="typo" evidence="76-77">ff</del></add><add seq="20230526081948" type="nt|continue" evidence="78-82">effe.</add>`
> </div>


After the immediate correction of the typo (deleting the 'ff'), the new text production is continued. Since the cursor was not relocated, the continuation of the text production is encoded with `<add type="nt|continue">`. In this way, the writing action itself will not be counted as another newly produced sentence. 

#### Typo related addition ####
`<add type="typo">`: A large number of revisions in digital writing occur as a result of typographical errors. Within the scope of genetic criticism, such “typos” are not the most meaningful entities because they do not immediately affect the meaning of the text. Yet, the revision of typographical errors can also break the flow in writing and therefore influence the writing process. In order to be able to distinguish between revisions and typos, every typo is encoded with `@type="typo"`.[^2]  
There are two ways typos can be corrected: 
1. immediately using the backspace-key: in this case, only a typo-related deletion occurs, after which the author continues writing (as the typo in Example 1, see also [Deletions](../deletions)). 
2. at a later moment: in this case, both a deletion and an addition occur. The deletion of the wronlgy typed character and the addition of the correct one. This is when the `<add type="typo">`is used.

In Example 2, the writer first wrote "he says: ", but she of course wanted to start the sentence with a capital 'H'. She thus went back to the start of the sentence to first delete the 'h', and then type the 'H'. The typing of the 'H' is the typo related addition.
##### Example 2 #####
{: .no_toc }

{: .example }
> <div markdown="block">
`<add seq="20230526082627" type="nt" evidence="922-931"><del seq="20230526082633" type="typo" evidence="935">h</del><add seq="20230526082633" type="typo" evidence="937">H</add>e says: </add>`
> </div>

These typo related additions can occur before the sentence is completely finished, or can already be made as the sentence is still in production.

#### Pre-contextual addition ####
`<add type="pre-context">`: Pre-contextual additions occur during writing, specifically, before a sentence has been completed. Most pre-contextual __revisions__ are made as the writer decides that something needs to be adjusted in the moment of writing, and are therefore mostly represented as 'pre-contextual deletions' (See: [Deletions](../deletions)). In that case the writer immediately presses the backspace key to delete the just written text and then continues writing. The cursor is not relocated. As well as revising directly at the leading edge (the location in the text where new meaning is created), the writer can also perform a pre-contextual revision after relocating the cursor to a location earlier in the sentence in production, to make a revision before finishing the sentence at the end of the leading edge. In those cases, when an insertion is being made, it is a pre-contextual addition. 

In Example 3, the writer started with writing "Microsoft Word, Notion,", then she relocated her cursor to the start of the sentence to add another opening of the sentence: "Finder, Cala". Then she corrected the typo, and continued finishing the pre-contextual addition: "endar, Safari, Microsoft Outlook" (`<add type="pre-context|continue">`).

##### Example 3 #####
{: .no_toc }

{: .example }
> <div markdown="block">
`<add seq="20230526082028" type="pre-context" evidence="185-197">Finder, Cal<del seq="20230526082033" type="typo" evidence="198">a</del></add><add seq="20230526082033" type="pre-context|continue" evidence="199-235">endar, Safari, Microsoft Outlook, </add><add seq="20230526082014" type="nt" evidence="153-177">Microsoft Word, Notion, </add><mod seq="20230529082051" type="continue" evidence="240-250">Scrivener, <del seq="20230526082058" type="typo" evidence="255-257">ado</del></mod><mod seq="20230526082059" type="continue|continue" evidence="259-311">Adobe Acrobat Reader, the Downloads folder, Bin.</mod>`
> </div>

#### Contextual addition ####
`<add type="context">`: Contextual revisions, as opposed to pre-contextual revisions, are those revisions that are made in the text that has already been written. In the case of contextual additions, the writer relocates the cursor to insert text in already written text, or it is part of a substitution (contextual deletion and contextual addition). Contextual additions can take place at any point after writing the text in question, such as immediately after the production of the sentence, or at a later stage.

In Example 4, the writer had previously written the sentence "The Print Layout, imitating paper." Later, after the sentence had already been finished, she decided to add "just" to the sentence.
##### Example 4 #####
{: .no_toc }

{: .example }
> <div markdown="block">
`<seg><add seq="20230526082146" type="nt" evidence="342-377">The Print Layout, <add seq="20230526083451" type="context" evidence="1844-1848">just </add>imitating paper.</add></seg>`
> </div>

#### Translocation related addition ####
`<add type="translocation">`: Digital writing allows for easy relocating text elements, for example by using 'CTRL X' and 'CTRL V'. In the basis, the translocation is just a deletion of text in one location in the text, and adding it again at another location. To allow these movements of text to be included in the encoding, and differentiated from other revision types, the translocations are encoded using `@type="translocation"`, for both the deletion and the addition. 

In Example 5, the writer relocated the short sentence "CTRL+S."
##### Example 5 #####
{: .no_toc }

{: .example }
> <div markdown="block">
`<seg><add seq="20230526083311" type="translocation" evidence="1636">CTRL+S.</add></seg>`  
`<seg><add seq="20230526083218" type="nt" evidence="1501-1510">Do not <del seq="20230526083221" type="pre-context" evidence="1511-1513">to </del></add><add seq="20230526083222" type="nt|continue" evidence="1514-1537">forget to save the file.</add></seg>`  
`<seg><del seq="20230526083308" type="translocation" evidence="1628"><add seq="20230526083228" type="nt" evidence="1540-1548">CTRL+S.</add></del></seg>`
> </div>

#### Copied text from a digital source ####
`<add type="source">`: Since writers have access to the Internet and other digital sources during writing, they can also easily copy source material from these sources into their document. To account for these instances - to differentiate them from regular new text production - the copy-pasting from sources can be annotated using `<add type="source">`.  

In Example 6, the writer found a quote online which she could use in her text. She copied it directly from the website and pasted it into de Word docement. 
##### Example 6 #####
{: .no_toc }

{: .example }
> <div markdown="block">
`<add seq="20230526082703" type="source" evidence="971">Longhand isn't well suited to my way of writing. I tend to end up with dozens of pages of crossings-out and margin scribbles just to find one good paragraph, and it's easy to lose your train of thought, working like that.</add>`
> </div>

### `@evidence` ###
The value of the `@evidence` attribute should (at least) be the number of the 'Event id' of the first pressed key of the writing action. 

{: .warning }
The number in every `@evidence` needs the be **unique**, each encoded writing operation will be identified using this number.

----
[^1]: Typing errors can be hard to distinguish from spelling errors. In the encoding of the typing errors, I therefore used a list of criteria (developed by Stevenson, Schoonen, and Glopper 2006) for distinguishing typing revisions from spelling revisions. According to the checklist developed by Stevenson et al., a revision can be identified as a typing revision, if one or more of the following applies: “a. the pre-revision form does not conform to the orthographic rules of the language; b. the pre-revision form involves a letter string which does not conform to a likely pronunciation of the word; c. the semantic context indicates that the pre-revision form could not have been intended; d. the same word is written correctly at an earlier point in the text; e. a letter is replaced by an adjacent letter on the keyboard” (Stevenson, Schoonen, and Glopper 2006, 232).