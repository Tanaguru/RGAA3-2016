# Rule 4.9.1

## Summary

## Business description

### Criterion

[4.9](http://references.modernisation.gouv.fr/rgaa/criteres.html#crit-4-9)

###Test

[4.9.1](http://references.modernisation.gouv.fr/rgaa/criteres.html#test-4-9-1)

### Description

Chaque <a href="http://references.modernisation.gouv.fr/rgaa/glossaire.html#mdia-temporel-type-son-vido-et-synchronis">m&eacute;dia temporel</a> pr&eacute;-enregistr&eacute; seulement audio a-t-il, si n&eacute;cessaire, une interpr&eacute;tation en langue des signes adapt&eacute;e &agrave; la langue du m&eacute;dia (<a href="http://references.modernisation.gouv.fr/rgaa/cas-particuliers.html#cp-4-1,4-2,4-3,4-5,4-7,4-9,4-11,4-13" title="Cas particuliers pour le crit&egrave;re 4.9">hors cas particuliers</a>) ?

### Level

**AAA**

## Technical description

### Scope

**Page**

### Decision level

**Semi-Decidable**

## Algorithm

### Selection

#### Set1

All the elements `<audio>` tags (css selector : `audio`);

#### Set2

All the elements `<embed>` and `<object>` tags (css selector : `embed`, `object`);

### Process

##### Test1

For each element of **Set1**, raise a MessageA

If **Set1** is empty and **Set2** is not empty, raise a MessageB

#### Messages

##### MessageA : We detected audio element, check that they have a sign language interpretation

-    code : **WeDetectedAudioElementCheckThatTheyHaveSignLanguageInterpretation** 
-    status: Pre-Qualified (NMI-Neutral)
-    parameter : tag name, snippet
-    present in source : yes

##### MessageB: Manual check on page

-   code : ManualCheckOnPage
-   status: Pre-Qualified (NMI-Neutral)
-   present in source : yes

#### Rules remark

 * WeDetectedAudioElementCheckThatTheyHaveSignLanguageInterpretation (fr): Nous d&eacute;tectons un &eacute;l&eacute;ment audio, v&eacute;rifier qu'il y a une interpr&eacute;tation en langue des signes
 * WeDetectedAudioElementCheckThatTheyHaveSignLanguageInterpretation (en): We detected audio element, check that they have a sign language interpretation

 * ManualCheckOnPage (fr): Veuillez v&eacute;rifier manuellement dans la page :
 * ManualCheckOnPage (en): Please manual check on the page:

### Analysis

#### Not Applicable

if no media element is present in the page (**Set1** and **Set2** is empty)

#### Pre-qualified

In all cases
