# Rule 4.3.1

## Summary

## Business description

### Criterion

[4.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-4-3)

###Test

[4.3.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-4-3-1)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#mdia-temporel-type-son-vido-et-synchronis">m&eacute;dia temporel</a> synchronis&eacute; pr&eacute;-enregistr&eacute; v&eacute;rifie-t-il, si n&eacute;cessaire, l'une de ces conditions (<a href="http://references.modernisation.gouv.fr/rgaa/cas-particuliers.html#cp-4-1,4-2,4-3,4-5,4-7,4-9,4-11,4-13" title="Cas particuliers pour le crit&egrave;re 4.3">hors cas particuliers</a>) ? 
 
 * Le <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#transcription-textuelle-media-temporel">m&eacute;dia temporel</a> synchronis&eacute; poss&egrave;de des <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#soustitres-synchroniss-objet-multimdia">sous-titres synchronis&eacute;s</a> 
 * Il existe une version alternative poss&eacute;dant des <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#soustitres-synchroniss-objet-multimdia">sous-titres synchronis&eacute;s</a> accessible via un <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#lien-adjacent">lien adjacent</a> (une url ou une ancre) 


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

##### MessageA : We detected video element, check manually that possible to show synchronized captions

-    code : **WeDetectedVideoElementCheckManuallyThatPossibleToShowSynchronizedCaptions** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageB : No video element detected, check manually the presence of video element and that possible to show synchronized captions

-    code : **NoVideoElementDetectedCheckManuallyThePresenceOfOtherVideoElementAndThatPossibleToShowSynchronizedCaptions** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

#### Rules remark

 * WeDetectedVideoElementCheckManuallyThatPossibleToShowSynchronizedCaptions (fr): Nous d&eacute;tectons des &eacute;l&eacute;ments vid&eacute;o, v&eacute;rifier manuellement qu'il est possible d'afficher les sous-titres
 * WeDetectedVideoElementCheckManuallyThatPossibleToShowSynchronizedCaptions (en): We detected video element, check manually that possible to show synchronized captions

 * NoVideoElementDetectedCheckManuallyThePresenceOfOtherVideoElementAndThatPossibleToShowSynchronizedCaptions (fr): Aucun &eacute;l&eacute;ment vid&eacute;o d&eacute;tect&eacute;, v&eacute;rifier manuellement la pr&eacute;sence &eacute;l&eacute;ments vid&eacute;o et qu'il est possible d'afficher les sous-titres
 * NoVideoElementDetectedCheckManuallyThePresenceOfOtherVideoElementAndThatPossibleToShowSynchronizedCaptions (en): No video element detected, check manually the presence of video element and that possible to show synchronized captions

### Accede Web guidelines

 * Rgaa32016-4-3-1-Accedeweb-HTML-13
 * Rgaa32016-4-3-1-Accedeweb-EDIT-8-3

### Analysis

#### Pre-qualified

In all cases
