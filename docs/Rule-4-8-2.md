# Rule 4.8.2

## Summary

## Business description

### Criterion

[4.8](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-4-8)

###Test

[4.8.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-4-8-2)

### Description

Pour chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#mdia-temporel-type-son-vido-et-synchronis">m&eacute;dia temporel</a> synchronis&eacute; ayant une <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#audiodescription-synchronise-media-temporel">audio-description</a> synchronis&eacute;e, celle-ci est-elle pertinente ?

### Level

**AA**

## Technical description

### Scope

**Page**

### Decision level

**Semi-Decidable**

## Algorithm

### Selection

#### Set1

All the elements `<video>` tags (css selector : `video`);

#### Set2

All the elements `<bgsound>`, `<embed>` and `<object>` tags (css selector : `bgsound`, `embed`, `object`);

### Process

#### Tests

##### Test1

If **Set1** is empty and **Set2** is not empty, raise a MessageA

##### Test2

For each element of **Set1**, check the presence of an `<audio>`, a `<button>`, a `<div role="button">` tag with an id or a class like following expression:
 - audiodescription
 - ad
 - audio-description
 - audio_description

For each element return true-result of **Test3**, raise a MessageB

For each element return false-result of **Test2**, raise a MessageA

#### Messages

##### MessageA : No video element detected, check manually the presence of an video element and check if its text transcription is relevant

-    code : **NoVideoElementDetectedCheckManuallyThePresenceOfVideoElementAndCheckIfItsTextTranscriptionRelevant** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageB : We detected video element, check manually, if presente, if the audio description is relevant

-    code : **WeDetectedVideoElementCheckManuallyIfPresentIfAudioDescriptionRelevant** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet, text
-    present in source : yes

#### Rules remark

 * NoVideoElementDetectedCheckManuallyThePresenceOfVideoElementAndCheckIfItsTextTranscriptionRelevant (fr): Aucun &eacute;l&eacute;ment vid&eacute;o avec transcription textuelle d&eacute;tect&eacute;, v&eacute;rifier manuellement la pr&eacute;sence d'&eacute;l&eacute;ments vid&eacute;o et v&eacute;rifier si leur transcription textuelle sont pertinente
 * NoVideoElementDetectedCheckManuallyThePresenceOfVideoElementAndCheckIfItsTextTranscriptionRelevant (en): No video element with text transcription detected, check manually the presence of an video element and check if its text transcription is relevant

 * WeDetectedVideoElementCheckManuallyIfPresentIfAudioDescriptionRelevant (fr): Nous d&eacute;tectons des &eacute;l&eacute;ments vid&eacute;o, v&eacute;rifier manuellement, si pr&eacute;sente, si l'audio description est pertinente
 * WeDetectedVideoElementCheckManuallyIfPresentIfAudioDescriptionRelevant (en): We detected video element, check manually, if presente, if the audio description is relevant

### Accede Web guidelines

 * Rgaa32016-4-8-2-Accedeweb-EDIT-8-3

### Analysis

#### Not Applicable

if no media element is present in the page (**Set1** and **Set2** is empty)

#### Pre-qualified

In all cases