# Rule 9.3.1

## Summary

## Business description

### Criterion

[9.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-9-3)

###Test

[9.3.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-9-3-1)

### Description

Dans chaque page Web, les informations regroup&eacute;es sous forme de listes non ordonn&eacute;es v&eacute;rifient-elles une de ces conditions ? 
 
 * La liste utilise les balises HTML `ul` et `li` 
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

#### Set2

All Series of links (more than 2 links in a same tag) only separate by a space ` `, a ` | `, a ` * `, a ` § `, a ` ¤ `, a ` µ `, a `<br />` tag or a ` - `

#### Set3

All tags that contains more than 2 following caracters : a ` | `, a ` * `, a ` § `, a ` ¤ `, a ` µ ` or a ` - `. These caracters can be followed by a `<br />` tag

### Process

#### Tests

##### Test2

For each element of **Set2**, raise the MessageB.

##### Test3

For each element of **Set3**, raise the MessageB.

If **Set2** and **Set3** are empty, raise the MessageA

#### Messages

##### MessageA : Check user is warned in case of new window open

-   code : ManualCheckOnElements
-   status: Pre-Qualified (NMI-Neutral)
-   parameter : text content, snippet
-   present in source : yes

##### MessageB : We detected elements that appear to be list elements not implement in list

-    code : **WeDetectedElementsThatAppearToBeListElementsNotImplementInList** 
-    status: Pre-qualified (NMI-Failed)
-    parameter : snippet
-    present in source : yes

#### Rules remark

 * ManualCheckOnElements (fr): Veuillez v&eacute;rifier les &eacute;l&eacute;ments <code>{0}</code> d&eacute;tect&eacute;s :
 * ManualCheckOnElements (en): Please check the <code>{0}</code> detected elements :

 * WeDetectedElementsThatAppearToBeListElementsNotImplementInList (fr): Nous d&eacute;tectons des &eacute;l&eacute;ments qui semble &ecirc;tre des &eacute;l&eacute;ments de liste non impl&eacute;ment&eacute; dans une liste :
 * WeDetectedElementsThatAppearToBeListElementsNotImplementInList (en): We detected elements that appear to be list elements not implement in list:

#### Rules remark

 * Rgaa32016-9-3-1-Accedeweb-HTML-1-6
 * Rgaa32016-9-3-1-Accedeweb-HTML-8-1
 * Rgaa32016-9-3-1-Accedeweb-EDIT-5

### Analysis

#### Per-qualified

In all cases
