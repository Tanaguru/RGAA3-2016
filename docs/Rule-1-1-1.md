# Rule 1.1.1

## Summary

This test consists in checking whether each `<img>` tag is defined with an `"alt"` attribute.

## Business description

### Criterion

[1.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-1-1)

###Test

[1.1.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-1-1-1)

### Description

Chaque image (balise `img`) a-t-elle un attribut `alt` ?

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

All the `<img>` tags (css selector : `img`)

### Process

#### Tests

##### Test1

For each element of **Set1**, test the presence of the `"alt"` attribute.

For each occurrence of false-result of **Test1**, raise a MessageA

#### Messages

##### MessageA : Missing Alt attribute

-    code : **AltMissing** 
-    status: Failed
-    parameter : `"src"` attribute, tag name, snippet
-    present in source : yes

#### Rules remark

 * AltMissing (en): The <code>alt</code> attribute is missing on the following elements :
 * AltMissing (fr): L&#39;attribut <code>alt</code> est absent pour les &eacute;l&eacute;ments suivants :

### Accede Web guidelines

 * Rgaa32016-1-1-1-Accedeweb-HTML-6-3
 * Rgaa32016-1-1-1-Accedeweb-EDIT-4-1
 * Rgaa32016-1-1-1-Accedeweb-EDIT-4-2

### Analysis

#### Passed

All the `<img>` tags of the page have an `"alt"` attribute (**Test1** returns true for all the elements of **Set1**)

#### Failed

At least one `<img>` tag has no `"alt"` attribute (**Test1** returns failed for at least one element)

#### Not Applicable

The page has no `<img>` tag (**Set1** is empty)

## Diagrammes

![](https://raw.githubusercontent.com/Tanaguru/RGAA3-2016/master/docs/Diagrammes/Test1-1-1.png?token=AI6sA6seL_G8Cales6bwE5OeJCu171T4ks5Y-cKmwA%3D%3D)

## RGAA 3 reference

https://github.com/Tanaguru/Tanaguru-rules-RGAA-3-doc/blob/master/docs/Rule-1-1-1.md

### Update

Add Accede Web guidelines
