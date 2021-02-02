# faust-xml
XML and other source data of the Faustedition

This repo contains the complete XML source data of the Faustedition.

* TEI transcriptions of manuscripts are in `xml/transcript`
* TEI transcriptions of printed editions are in `xml/print`
* non-TEI manuscript descriptions are in `xml/document`

## Manuscript Descriptions

All files somewhere below `xml/document` contain manuscript descriptions in a proprietary XML format, the corresponding XML schema can be found [in the faustedition/faust-schema project](https://github.com/faustedition/faust-schema/blob/master/src/main/xsd/metadata.xsd). The files below `xml/document/print` describe the prints, in a compatible but adapted format.

The element `<idno type="faustedition">` in each file contains the sigil that is used throughout the edition.
These metadata files also serve as an index into the transcripts folder: The XPath expressions `//f:textTranscript/@uri` and `//f:docTranscript/@uri` produce URIs that, when resolved, point to the respective textual and documentary transcripts. Resolving using the usual `xml:base` mechanism will produce an URI like `faust://xml/transcript/gsa/390028/390028.xml`, replace `faust://xml` with the path to this repository’s `xml` subfolder to find the corresponding XML document. 

## TEI transcriptions

Each _manuscript_ has been transcribed twice: There is one file with a textual transcription of the whole document’s _Faust_ text, and additionaly one file per _page_ with relevant content with a documentary transcription. The transcriptions follow the TEI schema described by the ODD file [in the faustedition/faust-schema project](https://github.com/faustedition/faust-schema/blob/master/src/main/odd/faust-tei.xml). The generated Relax NG schema file is available from <http://faustedition.net/schema/1.0/>. For _prints_ there is only a textual transcription. 

Each transcript file contains a limited TEI header which contains its sigil (as used throughout the edition) in the `<idno type="faustedition">` element.

The easiest way to find the transcriptions for a specific document is to navigate to the corresponding document or page [in the edition](http://faustedition.net/) and to use the download button to get a link to the transcription on Github. All transcriptions belonging to one document always share a folder, e.g., [`xml/transcript/gsa/391098`](https://github.com/faustedition/faust-xml/tree/1.2-RC/xml/transcript/gsa/391098) contains all transcriptions for _2 H_, the textual transcript in a file named like the folder (`391098.xml`) and the documentary transcriptions in the other files.

## Edited Text

Please note that the edited text’s TEI source is _not_ in this repository since it is generated from source and apparatus files. The final TEI including the critical apparatus can be found at <http://faustedition.net/downloads/faust.xml>, the transformation scripts and apparatus source is in the [faust-gen-html](https://github.com/faustedition/faust-gen-html) project.
