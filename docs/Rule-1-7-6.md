# Rule 1.7.6

## Summary

This test consists in detecting informative canvas images and thus defining the applicability of the test.

Human check will be then needed to determine whether the detected elements provide a detailed description.

## Business description

### Criterion

[1.7](http://references.modernisation.gouv.fr/referentiel-technique-0#crit-1-7)

###Test

[1.7.6](http://references.modernisation.gouv.fr/referentiel-technique-0#test-1-7-6)

### Description

Chaque image bitmap (balise `canvas`) ayant une description d&eacute;taill&eacute;e v&eacute;rifie-t-elle une de ces conditions ? 
 
 * La description d&eacute;taill&eacute;e adjacente &agrave; l'image bitmap est pertinente 
 * La description d&eacute;taill&eacute;e contenue entre `<canvas>` et `</canvas>` est pertinente 
 * La description d&eacute;taill&eacute;e via un lien adjacent est pertinente 


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

All the `<canvas>` tags of the page not within a link and not identified as captcha (see Notes about captcha detection)  (css selector : canvas:not(a canvas))

#### Set2

All the elements of **Set1** identified as informative image by marker usage (see Notes for details about detection through marker)

#### Set3

All the elements of **Set1** identified neither as informative image, nor as decorative image by marker usage (see Notes for details about detection through marker)

### Process

#### Test1

For each element of **Set2**, raise a MessageA.

#### Test2

For each element of **Set3**, raise a MessageB.

##### MessageA : Check detailed description of informative images

-    code : **CheckDescriptionPertinenceOfInformativeImage** 
-    status: Pre-Qualified
-    parameter : text, tag name, snippet
-    present in source : yes

##### MessageB : Check nature of image and detailed description 

-    code : **CheckNatureOfImageAndDescriptionPertinence** 
-    status: Pre-Qualified
-    parameter : text, tag name, snippet
-    present in source : yes

### Accede Web guidelines

 * http://www.accede-web.com/notices/html-css-javascript/13-recommandations-additionnelles/alternative-contenu-multimedia-video-audio-object/

### Analysis

#### Not Applicable 

The page has no canvas image (**Set1** is empty)

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
