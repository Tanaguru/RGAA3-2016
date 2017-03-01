# Rule 4.1.2

## Summary

## Business description

### Criterion

[4.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-4-1)

###Test

[4.1.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-4-1-2)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#mdia-temporel-type-son-vido-et-synchronis">m&eacute;dia temporel</a> pr&eacute;-enregistr&eacute; seulement vid&eacute;o v&eacute;rifie-t-il, si n&eacute;cessaire, une de ces conditions (<a href="http://references.modernisation.gouv.fr/rgaa/cas-particuliers.html#cp-4-1,4-2,4-3,4-5,4-7,4-9,4-11,4-13" title="Cas particuliers pour le crit&egrave;re 4.1">hors cas particuliers</a>) ? 
 
 *  Il existe une <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#version-alternative-audio-seulement">version alternative <q>audio seulement</q></a> accessible via un <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#lien-adjacent">lien adjacent</a> (une `url` ou une `ancre`) 
 *  Il existe une <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#transcription-textuelle-media-temporel">transcription textuelle</a> adjacente clairement identifiable 
 *  Il existe une <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#audiodescription-synchronise-media-temporel">audio-description</a> synchronis&eacute;e  
 *  Il existe une version alternative avec une <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#audiodescription-synchronise-media-temporel">audio-description</a> synchronis&eacute;e accessible via un <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#lien-adjacent">lien adjacent</a> (une `url` ou une `ancre`) 


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

If **Set1** is not empty, raise a MessageB

#### Messages

##### MessageA : We detected video element, check manually the presence of an alternative

-    code : **WeDetectedVideoElementCheckManuallyThePresenceOfAlternative** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageB : No video element detected, check manually the presence of other video element and its alternative

-    code : **NoVideoElementDetectedCheckManuallyThePresenceOfOtherVideoElementAndItsAlternative** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

#### Rules remark

 * WeDetectedVideoElementCheckManuallyThePresenceOfAlternative (fr): Nous d&eacute;tectons des &eacute;l&eacute;ments vid&eacute;o, v&eacute;rifier manuellement la pr&eacute;sence d'une alternative
 * WeDetectedVideoElementCheckManuallyThePresenceOfAlternative (en): We detected video element, check manually the presence of an alternative

 * NoVideoElementDetectedCheckManuallyThePresenceOfOtherVideoElementAndItsAlternative (fr): Aucun &eacute;l&eacute;ment vid&eacute;o d&eacute;tect&eacute;, v&eacute;rifier manuellement la pr&eacute;sence d'autre &eacute;l&eacute;ments vid&eacute;o et de leur transcription textuelle
 * NoVideoElementDetectedCheckManuallyThePresenceOfOtherVideoElementAndItsAlternative (en): No video element detected, check manually the presence of other video element and its alternative

### Accede Web guidelines

 * Rgaa32016-4-1-2-Accedeweb-HTML-13
 * Rgaa32016-4-1-2-Accedeweb-EDIT-8-3

### Analysis

#### Pre-qualified

In all cases

