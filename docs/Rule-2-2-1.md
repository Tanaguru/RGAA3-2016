# Rule 2.2.1

## Summary

This test consists in checking the relevancy of the `"title"` attribute for each `<iframe>` tag.

## Business description

### Criterion

[2.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-2-2)

### Test

[2.2.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-2-2-1)

### Description

Pour chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#cadre-en-ligne">cadre en ligne</a> (balise `iframe`) ayant un attribut `title`, le contenu de cet attribut est-il pertinent ?

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

All the `<iframe>` tags of the page with a title `"attribute"` (css selector : `iframe[title]`)

### Process

#### Test1

For all elements of **Set1**, check whether the content of the "`title`" attribute is not relevant (see Notes for details about relevancy test). 

For each occurrence of true-result of **Test1**, raise a MessageA.

For each occurrence of false-result of **Test1**, raise a MessageB

##### MessageA

-   code : NotPertinentTitleOfFrame
-   status: Failed
-   parameter : `"title"` attribute, tag name, snippet
-   present in source : yes

##### MessageB

-   code : CheckTitleOfFramePertinence
-   status: Pre-Qualified
-   parameter : `"title"` attribute, tag name, snippet
-   present in source : yes

#### Rules remark

 * NotPertinentTitleOfFrame (fr): L&#39;attribut <code>title</code> des balises <code>iframe</code> suivantes n&#39;est pas pertinent : 
 * NotPertinentTitleOfFrame (en): The <code>title</code> attribute of the following <code>frame</code> tags is not pertinent : 

 * CheckTitleOfFramePertinence (fr): V&eacute;rifier la pertinence de l&#39;attribut <code>title</code> des balises <code>frame</code> suivantes :
 * CheckTitleOfFramePertinence (en): Please check the pertinence of the <code>title</code> attribute of the following <code>frame</code> tags :

### Accede Web guidelines

 * Rgaa32016-2-2-1-Accedeweb-HTML-13

### Analysis

#### Failed

At least one `<iframe>` has an irrelevant `"title"` attribute (**Test1** returns true for at least one element)

#### Pre-qualified

The content of the `"title"` attribute of all the `<iframe>` tags needs to be manually checked (**Test1** returns false for all the elements of **Set1**) 

#### Not Applicable

The page has no `<iframe>` tag with a `"title"` attribute (**Set1** is empty)

## Notes

The content of the "`title`" attribute is seen as not relevant if :

- empty
- only composed of non-alphanumerical characters
- identical to the `"src"` attribute

