# Rule 4.3.2

## Summary

No-check rule

## Business description

### Criterion

[4.3](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-4-3)

###Test

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

#### Set2

All the elements `<bgsound>`, `<embed>` and `<object>` tags (css selector : `bgsound`, `embed`, `object`);

### Process

#### Tests

##### Test1

For each element of **Set1**, check the presence of a kind="captions" attribute on the `<track>` tags

For each element return false-result of **Test1**, raise a MessageA

#### Messages

##### MessageA : Track tag without kind attribute

-    code : **TrackTagWithoutKindAttribute** 
-    status: Failed
-    parameter : tag name, snippet
-    present in source : yes

#### Rules remark

 * TrackTagWithoutKindAttribute (fr): Balise Track sans attribut kind d&eacute;tect&eacute;e
 * TrackTagWithoutKindAttribute (en): Track tag without kind attribute detected

### Accede Web guidelines

 * Rgaa32016-4-3-2-Accedeweb-EDIT-8-3

### Analysis

#### Not Applicable

if no media element is present in the page (**Set1** and **Set2** is empty)

#### Passed

All the video with track tag have a kind attribute (All element of **Test1** return true-result)

#### Failed

At least one video with track tag have no kind attribute (At least one element of **Test1** return false-result)

#References
https://dev.w3.org/html5/spec-author-view/video.html
