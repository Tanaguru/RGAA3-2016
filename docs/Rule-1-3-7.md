# Rule 1.3.5

## Summary

This test consists in detecting informative embed images and thus defining the applicability of the test.

Human check will be then needed to determine whether an alternative is present and is relevant.

## Business description

### Criterion

[1.3](http://references.modernisation.gouv.fr/referentiel-technique-0#crit-1-3)

###Test

[1.3.7](http://references.modernisation.gouv.fr/referentiel-technique-0#test-1-3-7)

### Description

Chaque image objet (balise `embed` avec l'attribut `type="image/..."`) porteuse d'information, qui utilise une propri&eacute;t&eacute; aria-lebel, aria-labelledby ou un attribut title, v&eacute;rifie-t-elle une de ces conditions(hors <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#cpCrit1-3" title="Cas particuliers pour le crit&egrave;re 1.3">cas particuliers</a>) ? 
 
 * S'il est présent, le contenu de l'attribut title est identique au contenu de l'attribut aria-label ; 
 * S'il est présent, le contenu de l'attribut title est identique au passage de texte lié par la propriété aria-labelledby.

### Level

**A**

## Technical description

### Scope

**Page**

### Decision level

**Decidable**

## Algorithm

### Selection

##### Set1

All the `<embed>` tags with a `"type"` attribute that starts with "image/...", not within a link and not identified as captcha (see Notes about captcha detection)  (css selector : embed[type^=image]:not(a embed))

### Process

#### Test

##### Test1

For each element of **Set1**, check the presence of the `"title"` attribute and the `"aria-label"` or the `"aria-labelledby"` attribute.

##### Test2

For each element return true-result of **Test1**, check whether the content of the `"title"` attribute is equal to the content of the `"aria-label"` attribute or the content associated with the `"aria-labelledby"` attribute.

For each occurrence of true-result of **Test2**, raise a MessageA.

For each occurrence of false-result of **Test2**, raise a MessageB.

#### Messages

##### MessageA : Check nature of image and the presence of an alternative mechanism

-    code : **CheckNatureOfImageAndPresenceOfAlternativeMechanism** 
-    status: Pre-Qualified (NMI-Passed)
-    parameter : text, `"src"` attribute, tag name, snippet
-    present in source : yes

##### MessageB : Detect the title not equal to the aria-label or aria-labelledby

-    code : **DetectTitleNotEqualAriaLabelAriaLabelledby** 
-    status: failed
-    parameter : text, `"src"` attribute, tag name, snippet
-    present in source : yes

### Analysis

#### Failed

The page has least one embed image that the title is different than the aria-label or the aria-labelledby (at least one element of **Test2** return false-result)

#### Pre-Qualified

The page has embed image that the title is equal than the aria-label or the aria-labelledby (all the element return true-result **Test2**)

#### Not Applicable 

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
