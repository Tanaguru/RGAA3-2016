# Rule 8.2.2

## Summary

This test consists in checking whether the W3C validator return no obsolete error message.

## Business description

### Criterion

[8.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-8-2)

###Test

[8.2.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-8-2-2)

### Description

Pour chaque d&eacute;claration de <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#type-de-document">type de document</a>, le code source de la page ne doit pas utiliser d'&eacute;l&eacute;ments obsol&egrave;tes. Cette r&egrave;gle est-elle respect&eacute;e <a href="http://references.modernisation.gouv.fr/rgaa/cas-particuliers.html#cp-8-2">hors cas particuliers</a> ?

### Level

**A**

## Technical description

### Scope

**Page**

### Decision level

**Decidable**

## Algorithm

### Selection

#### Set1

All error raised by the W3C validator.

#### Set2

All warning raised by the W3C validator.

### Process

#### Tests

##### Test1 

For each element in **Set1**, check if the error message contain the mention "element is obsolete".

For each element returning true in **Test1**, raise a MessageA.

##### Test2 

For each element in **Set1**, check if the error message contain mentions "isindex" and "seen".

For each element returning true in **Test2**, raise a MessageA.

##### Test3 

For each element in **Set2**, check if the warning message contain the mention "element is obsolete".

For each element returning true in **Test3**, raise a MessageA.

##### Test4 

For each element in **Set2**, check if the warning message contain the mention "attribute is obsolete".

For each element returning true in **Test4**, raise a MessageA.

#### Messages

##### MessageA : Obsolete error raised by the W3C validator

-    code : ObsoleteErrorRaisedW3CValidator
-    status: Failed
-    parameter : error message, element HTML Code
-    present in source : yes

#### Rules remark

 * ObsoleteErrorRaisedW3CValidator (fr): Des &eacute;l&eacute;ments obsol&egrave;tes ont &eacute;t&eacute; d&eacute;tect&eacute;s dans la page.
 * ObsoleteErrorRaisedW3CValidator (en): Obsoletes elements detected in the page.

### Accede Web guidelines

 * Rgaa32016-8-2-2-Accedeweb-HTML-4-1

### Analysis

#### Failed

At least one obsolete error is raised (**Test1**, **Test2**, **Test3** or **Test4** return true for at least one element).

#### Passed

The page has no W3C obsolete error (**Test1**, **Test2**, **Test3** and **Test4** return false for all element).