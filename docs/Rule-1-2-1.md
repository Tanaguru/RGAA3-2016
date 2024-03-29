# Rule 1.2.1

## Summary

This test consists in checking whether the `alt` attribute of each decorative image is empty.

## Business description

### Criterion

[1.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-1-2)

### Test

[1.2.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-1-2-1)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#image-de-dcoration">image de d&eacute;coration</a> (balise `img`) sans <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#lgende-dimage">l&eacute;gende</a> et ayant un attribut `alt` v&eacute;rifie-t-elle ces conditions : 
 
 * le contenu de l'attribut alt est vide (`alt=""`) ;
 * l'image de d&eacute;coration ne poss&egrave;de pas d'attribut `title` ;
 * la balise img est dépourvue de role, propriété ou état ARIA visant à labelliser l'image (`aria-label`, `aria-describedby`, `aria-labelledby` par exemple).

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

All the `<img>` tags of the page not within a link, without `<longdesc>` attribute and not identified as captcha (see Notes about captcha detection) (css selector : `img:not(a img):not([longdesc])`) and the `"role"` attribute that value is different than "img" or "presentation" is missing.

#### Set2

All the elements of **Set1** identified as decorative image by marker usage (see Notes for details about detection through marker)

#### Set3

All the elements of **Set1** identified neither as informative image, nor as decorative image by marker usage (see Notes for details about detection through marker)

### Process

#### Tests

##### Test1 

For each element of **Set2** (decorative `<img>` identified by a html marker), check that the content of the `"alt"` attribute is empty. 

For each element returning false in **Test1**, raise a MessageA.

##### Test2 

For each element of **Set2** (decorative `<img>` identified by a html marker), check that the `"title"` attribute is missing. 

For each element returning false in **Test2**, raise a MessageB. 

##### Test3

For each element of **Set3** (`<img>` tags not identified as decorative image), check that the content of the `"alt"` attribute empty. 

For each element returning true in **Test3**, raise a MessageD.

##### Test4 

For each element of **Set3** (decorative `<img>` identified by a html marker), check that the `"title"` attribute is missing. 

For each element returning true in **Test4**, raise a MessageD.

##### Test5 

For each element of **Set2** (decorative `<img>` identified by a html marker), check that the `"aria-label"`, `"aria-describedby"` and `"aria-labelledby"` attributes are missing. 

For each element returning false in **Test5**, raise a MessageE. 

##### Test6 

For each element of **Set3** (decorative `<img>` identified by a html marker), check that the `"aria-label"`, `"aria-describedby"` and `"aria-labelledby"` attributes are missing. 

For each element returning true in **Test6**, raise a MessageD.

#### Messages

##### MessageA : Decorative image with not empty alternative

-    code : DecorativeElementWithNotEmptyAltAttribute
-    status: Failed
-    parameter : `"alt"` attribute, `"title"` attribute, `"src"` attribute, Snippet
-    present in source : yes

##### MessageB : Decorative image with a title attribute

-    code : DecorativeElementWithTitleAttribute
-    status: Failed
-    parameter : `"alt"` attribute, `"title"` attribute, `"src"` attribute, Snippet
-    present in source : yes

##### MessageD : Check the nature of the image with a empty alternative

-    code : CheckNatureOfElementWithEmptyAltAttribute
-    status: Pre-qualified (NMI-Neutral)
-    parameter : Snippet
-    present in source : yes

##### MessageE : Decorative image with an Aria attribute

-    code : DecorativeElementWithAriaAttribute
-    status: Failed
-    parameter : `"alt"` attribute, `"aria-label"` attribute, `"aria-describedby"` attribute, `"aria-labelledby"` attribute, `"src"` attribute, Snippet
-    present in source : yes

#### Rules remark

 * DecorativeElementWithNotEmptyAltAttribute (fr): Les images de d&eacute;coration suivantes ont un attribut <code>alt</code> non vide :
 * DecorativeElementWithNotEmptyAltAttribute (en): The following decorative images have a not empty <code>alt</code> attribute :

 * DecorativeElementWithTitleAttribute (fr): Les images de d&eacute;coration suivantes ont un attribut <code>title</code> :
 * DecorativeElementWithTitleAttribute (en): The following decorative images have a <code>title</code> attribute:

 * CheckNatureOfElementWithEmptyAltAttribute (fr): Les images suivantes ont un attribut <code>alt</code> vide et aucun attribut <code>title</code>, v&eacute;rifier que ce sont bien des images de d&eacute;coration :
 * CheckNatureOfElementWithEmptyAltAttribute (en): The following images have an empty alt and no title attribute , please check they are decorative:

 * DecorativeElementWithAriaAttribute (fr): Les images de d&eacute;coration suivantes ont une ou plusieurs propri&eacute;t&eacute; <code>ARIA</code> :
 * DecorativeElementWithAriaAttribute (en): The following decorative images have one or more <code>ARIA</code> properties:

### Accede Web guidelines

 * Rgaa32016-1-2-1-Accedeweb-HTML-6-3
 * Rgaa32016-1-2-1-Accedeweb-EDIT-4-1

### Analysis

#### Not Applicable

The page has no `<img>` tag with an `"alt"` attribute (**Set1** is empty)

All the `<img>` of the page not identified as decorative image and have an alternative not empty (All element return false-result in **Test3**, **Test4** OR **Test6**)

#### Failed

At least one `<img>` identified as decorative has a not empty alternative (**Test1**, **Test2** OR **Test5** returns false for at least one element)

#### Passed

All the `<img>` of the page are identified as decorative and have an empty alternative (**Set3** is empty and **Test1**, **Test2** AND **Test5** returns true for all element)

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
