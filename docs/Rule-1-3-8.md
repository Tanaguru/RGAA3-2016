# Rule 1.3.8

## Summary

This test consists in checking for each informative vector image (`<svg>` tag) are implemented correctly and checking each informative vector image have a `"desc"` tags or a `"aria-label"` attribute with relevante alternative.

## Business description

### Criterion

[1.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-1-3)

###Test

[1.3.8](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-1-3-8)

### Description

Chaque image vectorielle (balise svg) porteuse d’information, en l’absence d’alternative, v&eacute;rifie-t-elle ces conditions (hors <a href="http://references.modernisation.gouv.fr/rgaa/cas-particuliers.html#cp-1-3" title="Cas particuliers pour le crit&egrave;re 1.3">cas particuliers</a>) ? 
 
 * La balise `svg` poss&egrave;de un `role="img"` 
 * La balise `svg` poss&egrave;de une propri&eacute;t&eacute; `"aria-label"` dont le contenu est pertinent et identique &agrave; l'attribut `title` s'il est pr&eacute;sent 
 * La balise `svg` poss&egrave;de une balise `desc` dont le contenu est pertinent et contient un passage de texte identique &agrave; la propri&eacute;t&eacute; aria-label et &agrave; l'attribut `title` de la balise `svg` s'il est pr&eacute;sent 

### Level

**A**

## Technical description

### Scope

**Page**

### Decision level

**Semidecidable**

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

#### Set7

All the elements of **Set3** with a `"role"` attribute with value `"img"` 

#### Set8

All the elements of **Set4** with a `"role"` attribute with value `"img"` 

#### Set9

All the elements of **Set5** with a `"role"` attribute with value `"img"` 

#### Set10

All the elements of **Set6** with a `"role"` attribute with value `"img"` 

### Process

#### Tests

##### Test1

For each element of **Set3** and **Set4**, check the presence of the `"role"` attribute with value `"img"`, the `"aria-label"` attribute and the `<desc>` child tag.

For each occurrence of false-result of **Test1**, raise a MessageA

##### Test2

For each element of **Set4** and **Set6**, check the presence of the `"role"` attribute with value `"img"`, the `"aria-label"` attribute and the `<desc>` child tag.

For each occurrence of false-result of **Test2**, raise a MessageA

##### Test3 

For each element of **Set6** and **Set7**, check whether the `"aria-label"` attribute is not empty when present.

For each occurrence of false-result of **Test3**, raise a MessageB.

##### Test4 

For each element of **Set8** and **Set9**, check whether the `"aria-label"` attribute is not empty when present.

For each occurrence of false-result of **Test4**, raise a MessageC.

##### Test5

For each element of **Set6** and **Set7**, check whether the `"aria-label"` attribute is identical to the `"title"` attribute when they are both present.

For each occurrence of false-result of **Test5**, raise a MessageB.

##### Test6 

For each element of **Set8** and **Set9**, check whether the `"aria-label"` attribute is identical to the `"title"` attribute when they are both present.

For each occurrence of false-result of **Test6**, raise a MessageC.

##### Test7

For each element of **Set6** and **Set7**, check whether the content of the `<desc>` child tag is not empty when present.

For each occurrence of false-result of **Test7**, raise a MessageB.

##### Test8 

For each element of **Set8** and **Set9**, check whether the content of the `<desc>` child tag is not empty when present.

For each occurrence of false-result of **Test8**, raise a MessageC.

##### Test9

For each element of **Set6** and **Set7**, check whether the content of the `<desc>` child tag is identical to the `"title"` attribute when they are both present.

For each occurrence of false-result of **Test9**, raise a MessageB.

##### Test10 

For each element of **Set8** and **Set9**, check whether the content of the `<desc>` child tag is identical to the `"title"` attribute when they are both present.

For each occurrence of false-result of **Test10**, raise a MessageC.

#### Messages

For each occurrence of **Set6** and **Set7** that return a true on **Test3**, **Test5**, **Test7** AND **Test9**, raise a MessageD

For each occurrence of **Set8** and **Set9** that return a true on **Test4**, **Test6**, **Test8** AND **Test10**, raise a MessageE

##### MessageA : `svg` without role `img` attribute or `aria-label` attribute or `desc` child tag

