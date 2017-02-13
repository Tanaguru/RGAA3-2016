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

For each element of **Set1**, test the presence of an `"alt"` attribute. 

For each occurrence of false-result of **Test1**, raise a MessageA

##### Test2

For each element of **Set1**, test the presence of a `"role"` attribute that value is different than "img" or "presentation".

For each occurrence of true-result of **Test2**, raise a MessageB

##### MessageA : Missing Alt attribute

-    code : **AltMissing** 
-    status: Failed
-    parameter : `"href"` attribute, tag name, snippet
-    present in source : yes

##### MessageB : Check manually that use Aria role is relevant

-    code : **CheckManuallyThatUseAriaRoleRelevant** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : `"src"` attribute, tag name, snippet
-    present in source : yes

#### Rules remark

 * AltMissing (en): The <code>alt</code> attribute is missing on the following elements :
 * AltMissing (fr): L&#39;attribut <code>alt</code> est absent pour les &eacute;l&eacute;ments suivants : 

 * CheckManuallyThatUseAriaRoleRelevant (en): Check manually that use Aria role on these elements is relevant:
 * CheckManuallyThatUseAriaRoleRelevant (fr): V&eacute;rifier manuellement qu'utiliser un role Aria sur ces &eacute;l&eacute;ments est pertinent :

### Accede Web guidelines

 * Rgaa32016-1-1-2-Accedeweb-HTML-13
 * Rgaa32016-1-1-2-Accedeweb-EDIT-4-1
 * Rgaa32016-1-1-2-Accedeweb-EDIT-4-2

### Analysis

#### Passed

All the `<area>` tags of the page, correctly associated with an image, have an `"alt"` attribute (**Test1** returns true for all the elements of **Set1**)

#### Failed

At least one `<area>` tag, correctly associated with an image, has no `"alt"` attribute (**Test1** returns failed for at least one element)

#### Pre-qualified

All the `<area>` tags of the page have an `"role"` attribute that value is different than "img" or "presentation" (**Test2** returns true for all the elements of **Set1**)

#### Not Applicable

The page has no `<area>` tag, correctly associated with an image (**Set1** is empty)
