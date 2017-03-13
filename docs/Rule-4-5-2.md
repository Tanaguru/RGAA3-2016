# Rule 4.5.2

## Summary

## Business description

### Criterion

[4.5](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-4-5)

###Test

[4.5.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-4-5-2)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#mMediaTemp">m&eacute;dia temporel</a> synchronis&eacute; en direct v&eacute;rifie-t-il, si n&eacute;cessaire, une de ces conditions (<a href="http://references.modernisation.gouv.fr/rgaa/cas-particuliers.html#cp-4-1,4-2,4-3,4-5,4-7,4-9,4-11,4-13" title="Cas particuliers pour le crit&egrave;re 4.5">hors cas particuliers</a>) ? 
 
 *  Il existe des <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#soustitres-synchroniss-objet-multimdia">sous-titres synchronis&eacute;s</a> 
 *  Il existe une version ayant des <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#soustitres-synchroniss-objet-multimdia">sous-titres synchronis&eacute;s</a> accessible via un <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#lien-adjacent">lien adjacent</a> (une `url` ou une `ancre`) 
 *  Il existe une <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#transcription-textuelle-media-temporel">transcription textuelle</a> accessible via un <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#lien-adjacent">lien adjacent</a> (une `url` ou une `ancre`) 
 *  Il existe une <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#transcription-textuelle-media-temporel">transcription textuelle</a> adjacente clairement identifiable 


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

All the elements `<audio>` tags (css selector : `audio`);

#### Set2

All the elements `<embed>` and `<object>` tags (css selector : `embed`, `object`);

### Process

#### Tests

##### Test1

If **Set1** is empty and **Set2** is not empty, raise a MessageA

##### Test2

For each element of **Set1**, check the presence in the content of page a mention or a link that like following expression:
 - text transcription
 - transcription 
 - transcription textuelle
 - video text
 - Texte de la vidéo

For each element return true-result of **Test2**, raise a MessageB

##### Test3

For each element of **Set1**, check the presence of a `<track>` tag child of the element

For each element return true-result of **Test3**, raise a MessageC

For each element return false-result of **Test2** and **Test3**, raise a MessageA

#### Messages

##### MessageA : Check manually the presence of an video element and check whether it has an alternative

-    code : **CheckManuallyThePresenceOfVideoElementAndCheckWhetherItHasAnAlternative** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageB : We detected video element which appears to be accompanied by a textual transcription, check manually

-    code : **WeDetectedVideoElementWhichAppearsToBeAccompaniedByTextualTranscriptionCheckManually** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet, text
-    present in source : yes

##### MessageC : We detected video element with synchronized captions

-    code : **WeDetectedVideoElementWithSynchronizedCaptions** 
-    status: Pre-qualified (NMI-Passed)
-    parameter : tag name, snippet
-    present in source : yes

#### Rules remark

 * CheckManuallyThePresenceOfVideoElementAndCheckWhetherItHasAnAlternative (fr): V&eacute;rifier manuellement la pr&eacute;sence d'&eacute;l&eacute;ments vid&eacute;o et v&eacute;rifier qu'elle a une alternative
 * CheckManuallyThePresenceOfVideoElementAndCheckWhetherItHasAnAlternative (en): Check manually the presence of an video element and check whether it has an alternative

 * WeDetectedVideoElementWhichAppearsToBeAccompaniedByTextualTranscriptionCheckManually (fr): Nous d&eacute;tectons des &eacute;l&eacute;ments vid&eacute;o qui semble &ecirc;tre accompagn&eacute; d'une transcription textuelle, v&eacute;rifier manuellement
 * WeDetectedVideoElementWhichAppearsToBeAccompaniedByTextualTranscriptionCheckManually (en): We detected video element which appears to be accompanied by a textual transcription, check manually

 * WeDetectedVideoElementWithSynchronizedCaptions (fr): Nous d&eacute;tectons des &eacute;l&eacute;ments vid&eacute;o avec des sous-titres
 * WeDetectedVideoElementWithSynchronizedCaptions (en): We detected video element, check manually that possible to show synchronized captions

### Analysis

#### Not Applicable

if no media element is present in the page (**Set1** and **Set2** is empty)

#### Pre-qualified

In all cases

