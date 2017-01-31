# Rule 1.1.2

## Summary

This test consists in checking whether each `<area>` of an image map is defined with an `"alt"` attribute

## Business description

### Criterion

[1.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-1-1)

### Test

[1.1.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-1-1-2)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#zone-dune-image-ractive">zone</a> (balise `area`) d'une <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#image-ractive">image r&eacute;active</a> a-t-elle un attribut `alt` ?

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

All the `<area>` tags, defined within a `<map>` tag whose the `"id"` attribute corresponds to the `"usemap"` attribute of an `<img>` tag.

### Process

#### Test1

For each element of **Set1**, test the presence of an `"alt"` attribute. For each occurrence of false-result of **Test1**, raise a MessageA

##### MessageA : Missing Alt attribute

-    code : **AltMissing** 
- 	 message (fr) : "L'attribut alt est absent pour les éléments suivants : "
- 	 message (en) : "The alt attribute is missing on the following elements : "
-    status: Failed
-    parameter : `"href"` attribute, tag name, snippet
-    present in source : yes

### Accede Web guidelines

 * http://www.accede-web.com/notices/html-css-javascript/13-recommandations-additionnelles/alt-image-mappee-area/
 * http://www.accede-web.com/notices/editoriale/4-images/#ancre-01
 * http://www.accede-web.com/notices/editoriale/4-images/#ancre-02

### Analysis

#### Passed

All the `<area>` tags of the page, correctly associated with an image, have an `"alt"` attribute (**Test1** returns true for all the elements of **Set1**)

#### Failed

At least one `<area>` tag, correctly associated with an image, has no `"alt"` attribute (**Test1** returns failed for at least one element)

#### Not Applicable

The page has no `<area>` tag, correctly associated with an image (**Set1** is empty)
