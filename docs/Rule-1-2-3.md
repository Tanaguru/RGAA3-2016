# Rule 1.2.3

## Summary

This test consists in checking whether the textual alternative of each decorative object image is empty.

## Business description

### Criterion

[1.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-1-2)

### Test

[1.2.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-1-2-3)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#image-objet">image objet</a> (balise `object` avec l'attribut `type="image/..."`) <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#image-de-dcoration">de décoration</a>, sans <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#lgende-dimage">l&eacute;gende</a>, vérifie-t-elle ces conditions ? 

*  La balise `object` possède un attribut `aria-hidden="true"` ;
*  L’alternative textuelle entre `<object>` et `</object>` est vide ;
*  La balise `object` ou l’un de ses enfants est dépourvue de rôle, propriété ou état ARIA visant à labelliser l’image (`aria-label`, `aria-describedby`, `aria-labelledby` par exemple).

### Level

**A**

## Technical description

### Scope

**page**

### Decision level

**Semi-Decidable**

## Algorithm

### Selection

#### Set1

All the `<object>` tags with a `"type"` attribute equals to "image", not within a link and not identified as captcha (see Notes about captcha detection) (css selector : `object[type^=image]:not(a object)`) and the `"role"` attribute that value is different than "img" or "presentation" is missing.

#### Set2

All the elements of **Set1** identified as decorative image by marker usage (see Notes for details about detection through marker)

#### Set3

All the elements of **Set1** identified neither as informative image, nor as decorative image by marker usage (see Notes for details about detection through marker)

### Process

#### Tests

##### Test1

For each element of **Set2**, Check the presence of text between `<object>` tags.

For each occurrence of true-result of **Test1**, raise a MessageA

##### Test2

For each element of **Set3**, Check the presence of text between `<object>` tags.

For each occurrence of false-result of **Test2**, raise a MessageC

##### Test3

For each element of **Set2**, Check the presence of an `aria-hidden` attribute with `true` value.

For each occurrence of false-result of **Test3**, raise a MessageD

##### Test4

For each element of **Set3**, Check the presence of an `aria-hidden` attribute with `true` value.

For each occurrence of true-result of **Test4**, raise a MessageC

##### Test5 

For each element of **Set2** (decorative `<object>` identified by a html marker), check that the `"aria-label"`, `"aria-describedby"` and `"aria-labelledby"` attributes are missing on the tag or least one its children. 

For each element returning false-result in **Test5**, raise a MessageE. 

##### Test6 

For each element of **Set3** (decorative `<object>` not identified by a html marker), check that the `"aria-label"`, `"aria-describedby"` and `"aria-labelledby"` attributes are missing on the tag or least one its children. 

For each element returning true in **Test6**, raise a MessageC.

#### Messages

##### MessageA : Decorative image with not empty alternative

-    code : DecorativeElementWithNotEmptyAltAttribute
-    status: Failed
-    parameter : `"data"` attribute, text, Snippet
-    present in source : yes

##### MessageC : Check the nature of the image with a empty alternative

-    code : CheckNatureOfElementWithEmptyAlternative
-    status: Pre-qualified (NMI-Neutral)
-    parameter : text, Snippet
-    present in source : yes

##### MessageD : Decorative image without aria-hidden attribute

-    code : DecorativeElementWithoutAriaHiddenAttribute
-    status: Failed
-    parameter : `"data"` attribute, text, Snippet
-    present in source : yes

##### MessageE : Decorative image with an Aria attribute

-    code : DecorativeElementWithAriaAttribute
-    status: Failed
-    parameter : `"aria-label"` attribute, `"aria-describedby"` attribute, `"aria-labelledby"` attribute, Snippet
-    present in source : yes

#### Rules remark

 * DecorativeElementWithNotEmptyAltAttribute (fr): Les images de d&eacute;coration suivantes ont un attribut <code>alt</code> non vide :
 * DecorativeElementWithNotEmptyAltAttribute (en): The following decorative images have a not empty <code>alt</code> attribute :

 * CheckNatureOfElementWithEmptyAlternative (fr): Les images suivantes n'ont pas d'alternative, v&eacute;rifier que ce sont bien des images de d&eacute;coration :
 * CheckNatureOfElementWithEmptyAltAttribute (en): The following images have no alternative, please check they are decorative:

 * DecorativeElementWithoutAriaHiddenAttribute (fr): Les images de d&eacute;coration suivantes n'ont pas d'attribut <code>aria-hidden="true"</code> :
 * DecorativeElementWithoutAriaHiddenAttribute (en): The following decorative images have no <code>aria-hidden="true"</code> attribute:

 * DecorativeElementWithAriaAttribute (fr): Les images de d&eacute;coration suivantes ont une ou plusieurs propri&eacute;t&eacute; <code>ARIA</code> :
 * DecorativeElementWithAriaAttribute (en): The following decorative images have one or more <code>ARIA</code> properties:

### Accede Web guidelines

 * Rgaa32016-1-2-3-Accedeweb-EDIT-4-1

### Analysis

#### Passed

All the `<object type="image">` tags are identified as decorative and don't have text between `<object>` tags and have aria-hidden attribute with true value and don't have other aria attribute (**Test1** returns false for all elements and **Test3** and **Test5** returns true for all elements)

All the `<object type="image">` of the page not identified as decorative image and have an alternative not empty (All element return false-result in **Test2**, **Test4** OR **Test6**)

#### Failed

At least one `<object type="image>` identified as decorative have text between `<object>` tags or not have aria-hidden attribute or have an aria attribute (**Test1** returns true at least one element or **Test3** or **Test5** returns false at least one element)

#### Not Applicable

The page has no `<object type="image>` tag (**Set1** is empty)

#### Pre-qualified

In all other cases

## Notes

### Markers 

**Informative images** markers are set through the **INFORMATIVE_IMAGE_MARKER** parameter.

**Decorative images** markers are set through the **DECORATIVE_IMAGE_MARKER** parameter.

The value(s) passed as marker(s) will be checked against the following attributes:

- `class`
- `id`
- `role`

### Captcha detection

An element is identified as a CAPTCHA when the "captcha" occurrence is found :

- on one attribute of the element
- or within the text of the element
- or on one attribute of one parent of the element
- or within the text of one parent of the element
- or on one attribute of a sibling of the element
- or within the text of a sibling of the element
