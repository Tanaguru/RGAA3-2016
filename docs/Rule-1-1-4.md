# Rule 1.1.4

## Summary

This test consists in checking whether each `<area>` of a server image map is doubled by a link in the page.

## Business description

### Criterion

[1.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-1-1)

###Test

[1.1.4](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-1-1-4)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#zone-cliquable">zone cliquable</a> d'une <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#image-ractive">image r&eacute;active cot&eacute; serveur</a> est-t-elle doubl&eacute;e d'un lien dans la page ?

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

All the `<img>` tags with an `"ismap"` attribute and all the `<input>` tags with a `"type"` attribute equals to "image" and an `"ismap"` attribute (css selector : `img[ismap],input[type=image][ismap]`)

#### Set2

Check the presence on server side of the file "ismap.map". List all urls in this file.

### Process

#### Tests

##### Test1

if **Set1** and **Set2** are not null, For each element of **Set2**, check if a link with a same url is present in the page.

For each element return false-result, raise the MessageA.

##### Test2

if **Set2** is null, for each element of **Set1**, produce a MessageA

#### Messages

##### MessageA : Check a link is associated with the server-sided image map

-    code : CheckALinkIsAssociatedWithTheServerSidedImageMap
-    status: Pre-qualified (NMI or warning)
-    case : For each element of Set1
-    parameter : `"alt"` attribute, `"src"` attribute, `"url"` of the ismap.map file, tag name
-    present in source : yes

#### Rules remark

 * CheckALinkIsAssociatedWithTheServerSidedImageMap (en): Please check a link is associated with the following server-sided map images : 
 * CheckALinkIsAssociatedWithTheServerSidedImageMap (fr): V&eacute;rifier qu'un lien est associ&eacute; avec les images r&eacute;actives cot&eacute; serveur suivantes :  

### Analysis

#### Not Applicable

The page has no `<img>` tag with a `"ismap"` attribute (**Set1** is empty)

#### Passed

All the link in the ismap.map file have an alternative link in the page (all the element of the **Test1** return true-result)

#### Pre-qualified

All other case

## Notes

We only detect the elements of the **Set1** to determine whether the test is applicable

## Diagrammes

![](https://raw.githubusercontent.com/Tanaguru/RGAA3-2016/master/docs/Diagrammes/Test1-1-4.png?token=AI6sA1kFWrjWcf74ozPsFwkDusjGd_q1ks5Y-dj7wA%3D%3D)

## RGAA 3 reference

https://github.com/Tanaguru/Tanaguru-rules-RGAA-3-doc/blob/master/docs/Rule-1-1-4.md

### Update

 * Add **Set2** and **Test2**
 * Update **Test1**
