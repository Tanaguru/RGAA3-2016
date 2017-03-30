# Rule 9.3.2

## Summary

## Business description

### Criterion

[9.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-9-3)

###Test

[9.3.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-9-3-2)

### Description

Dans chaque page Web, les informations regroup&eacute;es sous forme de listes ordonn&eacute;es v&eacute;rifient-elles une de ces conditions ? 
 
 * La liste utilise les balises HTML `ol` et `li` 
 * La liste utilise les roles ARIA `list` et `listitem` 


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

All tags that contains texts preceded by a sequence of numbers. These texts can be followed by a `<br />` tag

### Process

#### Tests

##### Test1

For each element of **Set1**, raise the MessageA.

If **Set1** empty, raise the MessageB

#### Messages

##### MessageA : We detected elements that appear to be order list elements not implement in order list

-    code : **WeDetectedElementsThatAppearToBeOrderListElementsNotImplementInOrderList** 
-    status: Pre-qualified (NMI-Failed)
-    parameter : snippet
-    present in source : yes

##### MessageB : Check user is warned in case of new window open

-   code : ManualCheckOnElements
-   status: Pre-Qualified (NMI-Neutral)
-   parameter : text content, snippet
-   present in source : yes

#### Rules remark

 * ManualCheckOnElements (fr): Veuillez v&eacute;rifier les &eacute;l&eacute;ments <code>{0}</code> d&eacute;tect&eacute;s :
 * ManualCheckOnElements (en): Please check the <code>{0}</code> detected elements :

 * WeDetectedElementsThatAppearToBeOrderListElementsNotImplementInOrderList (fr): Nous d&eacute;tectons des &eacute;l&eacute;ments qui semble &ecirc;tre des &eacute;l&eacute;ments de liste ordonn&eacute;e non impl&eacute;ment&eacute; dans une liste ordonn&eacute;e :
 * WeDetectedElementsThatAppearToBeOrderListElementsNotImplementInOrderList (en): We detected elements that appear to be order list elements not implement in order list:

#### Rules remark

 * Rgaa32016-9-3-2-Accedeweb-HTML-8-2
 * Rgaa32016-9-3-2-Accedeweb-EDIT-5

### Analysis

#### Per-qualified

In all cases