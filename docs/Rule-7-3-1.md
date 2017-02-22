# Rule 7.3.1

## Summary

## Business description

### Criterion

[7.3](http://references.modernisation.gouv.fr/referentiel-technique-0#crit-7-3)

###Test

[7.3.1](http://references.modernisation.gouv.fr/referentiel-technique-0#test-7-3-1)

### Description

Chaque &eacute;l&eacute;ment poss&eacute;dant un gestionnaire d'&eacute;v&eacute;nement contr&ocirc;l&eacute; par un <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#mScript">script</a> v&eacute;rifie-t-il une de ces conditions (<a href="http://references.modernisation.gouv.fr/referentiel-technique-0#cpCrit7-3" title="Cas particuliers pour le crit&egrave;re 7.3">hors cas particuliers</a>) ? 
 
 *  L'&eacute;l&eacute;ment est <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#mAAClavierSouris">accessible par le clavier et la souris</a> 
 *  Un &eacute;l&eacute;ment <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#mAAClavierSouris">accessible par le clavier et la souris</a> permettant de r&eacute;aliser la m&ecirc;me action est pr&eacute;sent dans la page 

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

All tags that not `<button>`, `<a>`, `<input>`, `<select>`, `<textarea>`, `<area>`,  with at least one of these attributes :
 - onclick;
 - oncontextmenu
 - ondblclick
 - onmousedown
 - onmouseenter
 - onmouseleave
 - onmousemove
 - onmouseover
 - onmouseout
 - onmouseup

#### Set2

All interactive element `<button>`, `<a>`, `<input>`, `<select>`, `<textarea>`, `<area>`

### Process

#### Tests

##### Test1

For each element of **Set1**, check if the element has a `tabindex` attribute that value is differente than `-1`

For each element return true-result of **Test1**, raise a MessageA

##### Test2

For each element return false-result of **Test1**, check if the element has a `tabindex` attribute that value is `-1` 

For each element return true-result of **Test2**, raise a MessageB

For each element return false-result of **Test2**, raise a MessageC

If **Set1** is empty, raise a MessageA

#### Messages

##### MessageA : Check Manually

-    code : **CheckManually** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageB : Interactive element which it is not possible to take the focus, check if a mechanism allows the user to take the focus

-    code : **InteractiveElementWhichItIsNotPossibleToTakeTheFocusCheckMechanismAllowsUserToTakeFocus** 
-    status: Pre-qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageC : Interactive element which it is not possible to take the focus

-    code : **InteractiveElementWhichItIsNotPossibleToTakeTheFocus** 
-    status: Pre-qualified (NMI-Failed)
-    parameter : tag name, snippet
-    present in source : yes

#### Rules remark

 * CheckManually (fr): V&eacute;rifier manuellement
 * CheckManually (en): Check Manually

 * InteractiveElementWhichItIsNotPossibleToTakeTheFocusCheckMechanismAllowsUserToTakeFocus (fr): Element interactif d&eacute;tect&eacute; dans la page dont il n'est pas possible de prendre le focus, v&eacute;rifier manuellement si un m&eacute;canisme permet &agrave; l'utilisateur permet &agrave; l'utilisateur d'en prendre le focus 
 * InteractiveElementWhichItIsNotPossibleToTakeTheFocusCheckMechanismAllowsUserToTakeFocus (en): Interactive element detected in the page which it is not possible to take the focus, check if a mechanism allows the user to take the focus

 * InteractiveElementWhichItIsNotPossibleToTakeTheFocus (fr): Element interactif d&eacute;tect&eacute; dans la page dont il n'est pas possible de prendre le focus
 * InteractiveElementWhichItIsNotPossibleToTakeTheFocus (en): Interactive element detected in the page which it is not possible to take the focus

### Analysis

#### Pre-qualified

In all other cases
