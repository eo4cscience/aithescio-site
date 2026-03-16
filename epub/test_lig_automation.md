# LIG Automation Test Template

This page verifies the Stage 2 automation of the Leipzig Interlinear Gloss [DD-LIG].

## Automated LIG Injection

The following block is generated dynamically by the `lig_injector.py` from the `fishermen_sentence` record in the data store.

**Rendered LIG:**

<div class="lig-container lig-display">
<div class="lig-line-source">Bhíodh na hiascairí ag cur na mbád in oiriúint do shéasúr an earraigh.</div>
<div class="lig-line-ipa">/vʲiːəx nə hiasˠkəɾʲiː ə kʊɾˠ nə mˠaːd̪ˠ ə n̪ˠɔɾʲuːnʲtʲ d̪ˠɔ çeːsˠuːɾˠ ə nʲaɾˠə/</div>
<div class="lig-morpheme-collection">
<div class="lig-morpheme-stack">
<div class="lig-morpheme-text">Bhí-odh</div>
<div class="lig-morpheme-src-stem">bí</div>
<div class="lig-morpheme-tgt-text">be</div>
<div class="lig-morpheme-func">bí.PAST-HABIT.3SG.AUT</div>
</div><div class="lig-morpheme-stack">
<div class="lig-morpheme-text">na</div>
<div class="lig-morpheme-src-stem">na</div>
<div class="lig-morpheme-tgt-text">the</div>
<div class="lig-morpheme-func">na.DEF.ART.PL</div>
</div><div class="lig-morpheme-stack">
<div class="lig-morpheme-text">h-iasc-airí</div>
<div class="lig-morpheme-src-stem">iasc</div>
<div class="lig-morpheme-tgt-text">fish</div>
<div class="lig-morpheme-func">HIATUS-iasc-ER.PL</div>
</div><div class="lig-morpheme-stack">
<div class="lig-morpheme-text">ag</div>
<div class="lig-morpheme-src-stem">ag</div>
<div class="lig-morpheme-tgt-text">at</div>
<div class="lig-morpheme-func">ag.PROG</div>
</div><div class="lig-morpheme-stack">
<div class="lig-morpheme-text">cur</div>
<div class="lig-morpheme-src-stem">cuir</div>
<div class="lig-morpheme-tgt-text">put</div>
<div class="lig-morpheme-func">cuir.VN</div>
</div><div class="lig-morpheme-stack">
<div class="lig-morpheme-text">na</div>
<div class="lig-morpheme-src-stem">na</div>
<div class="lig-morpheme-tgt-text">the</div>
<div class="lig-morpheme-func">na.DEF.ART.GEN.PL</div>
</div><div class="lig-morpheme-stack">
<div class="lig-morpheme-text">m-bád</div>
<div class="lig-morpheme-src-stem">bád</div>
<div class="lig-morpheme-tgt-text">boat</div>
<div class="lig-morpheme-func">ECL-bád.GEN.PL</div>
</div><div class="lig-morpheme-stack">
<div class="lig-morpheme-text">in</div>
<div class="lig-morpheme-src-stem">i</div>
<div class="lig-morpheme-tgt-text">in</div>
<div class="lig-morpheme-func">i.prep</div>
</div><div class="lig-morpheme-stack">
<div class="lig-morpheme-text">oiriúint</div>
<div class="lig-morpheme-src-stem">oiriúint</div>
<div class="lig-morpheme-tgt-text">preparation</div>
<div class="lig-morpheme-func">oiriúint.VN</div>
</div><div class="lig-morpheme-stack">
<div class="lig-morpheme-text">do</div>
<div class="lig-morpheme-src-stem">do</div>
<div class="lig-morpheme-tgt-text">for</div>
<div class="lig-morpheme-func">do.prep</div>
</div><div class="lig-morpheme-stack">
<div class="lig-morpheme-text">shéasúr</div>
<div class="lig-morpheme-src-stem">séasúr</div>
<div class="lig-morpheme-tgt-text">season</div>
<div class="lig-morpheme-func">LEN-séasúr</div>
</div><div class="lig-morpheme-stack">
<div class="lig-morpheme-text">an</div>
<div class="lig-morpheme-src-stem">an</div>
<div class="lig-morpheme-tgt-text">the</div>
<div class="lig-morpheme-func">an.DEF.ART.GEN.SG</div>
</div><div class="lig-morpheme-stack">
<div class="lig-morpheme-text">earraigh</div>
<div class="lig-morpheme-src-stem">earrach</div>
<div class="lig-morpheme-tgt-text">spring</div>
<div class="lig-morpheme-func">earrach.GEN.SG</div>
</div>
</div>
<div class="lig-line-translation">
The fishermen used to be preparing the boats for the spring season.
</div>
</div>


---

### Verification Points:
1.  **Alignment**: All 4 rows (Surface, Irish Stem, Target Stem, Function) should be vertically aligned.
2.  **Coloring**: Irish stems should be in light blue (`#7dd3fc`).
3.  **Functions**: Should be in Emerald small-caps.
4.  **Translation**: Should be in a blockquote-style callout.
