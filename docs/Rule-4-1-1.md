# Rule 4.1.1

## Summary

## Business description

### Criterion

[4.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-4-1)

###Test

[4.1.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-4-1-1)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#mdia-temporel-type-son-vido-et-synchronis">m&eacute;dia temporel</a> pr&eacute;-enregistr&eacute; seulement audio, v&eacute;rifie-t-il, si n&eacute;cessaire, l'une de ces conditions (<a href="http://references.modernisation.gouv.fr/rgaa/cas-particuliers.html#cp-4-1,4-2,4-3,4-5,4-7,4-9,4-11,4-13" title="Cas particuliers pour le crit&egrave;re 4.1">hors cas particuliers</a>) ? 
 
 *  Il existe une <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#transcription-textuelle-media-temporel">transcription textuelle</a> accessible via un <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#lien-adjacent">lien adjacent</a> (une `url` ou une `ancre`) 
 *  Il existe une transcription textuelle adjacente clairement identifiable 

### Level

**A**

## Technical description

### Scope

**Page**

### Decision level

**Semi-Decidable**

## Algorithm

### Selection

#### Set1

All the elements `<audio>` tags (css selector : `audio`);

#### Set2

All the elements `<video>` tags (css selector : `video`) with `src` attribute that value has an audio extension (see note about audio extension)

#### Set3

All the elements `<object>` tags (css selector : `object`) with `data` attribute that value has an audio extension 

#### Set4

All the elements `<embed>` tags (css selector : `embed`) with `src` attribute that value has an audio extension 

#### Set5

All the elements `<bgsound>`, `<embed>` not in **Set4** and `<object>` not in **Set3** tags (css selector : `bgsound`, `embed`, `object`);

### Process

#### Tests

##### Test1

For each element of **Set1**, **Set2**, **Set3** and **Set4**, check if these brothers tags are not textual tags (see note about not textual tags), for a not semantics tag, see childs

For each element return true-result of **Test1**, raise MessageA

##### Test2

For each element return false-result of **Test1**, check if one of these brothers tags has a key expression (see note about key expression)

For each element return false-result of **Test2**, raise MessageB, raise MessageC instead

##### Test2

If **Set1**, **Set2**, **Set3** and **Set4** are empty and **Set5** is not empty, raise a MessageD

#### Messages

##### MessageA : Audio element without text transcription

-    code : **AudioElementWithoutTextTranscription** 
-    status: Failed
-    parameter : tag name, snippet
-    present in source : yes

##### MessageB : We detected audio element with a text transcription nearby check manually that relevant

-    code : **WeDetectedAudioElementWithTextTranscriptionNearbyCheckManually** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageC : We detected audio element, check manually the presence of a text transcription

-    code : **WeDetectedAudioElementCheckManuallyThePresenceOfTextTranscription** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageD : No audio element detected, check manually the presence of other audio element and its text transcription

-    code : **NoAudioElementDetectedCheckManuallyThePresenceOfOtherAudioElementAndItsTextTranscription** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

#### Rules remark

 * AudioElementWithoutTextTranscription (fr): &Eacute;l&eacute;ment audio sans transcription textuelle
 * AudioElementWithoutTextTranscription (en): Audio element without text transcription

 * WeDetectedAudioElementWithTextTranscriptionNearbyCheckManually (fr): Nous d&eacute;tectons des &eacute;l&eacute;ments audio avec une transcription textuelle à proximit&eacute;, v&eacute;rifier manuellement que cela est correct :
 * WeDetectedAudioElementWithTextTranscriptionNearbyCheckManually (en): We detected audio element with a text transcription nearby check manually that relevant

 * WeDetectedAudioElementCheckManuallyThePresenceOfTextTranscription (fr): Nous d&eacute;tectons des &eacute;l&eacute;ments audio, v&eacute;rifier manuellement la pr&eacute;sence d'une transcription textuelle
 * WeDetectedAudioElementCheckManuallyThePresenceOfTextTranscription (en): We detected audio element, check manually the presence of a text transcription

 * NoAudioElementDetectedCheckManuallyThePresenceOfOtherAudioElementAndItsTextTranscription (fr): Aucun &eacute;l&eacute;ment audio d&eacute;tect&eacute;, v&eacute;rifier manuellement la pr&eacute;sence d'autre &eacute;l&eacute;ments audio et de leur transcription textuelle
 * NoAudioElementDetectedCheckManuallyThePresenceOfOtherAudioElementAndItsTextTranscription (en): No audio element detected, check manually the presence of other audio element and its text transcription

### Accede Web guidelines

 * Rgaa32016-4-1-1-Accedeweb-HTML-13
 * Rgaa32016-4-1-1-Accedeweb-EDIT-8-3

### Analysis

#### Not Applicable

If no media element is present in the page (**Set1**, **Set2**, **Set3**, **Set4** and **Set5** are empty)

#### Failed

At least one audio element don't have a transcription near the element (At least one element return true-result of **test1**)

#### Pre-qualified

In all other cases

## Diagrammes

![](https://raw.githubusercontent.com/Tanaguru/RGAA3-2016/master/docs/Diagrammes/Test4-1-1.png?token=AI6sA-4TkbE-q6EoBy6YIFZlIeQeI181ks5Y-IDcwA%3D%3D)

## References

https://dev.w3.org/html5/spec-author-view/video.html

### Update

New test

## Notes

The textual tags : 
 - `<video>` ;
 - `<audio>` ;
 - `<embed>` ;
 - `<object>` ;
 - `<img>` ;
 - `<svg>` ;
 - `<canvas>` ;
 - `<source>` ; 
 - `<input>` ;
 - `<textarea>` ;
 - `<select>` ;

the following list of audio extension :
 - mp3 ;

This list must be implement with a file editable by the administrator

Complete this list if necessary.

