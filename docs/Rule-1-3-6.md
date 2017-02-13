# Rule 1.3.6

## Summary

This test consists in detecting informative object images and thus defining the applicability of the test.

Human check will be then needed to determine whether an alternative is present and is relevant.

## Business description

### Criterion

[1.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-1-3)

###Test

[1.3.6](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-1-3-6)

### Description

Chaque image embarqu&eacute;e (balise `embed` avec l'attribut `type="image/..."`) porteuse d'information v&eacute;rifie-t-elle une de ces conditions (hors <a href="http://references.modernisation.gouv.fr/rgaa/cas-particuliers.html#cp-1-3" title="Cas particuliers pour le crit&egrave;re 1.3">cas particuliers</a>) ? 
 
 * L'image embarqu&eacute;e est imm&eacute;diatement suivie d'un lien adjacent permettant d'afficher une page ou un passage de texte contenant une alternative pertinente. 
 * Un m&eacute;canisme permet &agrave; l'utilisateur de remplacer l'image embarqu&eacute;e par un texte alternatif pertinent 
 * Un m&eacute;canisme permet &agrave; l'utilisateur de remplacer l'image embarqu&eacute;e par une image poss&eacute;dant une alternative pertinente. 


### Level

**A**

## Technical description

### Scope

**Page**

### Decision level

**Semi-Decidable**

## Algorithm

### Selection

##### Set1

All the `<embed>` tags of the page not within a link and with a `"type"` attribute that starts with "image/..."  not identified as captcha (see Notes about captcha detection)  (css selector : embed[type^=image]:not(a embed)) and the `"role"` attribute is missing.

#### Set2

All the elements of **Set2** identified as informative image by marker usage (see Notes for details about detection through marker)

#### Set3

All the elements of **Set1** identified neither as informative image, nor as decorative image by marker usage (see Notes for details about detection through marker)

### Process

#### Test1

For each element of **Set2**, raise a MessageA.

#### Test2

For each element of **Set3**, check that the aria-hidden attribute is missing 

For each element return true-result of **Test2**, raise a MessageB.

##### MessageA : Check the presence of an alternative mechanism for information image

-    code : **CheckPresenceOfAlternativeMechanismForInformativeImage** 
-    status: Pre-Qualified (NMI-Passed)
-    parameter : text, `"src"` attribute, tag name, snippet
-    present in source : yes

##### MessageB : Check nature of image and the presence of an alternative mechanism

-    code : **CheckNatureOfImageAndPresenceOfAlternativeMechanism** 
-    status: Pre-Qualified (NMI-Neutral)
-    parameter : text, `"src"` attribute, tag name, snippet
-    present in source : yes

#### Rules remark

 * CheckPresenceOfAlternativeMechanismForInformativeImage (fr): V&eacute;rifier pour images porteuses d'information suivantes s'il existe un m&eacute;chanisme alternatif pour avoir acc&egrave;s à l'information :
 * CheckPresenceOfAlternativeMechanismForInformativeImage (en): The following images have a not pertinent <code>alt</code> attribute, please check they convey information and the pertinence of the alternative:

 * CheckNatureOfImageAndPresenceOfAlternativeMechanism (fr): Si les images suivantes sont porteuses d&#39;information, v&eacute;rifier la pertinence de leur attribut <code>alt</code> : 
 * CheckNatureOfImageAndPresenceOfAlternativeMechanism (en): If the following images convey information, please check the pertinence of their <code>alt</code> attribute :

### Accede Web guidelines

 * Rgaa32016-1-3-6-Accedeweb-EDIT-4-2

### Analysis

#### Not Applicable 

The page has no embedded image (**Set1** is empty)

All elements not indentified as decorative image or informative image and have an alternative (All elements return false-result of **Test2**)

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
