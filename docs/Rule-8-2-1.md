# Rule 8.2.1

## Summary

This test consists in checking whether the W3C validator return no error message.

## Business description

### Criterion

[8.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-8-2)

###Test

[8.2.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-8-2-1)

### Description

Pour chaque d&eacute;claration de <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#type-de-document">type de document</a>, le code source de la page v&eacute;rifie-t-il ces conditions (hors <a href="http://references.modernisation.gouv.fr/rgaa/cas-particuliers.html#cp-8-2">cas particuliers</a>) ? 
 
 *  Les balises respectent les r&egrave;gles d'&eacute;criture ;
 *  L'imbrication des balises est conforme ;
 *  L'ouverture et la fermeture des balises sont conformes ;
 *  Les attributs respectent les r&egrave;gles d'&eacute;criture ;
 *  Les valeurs des attributs respectent les r&egrave;gles d'&eacute;criture.

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

### Process

#### Tests

##### Test1 

For each element in **Set1**, raise a MessageA.

#### Messages

##### MessageA : Error raised by the W3C validator

-    code : ErrorRaisedW3CValidator
-    status: Failed
-    parameter : error message, element HTML Code
-    present in source : yes

### Analysis

#### Failed

At least one error is raised in **Set1**.

#### Passed

The page has no W3C error (**Set1** is empty).
