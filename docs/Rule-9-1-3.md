# Rule 9.1.3

## Summary

## Business description

### Criterion

[9.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-9-1)

###Test

[9.1.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-9-1-3)

### Description

Dans chaque page Web, chaque <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#mTitre">titre</a> (balise `h` ou balise poss&eacute;dant un role ARIA `"heading"` associ&eacute; &agrave; une propri&eacute;t&eacute; `aria-level`) n&eacute;cessaire &agrave; la structure de l'information est-il pr&eacute;sent ?

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

All the tags in the page that not a `<Hx>` tag where x is comprise between 1 and 6 or not a tag with a `"role"` attribute equals to "heading" and an `"aria-level"` attribute (h1, h2, h3, h4, h5, h6, [role=heading][aria-level])

### Process

#### Tests

##### Test1

For each element of **Set1**, check the presence of a `class` or `id` attribute with a value like following list :
 - heading
 - title
 - titre

For each occurrence of true-result of **Test1**, raise a MessageA, raise a MessageB

#### Messages

##### MessageA : We detected element that can be heading elements, check manualy if the heading hierarchy is relevant

-    code : **WeDetectedElementThatCanBeHeadingCheckManualyHeadingHierarchyRelevant** 
-    status: Pre-Qualified (NMI-Failed)
-    parameter : text content, definition
-    present in source : yes

##### MessageB : Check user is warned in case of new window open

-   code : ManualCheckOnElements
-   status: Pre-Qualified (NMI-Neutral)
-   parameter : text content, snippet
-   present in source : yes

#### Rules remark

 * WeDetectedElementThatCanBeHeadingCheckManualyHeadingHierarchyRelevant (fr): Nous d&eacute;tectons des &eacute;l&eacute;ments pouvant &ecirc;tre des titres, v&eacute;rifier manuellement que la hi&eacute;rarchie de titre est pertinente :
 * WeDetectedElementThatCanBeHeadingCheckManualyHeadingHierarchyRelevant (en): We detected element that can be heading elements, check manualy if the heading hierarchy is relevant

 * ManualCheckOnElements (fr): Veuillez v&eacute;rifier les &eacute;l&eacute;ments <code>{0}</code> d&eacute;tect&eacute;s :
 * ManualCheckOnElements (en): Please check the <code>{0}</code> detected elements :

### Analysis

#### No Tested 

In all cases
