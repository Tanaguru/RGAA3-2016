# Rule 4.2.3

## Summary

## Business description

### Criterion

[4.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-4-2)

###Test

[4.2.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-4-2-3)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#mdia-temporel-type-son-vido-et-synchronis">m&eacute;dia temporel</a> synchronis&eacute; pr&eacute;-enregistr&eacute; v&eacute;rifie-t-il une de ces conditions (<a href="http://references.modernisation.gouv.fr/rgaa/cas-particuliers.html#cp-4-1,4-2,4-3,4-5,4-7,4-9,4-11,4-13" title="Cas particuliers pour le crit&egrave;re 4.2">hors cas particuliers</a>) ? 
 
 * La <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#transcription-textuelle-media-temporel">transcription textuelle</a> est pertinente 
 * L'<a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#audiodescription-synchronise-media-temporel">audio-description</a> synchronis&eacute;e est pertinente 
 * L'<a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#audiodescription-synchronise-media-temporel">audio-description</a> synchronis&eacute;e de la version alternative est pertinente 

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

All the elements `<video>` tags (css selector : `video`);

### Process

#### Tests

##### Test1

If **Set1** is empty, raise a MessageA

##### Test2

For each element of **Set1**, check the presence in the content of page a mention or a link that like following expression:
 - text transcription
 - transcription 
 - transcription textuelle
 - video text
 - Texte de la vidéo

For each element return true-result of **Test2**, raise a MessageB

##### Test3

For each element of **Set1**, check the presence of an `<audio>`, a `<button>`, a `<div role="button">` tag with an id or a class like following expression:
 - audiodescription
 - ad
 - audio-description
 - audio_description

For each element return true-result of **Test3**, raise a MessageA instead

#### Messages

##### MessageA : No video element detected, check manually the presence of an video element and check if its text transcription is relevant

-    code : **NoVideoElementDetectedCheckManuallyThePresenceOfVideoElementAndCheckIfItsTextTranscriptionRelevant** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageB : We detected video element, check manually, if presente, if the text transcription is relevant

-    code : **WeDetectedVideoElementCheckManuallyIfPresentIfTextTranscriptionRelevant** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet, text
-    present in source : yes

#### Rules remark

 * NoVideoElementDetectedCheckManuallyThePresenceOfVideoElementAndCheckIfItsTextTranscriptionRelevant (fr): Aucun &eacute;l&eacute;ment vid&eacute;o avec transcription textuelle d&eacute;tect&eacute;, v&eacute;rifier manuellement la pr&eacute;sence d'&eacute;l&eacute;ments vid&eacute;o et v&eacute;rifier si leur transcription textuelle sont pertinente
 * NoVideoElementDetectedCheckManuallyThePresenceOfVideoElementAndCheckIfItsTextTranscriptionRelevant (en): No video element with text transcription detected, check manually the presence of an video element and check if its text transcription is relevant

 * WeDetectedVideoElementCheckManuallyIfPresentIfTextTranscriptionRelevant (fr): Nous d&eacute;tectons des &eacute;l&eacute;ments vid&eacute;o, v&eacute;rifier manuellement, si pr&eacute;sente, si la transcription textuelle est pertinente
 * WeDetectedVideoElementCheckManuallyIfPresentIfTextTranscriptionRelevant (en): We detected video element, check manually, if presente, if the text transcription is relevant

### Accede Web guidelines

 * Rgaa32016-4-2-3-Accedeweb-HTML-13
 * Rgaa32016-4-2-3-Accedeweb-EDIT-8-3

### Analysis

#### Pre-qualified

In all cases
