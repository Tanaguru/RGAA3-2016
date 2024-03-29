# Rule 1.6.8

## Summary

This test consists in detecting informative canvas images with an alternative text and thus defining the applicability of the test.

Human check will be then needed to determine whether the detailed description is well rendered by assistive technologies.

## Business description

### Criterion

[1.6](http://references.modernisation.gouv.fr/referentiel-technique-0#crit-1-6)

###Test

[1.6.8](http://references.modernisation.gouv.fr/referentiel-technique-0#test-1-6-8)

### Description

Pour chaque image bitmap (balise `canvas`) qui impl&eacute;mente une r&eacute;f&eacute;rence &agrave; une <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#mDescDetaillee">description d&eacute;taill&eacute;e</a> adjacente, cette r&eacute;f&eacute;rence est-elle <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#mRestitutionCorrecte">correctement restitu&eacute;e</a> par les technologies d'assistance ?

### Level

**A**

## Technical description

### Scope

**Page**

### Decision level

**Semi-decidable**

## Algorithm

### Selection

#### Set1

All the `<canvas>` tags of the page not within a link, not identified as captcha and with a not empty text (see Notes about captcha detection) (canvas:not(a canvas):not(:matchesOwn(^\\s*$)))

#### Set2

All the elements of **Set1** identified as informative image by marker usage (see Notes for details about detection through marker)

#### Set3

All the elements of **Set1** identified neither as informative image, nor as decorative image by marker usage (see Notes for details about detection through marker)

### Process

#### Test1

For each element of **Set2**, raise a MessageA.

#### Test2

For each element of **Set3**, raise a MessageB.

##### MessageA : Check the restitution by assistive technologies of the description of informative images

-    code : **CheckAtRestitutionOfDescriptionOfInformativeImage** 
-    status: Pre-Qualified
-    parameter : text, tag name, snippet
-    present in source : yes

##### MessageB : Check nature of image and the restitution by assistive technologies of their description

-    code : **CheckNatureOfImageAndAtRestitutionOfDescription** 
-    status: Pre-Qualified
-    parameter : text, tag name, snippet
-    present in source : yes

### Accede Web guidelines

 * http://www.accede-web.com/notices/editoriale/4-images/#ancre-04
 * http://www.accede-web.com/notices/editoriale/8-contenus-riches-multimedias/8-1-description-contenus-riches-graphiques-cartographies-plans-flash/

### Analysis

#### Not Applicable 

The page has no canvas image with a not empty text (**Set1** is empty)

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
