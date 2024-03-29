# Rule 1.3.9

## Summary

This test consists in detecting informative svg images with a `<desc>` child tag or a `"aria-label"` attribute and thus defining the applicability of the test.

Human check will be then needed to determine whether the alternative is well rendered by assistive technologies.

## Business description

### Criterion

[1.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-1-3)

###Test

[1.3.9](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-1-3-9)

### Description

Pour chaque image vectorielle porteuse d'information (balise `svg`) et poss&eacute;dant une alternative, cette alternative est-elle <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#correctement-restitue-par-les-technologies-dassistance">correctement restitu&eacute;e</a> par les technologies d'assistance ?

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

All the `<svg>` tags of the page not within a link, not identified as captcha and with a not empty `<desc>` child tag (see Notes about captcha detection) (svg:not(a svg):has(desc:not(:matchesOwn(^\\s*$))) and the `"role"` attribute is missing.

#### Set2

All the `<svg>` tags of the page not within a link, not identified as captcha and with a not empty `"aria-label"` attribute (see Notes about captcha detection) (svg[aria-label]:not([aria-label~=^\\s*$]:not(a svg)) and the `"role"` attribute is missing.

#### Set3

All the elements of **Set1** identified as informative image by marker usage (see Notes for details about detection through marker)

#### Set4

All the elements of **Set2** identified as informative image by marker usage (see Notes for details about detection through marker)

#### Set5

All the elements of **Set1** identified neither as informative image, nor as decorative image by marker usage (see Notes for details about detection through marker)

#### Set6

All the elements of **Set2** identified neither as informative image, nor as decorative image by marker usage (see Notes for details about detection through marker)

### Process

#### Test1

For each element of **Set2** and **Set3**, raise a MessageA.

#### Test2

For each element of **Set4** and **Set5**, raise a MessageB.

##### MessageA : Check the restitution by assistive technologies of the alternative of informative images

-    code : **CheckAtRestitutionOfAlternativeOfInformativeSvgImage** 
-    status: Pre-Qualified
-    parameter : `"role"` attribute, `"aria-label"` attribute, `"title"` attribute, tag name, snippet
-    present in source : yes

##### MessageB : Check nature of image and the restitution by assistive technologies of their alternative

-    code : **CheckNatureOfSvgImageAndAtRestitutionOfAlternative** 
-    status: Pre-Qualified
-    parameter : `"role"` attribute, `"aria-label"` attribute, `"title"` attribute, tag name, snippet
-    present in source : yes

#### Rules remark

 * CheckAtRestitutionOfAlternativeOfInformativeSvgImage (fr): Veuillez v&eacute;rifier que l&#39;alternative des images vectorielles porteuses d&#39;information suivantes est correctement restitu&eacute;e par les technologies d&#39;assistance : 
 * CheckAtRestitutionOfAlternativeOfInformativeSvgImage (en): The following vector images that convey information have been detected, please check their alternative is correctly rendered by assistive technologies :

 * CheckNatureOfSvgImageAndAtRestitutionOfAlternative (fr): Si les images vectorielles suivantes sont porteuses d&#39;information, veuillez v&eacute;rifier que leur alternative est correctement restitu&eacute;e par les technologies d&#39;assistance : 
 * CheckNatureOfSvgImageAndAtRestitutionOfAlternative (en): If the following vector images convey information, please check their alternative is correctly rendered by assistive technologies :

### Analysis

#### Not Applicable 

The page has no svg image with a not empty `<desc>` child tag or a not empty `"aria-label"` attribute(**Set1** and **Set2** are empty)

#### Pre-Qualified

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
