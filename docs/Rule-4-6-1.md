# Rule 4.6.1

## Summary

## Business description

### Criterion

[4.6](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-4-6)

###Test

[4.6.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-4-6-1)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#mMediaTemp">m&eacute;dia temporel</a> seulement audio en direct v&eacute;rifie-t-il une de ces conditions ? 
 
 *  Les <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#soustitres-synchroniss-objet-multimdia">sous-titres synchronis&eacute;s</a> sont pertinents 
 *  Les <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#soustitres-synchroniss-objet-multimdia">sous-titres synchronis&eacute;s</a> de la version alternative sont pertinents 
 *  La <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#transcription-textuelle-media-temporel">transcription textuelle</a> est pertinente 

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

All the elements `<audio>` tags with at least one child `<track>` tag (css selector : `audio`);

### Process

#### Tests

##### Test1

For each element of **Set1**, raise a MessageA

If **Set1** is empty, raise a MessageB

#### Messages

##### MessageA : We detected audio element with synchronized captions, check that are relevant

-    code : **WeDetectedAudioElementWithSynchronizedCaptionsCheckThatRelevant** 
-    status: Pre-Qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageB: Manual check on page

-   code : ManualCheckOnPage
-   status: Pre-Qualified (NMI-Neutral)
-   present in source : yes

#### Rules remark

 * WeDetectedAudioElementWithSynchronizedCaptionsCheckThatRelevant (fr): Nous d&eacute;tectons un &eacute;l&eacute;ment audio avec sous-titres synchronis&eacute;s, v&eacute;rifier qu'ils sont pertinent
 * WeDetectedAudioElementWithSynchronizedCaptionsCheckThatRelevant (en): We detected audio element with synchronized captions, check that are relevant

 * ManualCheckOnPage (fr): Veuillez v&eacute;rifier manuellement dans la page :
 * ManualCheckOnPage (en): Please manual check on the page:

### Accede Web guidelines

 * Rgaa32016-4-4-1-Accedeweb-EDIT-8-3

### Analysis

#### Pre-qualified

In all cases
