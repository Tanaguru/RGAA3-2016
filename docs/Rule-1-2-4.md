# Rule 1.2.4

## Summary

This test consists in checking whether the ARIA attribute of each decorative vector image (`<svg>` tag) are implemented correctly and checking each decorative vector image or children have no `"title"` or `"desc"` attribute unless they are empty.

## Business description

### Criterion

[1.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-1-2)

###Test

[1.2.4](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-1-2-4)

### Description

Chaque image vectorielle de d&eacute;coration (balise `<svg>`) sans l&eacute;gende non porteuse d'information v&eacute;rifie-t-elle ces conditions ? 
 
 * La balise `<svg>` poss&egrave;de un attribut `aria-hidden="true"` ;
 * Les balises `<title>` et `<desc>` sont absentes ou vides ;
 * La balise `<svg>` ou l'un de ses enfants est d&eacute;pourvue d'attribut `title` ;
 * La balise `<svg>` ou l'un de ses enfants est d&eacute;pourvue de role, propri&eacute;t&eacute; ou &eacute;tat ARIA visant &agrave; labelliser l'image vectorielle (`aria-label`, `aria-describedby`, `aria-labelledby` par exemple). 

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

All the `<svg>` tags of the page, not within a link not identified as captcha (see Notes about captcha detection) (css selector : `svg:not(a svg)`) and the `"role"` attribute that value is different than "img" or "presentation" is missing.

#### Set2

All the elements of **Set1** identified as decorative image by marker usage (see Notes for details about detection through marker)

#### Set3

All the elements of **Set1** identified neither as informative image, nor as decorative image by marker usage (see Notes for details about detection through marker)

#### Set4

All the elements of **Set1** without a `"aria-hidden"` attribute equals to  `"true"`.

#### Set5

All the elements of **Set1** with a not empty `<title>` or `<desc>` tag as child tag.

#### Set6

All the elements of **Set1** with a `"aria-label"`, `"aria-labelledby"` or  `"aria-describedby"` attribute on the element or one of its children.

#### Set7

All the elements of **Set1** with a `"title"` attribute.

#### Set8

All the elements of **Set2** without `"title"`, `"aria-label"`, `"aria-labelledby"`, `"aria-describedby"` attributes, without a not empty `<title>` or `<desc>` tag as child tag and with a `"role"` attribute equals to  `"img"`.

### Process

#### Tests

##### Test1

For each element of **Set4**, raise a MessageA.

##### Test2

For each element of **Set5**, raise a MessageB.

##### Test3 

For each element of **Set6**, raise a MessageC.

##### Test4 

For each element of **Set7**, raise a MessageD.

##### Test5 

For each element of **Set8**, raise a MessageE.

#### Messages

##### MessageA : Decorative svg without aria-hidden true attribute 

-    code : DecorativeSvgWithoutAriaHiddenTrueAttribute
-    status: Failed
-    parameter : tag name, Snippet
-    present in source : yes

##### MessageB : Decorative svg with a not empty `<title>` or `<desc>` child tag

-    code : DecorativeSvgWithNotEmptyTitleOrDescTags
-    status: Failed
-    parameter : tag name, Snippet
-    present in source : yes

##### MessageC : Decorative svg or children with Aria attribute

-    code : DecorativeSvgOrChildrenWithAriaAttribute
-    status: Failed
-    parameter : tag name, Snippet
-    present in source : yes

##### MessageD : Decorative svg or children with `title` attribute

-    code : DecorativeSvgWithTitleAttribute
-    status: Failed
-    parameter : tag name, Snippet
-    present in source : yes

##### MessageE : Suspected decorative svg without alternative

-    code : SuspectedWellFormedDecorativeSvg
-    status: Pre-Qualified (NMI-Neutral)
-    parameter : tag name, Snippet
-    present in source : yes

#### Rules remark

 * DecorativeSvgWithoutAriaHiddenTrueAttribute (fr): Les images svg de d&eacute;coration suivantes n'ont pas d'attribut <code>aria-hidden="true"</code> :
 * DecorativeSvgWithoutAriaHiddenTrueAttribute (en): The following decorative svg images have no <code>aria-hidden="true"</code> attribute:

 * DecorativeSvgWithNotEmptyTitleOrDescTags (fr): Les images svg de d&eacute;coration suivantes ont des balises enfant de type <code>title</code> ou <code>desc</code> :
 * DecorativeSvgWithNotEmptyTitleOrDescTags (en): The following decorative svg images have child tags <code>title</code> or <code>desc</code>:

 * DecorativeSvgOrChildrenWithAriaAttribute (fr): Les images svg de d&eacute;coration suivantes, ou l'un de leurs enfants, ont un ou plusieurs attributs ARIA:
 * DecorativeSvgOrChildrenWithAriaAttribute (en): The following decorative svg images or childdren have one or more ARIA attribute:

 * DecorativeSvgWithTitleAttribute (fr): Les images svg de d&eacute;coration suivantes, ou l'un de leurs enfants, ont un attribut <code>title</code> :
 * DecorativeSvgWithTitleAttribute (en): The following decorative svg images or childdren have a <code>title</code> attribute:

 * SuspectedWellFormedDecorativeSvg (fr): Les images vectorielles suivantes ont une alternative vide, v&eacute;rifier que ce sont bien des images de d&eacute;coration :
 * SuspectedWellFormedDecorativeSvg (en): The following vectorial images have an empty alternative, please check they are decorative:

### Accede Web guidelines

 * Rgaa32016-1-2-4-Accedeweb-HTML-6-2
 * Rgaa32016-1-2-4-Accedeweb-EDIT-4-1

### Analysis

#### Not Applicable

The page has no `<svg>` tag (**Set1** is are empty)

All the `<svg>` not identified as decorative, have role img, no `aria-label`, `aria-describedby`, `aria-labelledby` or `title` attributes, no `<title>` or `<desc>` as child tag (**Set8** are empty)

#### Failed

At least one `<svg>` identified as decorative don't have a `aria-hidden` attribut with `true` value or have a `aria-label`, `aria-describedby`, `aria-labelledby` or `title` attribute or have a not empty `<title>` or `<desc>` as child tag (**Set4** OR **Set5** OR **Set6** OR **Set7** is not empty)

#### Passed

All the `<svg>` identified as decorative, have role img, no `aria-label`, `aria-describedby`, `aria-labelledby` or `title` attributes, no `<title>` or `<desc>` as child tag (**Set4** AND **Set5** AND **Set6** AND **Set7** are empty)

#### Pre-qualified

In all other cases

## Notes

The `<svg>` not identified by marker, without `"role"` attribute equals to "img" are not treated in this test. The test 1.3.5 asks to check that is attribute is present for informative `<svg>`. We can deduce this attribute has to be present for all `<svg>` in any way. To avoid to invalidate a same element twice, we decided to invalid this pattern in the test 1.3.5
 
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
