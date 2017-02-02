# Rule 1.2.2

## Summary

This test consists in checking whether the `alt` attribute of non clickable area is empty.

## Business description

### Criterion

[1.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-1-2)

###Test

[1.2.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-1-2-2)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#zone-non-cliquable">zone non cliquable</a> (balise `area` sans attribut `href`) <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#image-de-dcoration">de d&eacute;coration</a>, et ayant un attribut alt, v&eacute;rifie-t-elle ces conditions ? 
 
 * le contenu de l'attribut `alt` est vide (`alt=""`) ;
 * la zone cliquable ne poss&egrave;de pas d'attribut `title` ;
 * la balise `area` est dépourvue de rôle, propriété ou état ARIA visant à labelliser l’image (`aria-label`, `aria-describedby`, `aria-labelledby` par exemple).

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

All the `<area>` tags, defined within a `<map>` tag whose the `"id"` attribute corresponds to the `"usemap"` attribute of an `<img>` tag, and not identified as captcha (see Notes about captcha detection)

#### Set2

All the elements of **Set1** identified as decorative image by marker usage (see Notes for details about detection through marker)

#### Set3

All the elements of **Set1** identified neither as informative image, nor as decorative image by marker usage (see Notes for details about detection through marker)

### Process

#### Tests

##### Test1 

For each element of **Set2** (decorative `<area>` identified by a html marker), check that the content of the `"alt"` attribute is empty. 

For each element returning false in **Test1**, raise a MessageA.

##### Test2 

For each element of **Set2** (decorative `<area>` identified by a html marker), check that the `"title"` attribute is missing. 

For each element returning false in **Test2**, raise a MessageB. 

##### Test3

For each element of **Set3** (`<area>` tags not identified as decorative image), check that the content of the `"alt"` attribute empty. 

For each element returning true in **Test3**, raise a MessageD.

##### Test4 

For each element of **Set3** (decorative `<area>` not identified by a html marker), check that the `"title"` attribute is missing. 

For each element returning true in **Test4**, raise a MessageD.

##### Test5 

For each element of **Set2** (decorative `<area>` identified by a html marker), check that the `"aria-label"`, `"aria-describedby"` and `"aria-labelledby"` attributes are missing. 

For each element returning false in **Test5**, raise a MessageE. 

##### Test6 

For each element of **Set3** (decorative `<area>` not identified by a html marker), check that the `"aria-label"`, `"aria-describedby"` and `"aria-labelledby"` attributes are missing. 

For each element returning true in **Test6**, raise a MessageD.

#### Messages

##### MessageA : Decorative image with not empty alternative

-    code : DecorativeElementWithNotEmptyAltAttribute
-    status: Failed
-    parameter : `"alt"` attribute, `"title"` attribute, Snippet
-    present in source : yes

##### MessageB : Decorative image with a title attribute

-    code : DecorativeElementWithTitleAttribute
-    status: Failed
-    parameter : `"alt"` attribute, `"title"` attribute, Snippet
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

 * Rgaa32016-1-2-2-Accedeweb-EDIT-4-1

### Analysis

#### Not Applicable

The page has no `<area>` tag with an `"alt"` attribute (**Set1** is empty)

All the `<area>` of the page not identified as decorative image and have an alternative not empty (All element return false-result in **Test3**, **Test4** OR **Test6**)

#### Failed

At least one `<area>` identified as decorative has a not empty alternative (**Test1**, **Test2** OR **Test5** returns false for at least one element)

#### Passed

All the `<area>` of the page are identified as decorative and have an empty alternative (**Set3** is empty and **Test1**, **Test2** AND **Test5** returns true for all element)

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