-    code : SvgWithoutRoleImageAriaLabelOrDesc
-    status: Failed
-    parameter : tag name, Snippet
-    present in source : yes

##### MessageB : Informative svg with not bad alternative definition 

-    code : InformativeSvgWithNotPertinentAlternative
-    status: Pre-Qualified (NMI-Passed)
-    parameter : `"role"` attribute, `"aria-label"` attribute, `"title"` attribute, `"desc"` child tag, tag name, Snippet
-    present in source : yes

##### MessageC : Check nature of svg with bad alternative 

-    code : CheckNatureOfSvgWithNotPertinentAlternative
-    status: Pre-Qualified (NMI-Failed)
-    parameter : `"role"` attribute, `"aria-label"` attribute, `"title"` attribute, `"desc"` child tag, tag name, Snippet
-    present in source : yes

##### MessageD : Check alternative pertinence of informative `svg` 

-    code : CheckPertinenceOfAlternativeOfInformativeSvg
-    status: Pre-Qualified (NMI-Neutral)
-    parameter : `"role"` attribute, `"aria-label"` attribute, `"title"` attribute, `"desc"` child tag, tag name, Snippet
-    present in source : yes

##### MessageE : Check nature of svg and alternative pertinence 

-    code : CheckNatureOfSvgAndAlternativePertinence
-    status: Pre-Qualified (NMI-Neutral)
-    parameter : `"role"` attribute, `"aria-label"` attribute, `"title"` attribute, `"desc"` child tag, tag name, Snippet
-    present in source : yes

#### Rules remark

 * SvgWithoutRoleImageAriaLabelOrDesc (fr): L'attribut <code>role</code> avec la valeur <code>img</code>, l'attribut <code>aria-label</code> ou la balise enfant <code>desc</code> manquent sur les images vectorielles suivantes :
 * SvgWithoutRoleImageAriaLabelOrDesc (en): The <code>role</code> attribute with the "img" value, the aria-label attribute or the desc child tag are missing on the following vectorial images :

 * InformativeSvgWithNotPertinentAlternative (fr): Les images <code>svg</code> porteuses d&#39;information suivantes semblent avoir une alternative non pertinente : 
 * InformativeSvgWithNotPertinentAlternative (en): The following <code>svg</code> images that convey information seem to have a not pertinent alternative : 

 * CheckNatureOfSvgWithNotPertinentAlternative (fr): Les images <code>svg</code> suivantes semblent avoir une alternative non pertinente. V&eacute;rifier qu&#39;elles sont porteuses d&#39;information 
 * CheckNatureOfSvgWithNotPertinentAlternative (en): Check the following  <code>svg</code> images that seem to have a not pertinent alternative, convey information :

 * CheckPertinenceOfAlternativeOfInformativeSvg (fr): Veuillez v&eacute;rifier la pertinence de l&#39;alternative des images <code>svg</code> porteuses d&#39;information suivantes : 
 * CheckPertinenceOfAlternativeOfInformativeSvg (en): Check the pertinence of the alternative of the following <code>svg</code> images that convey information : 

 * CheckNatureOfSvgAndAlternativePertinence (fr): Si les images <code>svg</code> suivantes sont porteuses d&#39;information, veuillez v&eacute;rifier la pertinence de leur alternative :
 * CheckNatureOfSvgAndAlternativePertinence (en): If the following <code>svg</code> images convey information, check the pertinence of their alternative : 

### Accede Web guidelines

 * Rgaa32016-1-3-8-Accedeweb-EDIT-4-2

### Analysis

#### Failed

The page contains at least one `<svg>` without a `"role"` attribute equals to `"img"` (**Test1** OR **Test2** returns false for at least one element)

#### Not Applicable

The page has no `<svg>` tag (**Set1** and **Set2** are empty)

#### Pre-qualified

In all other cases

## Notes

The `<svg>` not identified by marker, without `"role"` attribute equals to "img" are invalidated in this test. The test 1.2.4 asks to check that is attribute is present for decorative `<svg>`. We can deduce this attribute has to be present for all `<svg>` in any way. To avoid to invalidate a same element twice, we decided to ONLY invalid this pattern in this test.

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

