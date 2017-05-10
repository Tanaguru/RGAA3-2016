# Rule 9.2.1

## Summary

This test consists in checking whether the `header`, `nav`, `main` and `footer` tag are present.

## Business description

### Criterion

[9.2](http://references.modernisation.gouv.fr/referentiel-technique-0#crit-9-2)

### Test

[9.2.1](http://references.modernisation.gouv.fr/referentiel-technique-0#test-9-2-1)

### Description

Dans chaque page Web, la structure du document v&eacute;rifie-t-elle ces conditions ? 
 
 * La <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#mZoneHeader">zone d'en-t&ecirc;te de la page</a> est structur&eacute;e via une balise `header` 
 * Les <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#mMenuNav">zones de navigation principales et secondaires</a> sont structur&eacute;es via une balise `nav` 
 *  La balise `nav` est r&eacute;serv&eacute;e &agrave; la structuration des zones de navigations principales et secondaires 
 * La <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#mZoneMain">zone de contenu principal</a> est structur&eacute;e via une balise `main` 
 * La structure du document utilise une balise `main` unique 
 * La <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#mZoneFooter">zone de pied de page</a> est structur&eacute;e via une balise `footer` 

### Level

**A**

## Technical description

### Scope

**Page**

### Decision level

**Decidable**

## Algorithm

### Selection

#### Set1

All the `<main>` tags

#### Set2

All the tags with an attribute `id` that value is `header`, `top` or `banner`

#### Set3

All the tags with an attribute `role` that value is `banner`

#### Set4

All the tags with an attribute `id` that value is `nav`, `navigation`, `nav-menu`, `nav_menu`, `primary-nav`, `secondary-nav`, `primary_nav`, `secondary_nav`, `menu-principal`, `menu-secondaire`, `menu_principal`, `menu_secondaire` or `menu`

#### Set5

All the tags with an attribute `role` that value is `navigation`

#### Set6

All the tags with an attribute `id` that value is `footer`, `footer-content`, `content-info` or `pied-de-page`

#### Set7

All the tags with an attribute `role` that value is `content-info`

### Process

#### Test

##### Test1

The `<!DOCTYPE>` tags is `<!DOCTYPE html>`

##### Test2 

Check if the **Test1** is true and the page has no `<header>` tag. 

if **Test2** is true and **Set2** or **Set3** are not empty raise a MessageB.

if **Test2** is true and **Set2** and **Set3** are empty raise a MessageC.

##### Test3

if **Test1** is true and **Test2** is false, check if the nearest ancestor sectioning of the first `<header>` tag is not `<body>` tag. 

if **Test3** is true, raise a MessageA

##### Test4

Check if the **Test1** is true and the page has no `<nav>` tag. 

if **Test4** is true and **Set4** or **Set5** are not empty raise a MessageD.

if **Test4** is true and **Set4** and **Set5** are empty raise a MessageE.

##### Test5

if the **Test1** is true, and the page has no `<main>` tag, raise a MessageF.

##### Test6

if the **Test1** is true, and **Set1** has more than one item, raise a MessageG.

##### Test7

Check if the **Test1** is true and the page has no `<footer>` tag. 

if **Test7** is true and **Set6** or **Set7** are not empty raise a MessageH.

if **Test7** is true and **Set6** and **Set7** are empty raise a MessageI.

#### Message

##### MessageA : Suspect Missed implement Header tag

-    code : **SuspectMissedImplementHeadertag** 
-    status: Pre-Qualified (NMI-Failed)
-    parameter : snippet
-    present in source : yes

##### MessageB : Missing Header tag

-    code : **MissingHeadertag** 
-    status: Failed
-    parameter : snippet
-    present in source : yes

##### MessageC : Suspected Missing Header tag

-    code : **SuspectedMissingHeadertag** 
-    status: Pre-Qualified (NMI-Failed)
-    parameter : none
-    present in source : no

##### MessageD : Missing Nav tag

-    code : **MissingNavtag** 
-    status: Failed
-    parameter : snippet
-    present in source : yes

##### MessageE : Suspected Missing Nav tag

-    code : **SuspectedMissingNavtag** 
-    status: Pre-Qualified (NMI-Failed)
-    parameter : none
-    present in source : no

##### MessageF : Missing Main tag

-    code : **MissingMaintag** 
-    status: Failed
-    parameter : none
-    present in source : no

##### MessageG : Multiple Main tag

-    code : **MultipleMaintag** 
-    status: Failed
-    parameter : Snippet
-    present in source : yes

##### MessageH : Missing Footer tag

-    code : **MissingFootertag** 
-    status: Failed
-    parameter : snippet
-    present in source : yes

##### MessageI : Suspected Missing Footer tag

-    code : **SuspectedMissingFootertag** 
-    status: Pre-Qualified (NMI-Failed)
-    parameter : none
-    present in source : no

### Analysis

#### Not Applicable

if the `<!DOCTYPE>` tags is not `<!DOCTYPE html>` (**Test1** is false)

#### Failed

At least one of tests **Test5** or **Test6** is true

At least one of this cases :
-    if **Test2** is true and **Set2** or **Set3** are not empty
-    if **Test4** is true and **Set4** or **Set5** are not empty
-    if **Test7** is true and **Set6** or **Set7** are not empty

#### Passed

If **Test1** is true and all tests **Test2**, **Test3**, **Test4**, **Test5**, **Test6** and **Test7**  are false

#### Pre-Qualified

In all other case

## Diagrammes

![](https://raw.githubusercontent.com/Tanaguru/RGAA3-2016/master/docs/Diagrammes/Test8-10-2.png?token=AI6sAz_lihDvdS6W-NtN_O7rIBgrBXmVks5ZHFlvwA%3D%3D)

## RGAA 3 reference

https://github.com/Tanaguru/Tanaguru-rules-RGAA-3-doc/blob/master/docs/Rule-9-2-1.md

### Update

Add the test

### Notes

HTML5 doctype is NOT case-sensitive:
[http://www.w3.org/TR/html5/syntax.html#the-doctype](http://www.w3.org/TR/html5/syntax.html#the-doctype "http://www.w3.org/TR/html5/syntax.html#the-doctype")
