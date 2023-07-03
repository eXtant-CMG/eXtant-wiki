---
layout: default
title: The tags
parent: Encoding manual
permalink: /loxensis/encoding/the-tags
has_children: true
nav_order: 2
---
# The tags #
{: .no_toc }
For encoding the keystroke logging data, only a limited number of tags from the [TEI Guidelines](https://tei-c.org) are needed. If started from the '[Start file'](start-file) only the following elements are needed:


| Syntax      | Description |
| ----------- | ----------- |
| `<p>`     | All the text is encoded in one single `<p>` element(`<p source="keystroke"`) ,  all the 'Focus events' in another `<p>` element  (`<p source="sources"`), and all editor notes (annotations) in a separate `<p source="notes">` element.     |
| `<seg>`   | Every sentence is encoded with a `<seg>` element       |
| `<lb/>`   | Every 'Enter/Return' is encoded with the empty element `<lb/>` element       |
| `<add>`   | Every addition, including new text production, is encoded with a `<add>` element       |
| `<del>`   | Every deletion is encoded with a `<del>` element       |
| `<mod>`   | During the production of a sentence the author can decide to leave the sentence produced so far to make a revision elsewhere after which they return to the end of the sentence they were writing, this return to the unfinished sentence is encoded in `<mod>` elements      |
| `<media>`   | The `<media>` element is used to encode the 'Focus events', in order to include them in the sequentiality of the visualisations, they are encoded inside an `<add>` element. For sources, the `<add>` element is specified with the attribute `@type="focus"`       |
| `<desc>`   | The `<media>` element requires the `<desc>` element (nested in `<media>`) for the further description of the visited digital source       |
| `<title>`   | The `<title>` element is used to encode the title of the text, if any.   |
| `<emph>`   | The `<emph>` element (emphasized) is used to mark words or phrases which are stressed or emphasized for linguistic or rhetorical effect, it is specificed using the `@rend` attribute   |
| `<note>`   | The `<note>` element is used to encode editor notes, with the attribute `@corresp` to link it to the corresponding writing action  |

At the most basic level, digital writing only requires two writing operations: insertions and deletions. When text is typed in the word processor, the text is inserted (added); when the text is deleted using the backspace- or delete key character per character, or by selecting the to-be-deleted text and deleting it, the text is deleted. Yet, multiple types of these writing actions can be distinguished. This encoding manual builds upon the taxonomy by Lindgren and Sullivan (2006), which distinguishes between ‘pre-contextual’ revisions (“revisions made before an externalised context is completed”) and ‘contextual’ revisions (“revisions made within a completed externalised context”; see Lindgren 2006, 159), and applies these types of revisions to the writing of a sentence. As such, contextual revisions indicate revisions made in a previously written sentence, and pre-contextual revisions, by contrast, indicate revisions made before a sentence is completed. By using these two revision types, the editorial interpretation remains as limited as possible. These revision types, and the other writing actions that can be encoded, will be detailed in the following sections.
