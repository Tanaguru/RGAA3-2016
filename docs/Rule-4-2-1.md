# Rule 4.2.1

## Summary

## Business description

### Criterion

[4.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-4-2)

###Test

[4.2.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-4-2-1)

### Description

Pour chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#mdia-temporel-type-son-vido-et-synchronis">m&eacute;dia temporel</a> pr&eacute;-enregistr&eacute; seulement audio, ayant une <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#transcription-textuelle-media-temporel">transcription textuelle</a>, celle-ci est-elle pertinente (<a href="http://references.modernisation.gouv.fr/rgaa/cas-particuliers.html#cp-4-1,4-2,4-3,4-5,4-7,4-9,4-11,4-13" title="Cas particuliers pour le crit&egrave;re 4.2">hors cas particuliers</a>) ?

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

### Process

#### Tests

##### Test1

If **Set1** is empty, raise a MessageA

##### Test2

If **Set1** is not empty, check the presence in the content of page a mention or a link that like following expression:
 - text transcription
 - transcription 
 - transcription textuelle
 - video text
 - Texte de la vidéo

For each element return true-result of **Test2**, raise a MessageB, raise a MessageA instead

#### Messages

##### MessageA : No audio element detected, check manually the presence of an audio element and check if its text transcription is relevant

-    code : **NoAudioElementDetectedCheckManuallyThePresenceOfAudioElementAndCheckIfItsTextTranscriptionRelevant** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageB : We detected audio element, check manually, if presente, if the text transcription is relevant

-    code : **WeDetectedAudioElementCheckManuallyIfPresentIfTextTranscriptionRelevant** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet, text
-    present in source : yes

#### Rules remark

 * NoAudioElementDetectedCheckManuallyThePresenceOfAudioElementAndCheckIfItsTextTranscriptionRelevant (fr): Aucun &eacute;l&eacute;ment audio avec transcription textuelle d&eacute;tect&eacute;, v&eacute;rifier manuellement la pr&eacute;sence d'&eacute;l&eacute;ments audio et v&eacute;rifier si leur transcription textuelle sont pertinente
 * NoAudioElementDetectedCheckManuallyThePresenceOfAudioElementAndCheckIfItsTextTranscriptionRelevant (en): No audio element with text transcription detected, check manually the presence of an audio element and check if its text transcription is relevant

 * WeDetectedAudioElementCheckManuallyIfPresentIfTextTranscriptionRelevant (fr): Nous d&eacute;tectons des &eacute;l&eacute;ments audio, v&eacute;rifier manuellement, si pr&eacute;sente, si la transcription textuelle est pertinente
 * WeDetectedAudioElementCheckManuallyIfPresentIfTextTranscriptionRelevant (en): We detected audio element, check manually, if presente, if the text transcription is relevant

### Accede Web guidelines

 * Rgaa32016-4-2-1-Accedeweb-HTML-13
 * Rgaa32016-4-2-1-Accedeweb-EDIT-8-3

### Analysis

#### Pre-qualified

In all cases
