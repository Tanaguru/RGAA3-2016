# Rule 4.3.2

## Summary

## Business description

### Criterion

[4.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-4-3)

### Test

[4.3.2](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-4.3.2)

### Description

Pour chaque <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#mMediaTemp">m&eacute;dia temporel</a> synchronis&eacute; pr&eacute;-enregistr&eacute; poss&eacute;dant des <a href="http://references.modernisation.gouv.fr/referentiel-technique-0#mSsTitreSynchro">sous-titres synchronis&eacute;s</a> diffus&eacute;s via une balise `track`, la balise `track` poss&egrave;de-t-elle un attribut `kind="captions"`

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

All the elements `<video>` tags with at least one child `<track>` tag (css selector : `video`);

### Process

#### Tests

##### Test1

For each element of **Set1**, check if all child `<track>` tags don't have a kind attribute

For each element return true-result of **Test1**, raise a MessageA

##### Test2

For each element return false-result of **Test1**, check if at least one child `"<track>"` tag have a kind attribute with `"caption"`

For each element return false-result of **Test2**, raise a MessageB

#### Messages

##### MessageA : Track tag without kind attribute

-    code : **TrackTagWithoutKindAttribute** 
-    status: Failed
-    parameter : tag name, snippet
-    present in source : yes

##### MessageB : Track tag without kind caption attribute

-    code : **TrackTagWithoutKindCaptionAttribute** 
-    status: Failed
-    parameter : tag name, kind value, snippet
-    present in source : yes

#### Rules remark

 * TrackTagWithoutKindAttribute (fr): Balise Track sans attribut kind d&eacute;tect&eacute;e
 * TrackTagWithoutKindAttribute (en): Track tag without kind attribute detected

 * TrackTagWithoutKindCaptionAttribute (fr): Balise Track sans attribut kind dont la valeur est caption d&eacute;tect&eacute;e
 * TrackTagWithoutKindCaptionAttribute (en): Track tag without kind attribute that value is caption detected

### Accede Web guidelines

 * Rgaa32016-4-3-2-Accedeweb-EDIT-8-3

### Analysis

#### Not Applicable

if no media element with track tag is present in the page (**Set1** is empty)

#### Passed

All the video with track tag have a kind attribute with caption (All element of **Test2** return true-result)

#### Failed

At least one video with track tag have no kind attribute (At least one element of **Test1** return false-result)

At least one video with track tag without kind attribute that value is caption (At least one element of **Test2** return false-result)

## Diagrammes

![](https://raw.githubusercontent.com/Tanaguru/RGAA3-2016/master/docs/Diagrammes/Test4-3-2.png?token=AI6sA2ThE_N5fJHe1fg1Gq-fXcmozMhZks5Y9iZvwA%3D%3D)

## References

https://dev.w3.org/html5/spec-author-view/video.html

## RGAA 3 reference

https://github.com/Tanaguru/Tanaguru-rules-RGAA-3-doc/blob/master/docs/Rule-4-3-2.md

### Update

New test