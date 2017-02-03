# Rule 1.3.3

## Summary

This test consists in checking whether each button associated with an image that handles information has a relevant alternative.

## Business description

### Criterion

[1.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-1-3)

### Test

[1.3.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-1-3-3)

### Description

Pour chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#bouton-formulaire">bouton</a> associ&eacute; &agrave; une image (balise `input` avec l'attribut `type="image"`) ayant un attribut `alt`, v&eacute;rifie-t-elle ces conditions (hors <a href="http://references.modernisation.gouv.fr/rgaa/cas-particuliers.html#cp-1-3" title="Cas particuliers pour le crit&egrave;re 1.3">cas particuliers</a>) ?

 * Le contenu de l'attribut `alt` est pertinent ;
 * S'il est pr&eacute;sent, le contenu de l'attribut `title` est identique au contenu de l'attribut `alt` ;
 * S'il est pr&eacute;sent, le contenu de la propri&eacute;t&eacute; `aria-label` est identique au contenu de l'attribut alt ;
 * S'il est pr&eacute;sent, le contenu du passage de texte lié via la propriété aria-labelledby est identique au contenu de l'attribut alt.

### Level

**A**

## Technical description

### Scope

**page**

### Decision level

**Semi-decidable**

## Algorithm

### Selection

#### Set1

All the `<input>` tags with a `"type"` attribute equals to "image" and an `"alt"` attribute (css selector : `input[type=image][alt]`)

### Process

#### Test1

For all elements of **Set1**, check whether the content of the `"alt"` attribute is not relevant (see Notes for details about relevancy test). 

For each occurrence of true-result of **Test1**, raise a MessageA.

For each occurrence of false-result of **Test1**, raise a MessageB

#### Test2

For all elements return false-result of **Test1**, check whether the content of the `"title"` attribute is equal to the `"alt"` attribute.

For each occurrence of false-result of **Test2**, raise a MessageC.

#### Test3

For all elements return false-result of **Test1**, check whether the content of the `"aria-label"` attribute is equal to the `"alt"` attribute.

For each occurrence of false-result of **Test3**, raise a MessageC.

#### Test4

For all elements return false-result of **Test1**, check whether the text associated with the `"aria-labelledby"` attribute is equal to the `"alt"` attribute.

For each occurrence of false-result of **Test4**, raise a MessageC.

##### MessageA 

-    code : **NotPertinentAlt** 
-    status: Failed
-    parameter : `"alt"` attribute, `"src"` attribute, tag name
-    present in source : yes

##### MessageB 

-    code : **CheckPertinenceOfAltAttributeOfInformativeImage** 
-    status: Pre-Qualified (NMI-Neutral)
-    parameter : `"alt"` attribute, `"src"` attribute, tag name
-    present in source : yes

##### MessageC 

-    code : **AlternativeNotEqualAlt** 
-    status: Failed
-    parameter : `"alt"` attribute, `"title"` or `"aria-label"` attribute or text associated with `"aria-labelledby"`, `"src"` attribute, tag name
-    present in source : yes

#### Rules remark

 * NotPertinentAlt (fr): Les images porteuses d&#39;information suivantes ont un attribut <code>alt</code> non pertinent :
 * NotPertinentAlt (en): The following images that conveys information have a not pertinence <code>alt</code> attribute :

 * CheckPertinenceOfAltAttributeOfInformativeImage (fr): V&eacute;rifier la pertinence de l&#39;attribut <code>alt</code> des images porteuses d&#39;information suivantes :
 * CheckPertinenceOfAltAttributeOfInformativeImage (en): Please check the pertinence of the <code>alt</code> attribute of the following images that conveys information :

 * TitleNotIdenticalToAlt (fr): L&#39;alternative n&#39;est pas identique \u00e0 l&#39;attribut <code>alt</code> pour les images porteuses d&#39;information suivantes :
 * TitleNotIdenticalToAlt (en): The alternative is not identical to the <code>alt</code> attribute on the following images that convey information :

### Accede Web guidelines

 * Rgaa32016-1-3-3-Accedeweb-HTML-6-3
 * Rgaa32016-1-3-3-Accedeweb-EDIT-4-2

### Analysis

#### Failed

At least one `<input>` tag with a `"type"` attribute equals to "image" has an irrelevant `"alt"` attribute (**Test1** returns true for at least one element)

At least one `<input>` tag with a `"title"` or `"aria-label"` attribute or the text associated with a `"aria-labelledby"` is not equal to the `"alt"` attribute (**Test3**, **Test4** or **Test5** returns false for at least one element)

#### Pre-qualified

The alternatives of all the `<input>` tags with a `"type"` attribute equals to "image" need to be manually checked (**Test1** returns false for all the elements of **Set1**) 

#### Not Applicable

The page has no `<input>` tag with a `"type"` attribute equals to "image" tag and an `"alt"` attribute (**Set1** is empty)

## Notes

The content of the `"alt"` attribute is seen as not relevant if :

- empty
- only composed of non-alphanumerical characters
- identical to the `"src"` attribute
- it has an extension of image type (loaded by the nomenclature named **ImageFileExtensions** composed of : jpg, gif, jpeg, png, bmp)
