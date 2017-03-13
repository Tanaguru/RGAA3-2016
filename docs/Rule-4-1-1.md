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

All the elements `<embed>` and `<object>` tags (css selector : `embed`, `object`);

### Process

#### Tests

##### Test1

If **Set1** is empty and **Set2** is not empty, raise a MessageA

If **Set1** is not empty, raise a MessageB

#### Messages

##### MessageA : We detected audio element, check manually the presence of a text transcription

-    code : **WeDetectedAudioElementCheckManuallyThePresenceOfTextTranscription** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageB : No audio element detected, check manually the presence of other audio element and its text transcription

-    code : **NoAudioElementDetectedCheckManuallyThePresenceOfOtherAudioElementAndItsTextTranscription** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

#### Rules remark

 * WeDetectedAudioElementCheckManuallyThePresenceOfTextTranscription (fr): Nous d&eacute;tectons des &eacute;l&eacute;ments audio, v&eacute;rifier manuellement la pr&eacute;sence d'une transcription textuelle
 * WeDetectedAudioElementCheckManuallyThePresenceOfTextTranscription (en): We detected audio element, check manually the presence of a text transcription

 * NoAudioElementDetectedCheckManuallyThePresenceOfOtherAudioElementAndItsTextTranscription (fr): Aucun &eacute;l&eacute;ment audio d&eacute;tect&eacute;, v&eacute;rifier manuellement la pr&eacute;sence d'autre &eacute;l&eacute;ments audio et de leur transcription textuelle
 * NoAudioElementDetectedCheckManuallyThePresenceOfOtherAudioElementAndItsTextTranscription (en): No audio element detected, check manually the presence of other audio element and its text transcription

### Accede Web guidelines

 * Rgaa32016-4-1-1-Accedeweb-HTML-13
 * Rgaa32016-4-1-1-Accedeweb-EDIT-8-3

### Analysis

#### Not Applicable

If no media element is present in the page (**Set1** and **Set2** is empty)

#### Pre-qualified

In all cases
