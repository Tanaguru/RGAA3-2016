# Rule 1.3.1

## Summary

This test consists in checking whether the `alt` attribute of each image that convey information is pertinent.

## Business description

### Criterion

[1.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-1-3)

###Test

[1.3.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-1-3-1)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#image-porteuse-dinformation">image porteuse d'information</a> (balise `img`) ayant un attribut `alt` v&eacute;rifie-t-elle ces conditions (hors <a href="http://references.modernisation.gouv.fr/rgaa/cas-particuliers.html#cp-1-3" title="Cas particuliers pour le crit&egrave;re 1.3">cas particuliers</a>) ? 
 
 * Le contenu de l'attribut `alt` est pertinent ;
 * S'il est pr&eacute;sent, le contenu de l'attribut `title` est identique au contenu de l'attribut `alt` ;
 * S'il est pr&eacute;sent, le contenu de la propri&eacute;t&eacute; `aria-label` est identique au contenu de l'attribut alt ;
 * S'il est pr&eacute;sent, le contenu du passage de texte lié via la propriété aria-labelledby est identique au contenu de l'attribut alt.

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

All the `<img>` tags of the page not within a link not identified as captcha (see Notes about captcha detection) (css selector : `img:not(a img):not([longdesc])`)

#### Set2

All the elements of **Set1** with a `"longdesc"` attribute or identified as informative image by marker usage (see Notes for details about detection through marker)

#### Set3

All the elements of **Set1** identified neither as informative image, nor as decorative image by marker usage (see Notes for details about detection through marker) and with a not empty alt attribute.

### Process

#### Tests 

##### Test1

For each element of **Set3**, check whether the content of the `"alt"` attribute is not relevant (see Notes for details about relevancy test). 

For each occurrence of true-result of **Test1**, raise a MessageA.

For each occurrence of false-result of **Test1**, raise a MessageB.

##### Test2

For each element of **Set2**, check whether the content of the `"alt"` attribute is identical to the content of the `"title"` attribute.

For each occurrence of false-result of **Test2**, raise a MessageC.

##### Test3

For each element of **Set3**, check whether the content of the `"alt"` attribute is not relevant (see Notes for details about relevancy test). 

For each occurrence of true-result of **Test3**, raise a MessageD.

For each occurrence of false-result of **Test3**, raise a MessageE.

##### Test4

For each element of **Set2**, check whether the content of the `"alt"` attribute is identical to the content of the `"title"` attribute.

For each occurrence of false-result of **Test4**, raise a MessageD.

##### Test5

For each element of **Set1**, if present, check whether the content of the `"aria-label"` attribute is equal to the `"alt"` attribute. 

For each occurrence of false-result of **Test5**, raise a MessageF.

##### Test6

For each element of **Set1**, if present, check whether the content associated with the `"aria-labelledby"` attribute is equal to the `"alt"` attribute. 

For each occurrence of false-result of **Test6**, raise a MessageF.

#### Messages

##### MessageA 

-    code : **NotPertinentAlt** 
-    status: Failed
-    parameter : `"alt"` attribute, `"title"` attribute, `"src"` attribute, tag name
-    present in source : yes

##### MessageB 

-    code : **CheckPertinenceOfAltAttributeOfInformativeImage** 
-    status: Pre-Qualified (NMI-Passed)
-    parameter : `"alt"` attribute, `"title"` attribute, `"src"` attribute, tag name
-    present in source : yes

##### MessageC

-    code : **TitleNotIdenticalToAlt** 
-    status: Pre-Qualified (NMI-Failed)
-    parameter : `"alt"` attribute, `"title"` attribute, `"src"` attribute, tag name
-    present in source : yes

##### MessageD

-    code : **CheckNatureOfImageWithNotPertinentAlt** 
-    status: Pre-Qualified (NMI-Failed)
-    parameter : `"alt"` attribute, `"title"` attribute, `"src"` attribute, tag name
-    present in source : yes

##### MessageE

-    code : **CheckNatureOfImageAndAltPertinence** 
-    status: Pre-Qualified (NMI-Neutral)
-    parameter : `"alt"` attribute, `"title"` attribute, `"src"` attribute, tag name
-    present in source : yes

##### MessageF 

-    code : **TheTextAssociatedWithAriaAttributeIsNotEqualToAltAttribute** 
-    status: Failed
-    parameter : `"alt"` attribute, `"title"` attribute, `"src"` attribute, tag name
-    present in source : yes

#### Rules remark

 * NotPertinentAlt (fr): Les images porteuses d&#39;information suivantes ont un attribut <code>alt</code> non pertinent :
 * NotPertinentAlt (en): The following images that conveys information have a not pertinence <code>alt</code> attribute :

 * CheckPertinenceOfAltAttributeOfInformativeImage (fr): V&eacute;rifier la pertinence de l&#39;attribut <code>alt</code> des images porteuses d&#39;information suivantes :
 * CheckPertinenceOfAltAttributeOfInformativeImage (en): Please check the pertinence of the <code>alt</code> attribute of the following images that conveys information :

 * TitleNotIdenticalToAlt (fr): L&#39;attribut <code>title</code> n&#39;est pas identique \u00e0 l&#39;attribut <code>alt</code> pour les images porteuses d&#39;information suivantes :
 * TitleNotIdenticalToAlt (en): The <code>title</code> is not identical to the <code>alt</code> attribute on the following images that convey information :

 * CheckNatureOfImageWithNotPertinentAlt (fr): L&#39;attribut <code>alt</code> des images suivantes n&#39;est pas pertinent, v&eacute;rifier qu&#39;il s&#39;agit d&#39;images porteuses d&#39;information et de la pertinence de l'alternative :
 * CheckNatureOfImageWithNotPertinentAlt (en): The following images have a not pertinent <code>alt</code> attribute, please check they convey information and the pertinence of the alternative:

 * CheckNatureOfImageAndAltPertinence (fr): Si les images suivantes sont porteuses d&#39;information, v&eacute;rifier la pertinence de leur attribut <code>alt</code> : 
 * CheckNatureOfImageAndAltPertinence (en): If the following images convey information, please check the pertinence of their <code>alt</code> attribute : 

 * TheTextAssociatedWithAriaAttributeIsNotEqualToAltAttribute (fr): Les images suivantes ont une ou plusieurs propriété Aria qui ne sont pas égale à l'attribut <code>alt</code> :
 * TheTextAssociatedWithAriaAttributeIsNotEqualToAltAttribute (en): The following images have one or more Aria properties that are not identical to the <code>alt</code> attribute:

### Accede Web guidelines

 * Rgaa32016-1-3-1-Accedeweb-HTML-6-3
 * Rgaa32016-1-3-1-Accedeweb-EDIT-4-2

### Analysis

#### Failed

At least one `<img>` tag identified as informative has an irrelevant `"alt"` attribute (**Test1** returns true for at least one element)

At least one `<img>` tag have an aria-label or an aria-labelledby attribute that the text associated is not equal to the alt value (**Test5** or **Test6** returns false for at least one element)

#### Pre-qualified

The alternatives of all the `<img>` tags need to be manually checked (**Test1** returns false for all the elements of **Set1**) 

#### Not Applicable

The page has no `<img>` tag with an `"alt"` attribute not empty (**Set1** or **Set3** are empty)

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

### Alt attribute relevancy 

The content of the `"alt"` attribute is seen as not relevant if :

- empty
- only composed of non-alphanumerical characters
- identical to the `"src"` attribute
- it has an extension of image type (loaded by the nomenclature named **ImageFileExtensions** composed of : jpg, gif, jpeg, png, bmp)
