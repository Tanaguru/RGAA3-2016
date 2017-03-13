# Rule 4.4.1

## Summary

## Business description

### Criterion

[4.4](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-4-4)

###Test

[4.4.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-4-4-1)

### Description

Pour chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#mdia-temporel-type-son-vido-et-synchronis">m&eacute;dia temporel</a> synchronis&eacute; pr&eacute;-enregistr&eacute; ayant des <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#soustitres-synchroniss-objet-multimdia">sous-titres synchronis&eacute;s</a>, ces sous-titres sont-ils pertinents ?

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

All the elements `<video>` tags with at least one child `<track>` tag (css selector : `video`);

#### Set2

All the elements `<embed>` and `<object>` tags (css selector : `embed`, `object`);

### Process

#### Tests

##### Test1

For each element of **Set1**, raise a MessageA

If **Set1** is empty and **Set2** is not empty, raise a MessageB

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

 * WeDetectedVideoElementWithSynchronizedCaptionsCheckThatRelevant (fr): Nous d&eacute;tectons un &eacute;l&eacute;ment vid&eacute;o avec sous-titres synchronis&eacute;s, v&eacute;rifier qu'ils sont pertinent
 * WeDetectedVideoElementWithSynchronizedCaptionsCheckThatRelevant (en): We detected video element with synchronized captions, check that are relevant

 * ManualCheckOnPage (fr): Veuillez v&eacute;rifier manuellement dans la page :
 * ManualCheckOnPage (en): Please manual check on the page:

### Accede Web guidelines

 * Rgaa32016-4-4-1-Accedeweb-EDIT-8-3

### Analysis

#### Not Applicable

if no media element is present in the page (**Set1** and **Set2** is empty)

#### Pre-qualified

In all cases