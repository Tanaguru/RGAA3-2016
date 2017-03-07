# Rule 4.7.1

## Summary

## Business description

### Criterion

[4.7](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-4-7)

###Test

[4.7.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-4-7-1)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#mdia-temporel-type-son-vido-et-synchronis">m&eacute;dia temporel</a> pr&eacute;-enregistr&eacute; seulement vid&eacute;o v&eacute;rifie-t-il, si n&eacute;cessaire, une de ces conditions (<a href="http://references.modernisation.gouv.fr/rgaa/cas-particuliers.html#cp-4-1,4-2,4-3,4-5,4-7,4-9,4-11,4-13" title="Cas particuliers pour le crit&egrave;re 4.7">hors cas particuliers</a>) ? 
 
 * Il existe une <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#audiodescription-synchronise-media-temporel">audio-description</a> synchronis&eacute;e 
 * Il existe une version alternative avec une <a href="hhttp://references.modernisation.gouv.fr/rgaa/glossaire.html#audiodescription-synchronise-media-temporel">audio-description</a> synchronis&eacute;e 


### Level

**AA**

## Technical description

### Scope

**Page**

### Decision level

**Semi-Decidable**

## Algorithm

### Selection

#### Set1

All the elements `<video>` tags (css selector : `video`);

### Process

##### Test1

For each element of **Set1**, raise a MessageA

If **Set1** is empty, raise a MessageB

#### Messages

##### MessageA : We detected video element, check that have an audio description

-    code : **WeDetectedVideoElementCheckThatHaveAudioDescription** 
-    status: Pre-Qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageB: Manual check on page

-   code : ManualCheckOnPage
-   status: Pre-Qualified (NMI-Neutral)
-   present in source : yes

#### Rules remark

 * WeDetectedVideoElementCheckThatHaveAudioDescription (fr): Nous d&eacute;tectons un &eacute;l&eacute;ment vid&eacute;o, v&eacute;rifier qu'il y a une audio description
 * WeDetectedVideoElementCheckThatHaveAudioDescription (en): We detected video element, check that have an audio description

 * ManualCheckOnPage (fr): Veuillez v&eacute;rifier manuellement dans la page :
 * ManualCheckOnPage (en): Please manual check on the page:

### Analysis

#### Pre-qualified

In all cases
