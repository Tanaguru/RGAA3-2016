# Rule 1.1.3

## Summary

This test consists in checking whether each form button is defined with an `"alt"` attribute

## Business description

### Criterion

[1.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-1-1)

### Test

[1.1.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-1-1-3)

### Description

Chaque bouton de formulaire (balise `input` avec l'attribut `type="image"`) a-t-il un attribut `alt` ?

### Level

**A**

## Technical description

### Scope

**page**

### Decision level

**Decidable**

## Algorithm

### Selection

#### Set1

All the `<input>` tags with a `"type"` attribute equals to "image" (css selector : `input[type=image]`)

### Process

#### Test1

For each element of **Set1**, test the presence of an `"alt"` attribute.

For each occurrence of false-result of **Test1**, raise a MessageA

##### MessageA 

-    code : **AltMissing** 
- 	 message (fr) : "L'attribut alt est absent pour les éléments suivants : "
- 	 message (en) : "The alt attribute is missing on the following elements : "
-    status: Failed
-    parameter : `"src"` attribute, tag name, snippet
-    present in source : yes

### Accede Web guidelines

 * http://www.accede-web.com/notices/html-css-javascript/6-images-icones/6-3-balise-img/
 * http://www.accede-web.com/notices/editoriale/4-images/#ancre-02

### Analysis

#### Passed

All the `<input>` tags with a `"type"` attribute equals to "image" of the page have an `"alt"` attribute (**Test1** returns true for all the elements of **Set1**)

#### Failed

At least one `<input>` tag with a `"type"` attribute equals to "image" has no `"alt"` attribute (**Test1** returns failed for at least one element)

#### Not Applicable

The page has no `<input>` tag with a `"type"` attribute equals to "image" tag (**Set1** is empty)
