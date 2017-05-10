# Rule 4.1.3

## Summary

## Business description

### Criterion

[4.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-4-1)

###Test

[4.1.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-4-1-3)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#mdia-temporel-type-son-vido-et-synchronis">m&eacute;dia temporel</a> synchronis&eacute; pr&eacute;-enregistr&eacute; v&eacute;rifie-t-il, si n&eacute;cessaire, une de ces conditions (<a href="http://references.modernisation.gouv.fr/rgaa/cas-particuliers.html#cp-4-1,4-2,4-3,4-5,4-7,4-9,4-11,4-13" title="Cas particuliers pour le crit&egrave;re 4.1">hors cas particuliers</a>) ? 
 
 *  Il existe une <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#transcription-textuelle-media-temporel">transcription textuelle</a> accessible via un <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#lien-adjacent">lien adjacent</a> (une `url` ou une `ancre`) 
 *  Il existe une transcription textuelle adjacente clairement identifiable 
 *  Il existe une <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#audiodescription-synchronise-media-temporel">audio-description</a> synchronis&eacute;e 
 *  Il existe une version alternative avec une audio-description synchronis&eacute;e accessible via un lien adjacent (une `url` ou une `ancre`) 

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

All the elements `<video>` tags (css selector : `video`) with `src` attribute that value has video extention and no audio extension (see note about audio extension);

#### Set2

All the elements `<object>` tags (css selector : `object`) with `data` attribute that value has video extention and no audio extension 

#### Set3

All the elements `<embed>` tags (css selector : `embed`) with `src` attribute that value has video extention and no audio extension 

#### Set4

All the elements `<embed>` not in **Set3** and not with an audio source, `<object>` not in **Set2** tags and not with an audio source and `<svg>` and `<canvas>` tags (css selector : `embed`, `object`, `svg`, `canvas`);

### Process

#### Tests

##### Test1

For each element of **Set1**, **Set2** or **Set3**, check if these brothers tags are not textual tags (see note about not textual tags), for a not semantics tag, see childs

For each element return true-result of **Test1**, raise MessageA

##### Test2

For each element return false-result of **Test1**, check if one of these brothers tags has a key expression (see note about key expression)

For each element return false-result of **Test2**, raise MessageB, raise MessageC instead

##### Test3

If **Set1**, **Set2** and **Set3** are empty and **Set4** is not empty, raise a MessageD

#### Messages

##### MessageA : Video element without text transcription

-    code : **VideoElementWithoutTextTranscription** 
-    status: Failed
-    parameter : tag name, snippet
-    present in source : yes

##### MessageB : We detected video element with a text transcription nearby check manually that relevant

-    code : **WeDetectedVideoElementWithTextTranscriptionNearbyCheckManually** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageC : We detected video element, check manually the presence of a text transcription

-    code : **WeDetectedVideoElementCheckManuallyThePresenceOfTextTranscription** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageD : No video element detected, check manually the presence of other video element and its text transcription

-    code : **NoVideoElementDetectedCheckManuallyThePresenceOfOtherVideoElementAndItsTextTranscription** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

#### Rules remark

 * VideoElementWithoutTextTranscription (fr): &Eacute;l&eacute;ment video sans transcription textuelle
 * VideoElementWithoutTextTranscription (en): Video element without text transcription

 * WeDetectedVideoElementWithTextTranscriptionNearbyCheckManually (fr): Nous d&eacute;tectons des &eacute;l&eacute;ments video avec une transcription textuelle à proximit&eacute;, v&eacute;rifier manuellement que cela est correct :
 * WeDetectedVideoElementWithTextTranscriptionNearbyCheckManually (en): We detected video element with a text transcription nearby check manually that relevant

 * WeDetectedVideoElementCheckManuallyThePresenceOfTextTranscription (fr): Nous d&eacute;tectons des &eacute;l&eacute;ments vid&eacute;o, v&eacute;rifier manuellement la pr&eacute;sence d'une transcription textuelle
 * WeDetectedVideoElementCheckManuallyThePresenceOfTextTranscription (en): We detected video element, check manually the presence of an text transcription

 * NoVideoElementDetectedCheckManuallyThePresenceOfOtherVideoElementAndItsTextTranscription (fr): Aucun &eacute;l&eacute;ment vid&eacute;o d&eacute;tect&eacute;, v&eacute;rifier manuellement la pr&eacute;sence d'autre &eacute;l&eacute;ments vid&eacute;o et de leur transcription textuelle
 * NoVideoElementDetectedCheckManuallyThePresenceOfOtherVideoElementAndItsTextTranscription (en): No video element detected, check manually the presence of other video element and its text transcription

### Accede Web guidelines

 * Rgaa32016-4-1-3-Accedeweb-HTML-13
 * Rgaa32016-4-1-3-Accedeweb-EDIT-8-3

### Analysis

#### Not Applicable

If no media element is present in the page (**Set1**, **Set2**, **Set3** and **Set4** are empty)

#### Failed

At least one video element don't have a transcription near the element (At least one element return true-result of **test1**)

#### Pre-qualified

In all cases

## Diagrammes

![](https://raw.githubusercontent.com/Tanaguru/RGAA3-2016/master/docs/Diagrammes/Test4-1-2.png?token=AI6sAwxs4h--7_b-FlLferqPi2LgqjcJks5ZAGRFwA%3D%3D)

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

the following list of video extension :
 - mp3 ;

This list must be implement with a file editable by the administrator

Complete this list if necessary.
