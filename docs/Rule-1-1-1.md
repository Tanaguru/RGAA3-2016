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

#### Test1

For each element of **Set1**, test the presence of the `"alt"` attribute.

For each occurrence of false-result of **Test1**, raise a MessageA

##### MessageA : Missing Alt attribute

-    code : **AltMissing** 
- 	 message (fr) : "L'attribut alt est absent pour les éléments suivants : "
- 	 message (en) : "The alt attribute is missing on the following elements : "
-    status: Failed
-    parameter : `"src"` attribute, tag name, snippet
-    present in source : yes

### Accede Web guidelines

 * http://www.accede-web.com/notices/html-css-javascript/6-images-icones/6-3-balise-img/
 * http://www.accede-web.com/notices/editoriale/4-images/#ancre-01
 * http://www.accede-web.com/notices/editoriale/4-images/#ancre-02

### Analysis

#### Passed

All the `<img>` tags of the page have an `"alt"` attribute (**Test1** returns true for all the elements of **Set1**)

#### Failed

At least one `<img>` tag has no `"alt"` attribute (**Test1** returns failed for at least one element)

#### Not Applicable

The page has no `<img>` tag (**Set1** is empty)
