# Rule 4.6.2

## Summary

## Business description

### Criterion

[4.6](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-4-6)

###Test

[4.6.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-4-6-2)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#mMediaTemp">m&eacute;dia temporel</a> synchronis&eacute; en direct v&eacute;rifie-t-il une de ces conditions ? 
 
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

##### MessageA : We detected video element with synchronized captions, check that are relevant

-    code : **WeDetectedVideoElementWithSynchronizedCaptionsCheckThatRelevant** 
-    status: Pre-Qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageB: Manual check on page

-   code : ManualCheckOnPage
-   status: Pre-Qualified (NMI-Neutral)
-   present in source : yes

#### Rules remark

 * WeDetectedVideoElementWithSynchronizedCaptionsCheckThatRelevant (fr): Nous d&eacute;tectons un &eacute;l&eacute;ment audio avec sous-titres synchronis&eacute;s, v&eacute;rifier qu'ils sont pertinent
 * WeDetectedVideoElementWithSynchronizedCaptionsCheckThatRelevant (en): We detected audio element with synchronized captions, check that are relevant

 * ManualCheckOnPage (fr): Veuillez v&eacute;rifier manuellement dans la page :
 * ManualCheckOnPage (en): Please manual check on the page:

### Analysis

#### Pre-qualified

In all cases
