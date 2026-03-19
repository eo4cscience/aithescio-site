# Build Injection Collection Demo

This document provides a technical overview and live demonstration of the dynamic injection system used in the Build Engine. Each section explains a specific tag, its backend implementation, and its rendered result.

---

## 1. String Injection (`hello_msg`)

### Markdown Syntax
`<!-­- hello_msg -­->`

### Backend Process
1.  **Registry Lookup**: The scanner identifies `hello_msg`.
2.  **Function Call**: The engine calls `get_hello_message()` from `injectors.py`.
3.  **Static Return**: The function returns a hard-coded string: `"hello from data injector"`.

### Injection Logic
The entire comment block is replaced by the return value during the `process_content` phase using a simple regex substitution.

**Result:** hello from data injector



**Result for a timestanp:** 2026-03-18 19:35:49



---

## 2. Parameterized Injection (`GREET_USER`)

### Markdown Syntax
`<!-­- GREET_USER {"name": "Raynier van Egmond", "honoric": "Professor"} -­->`

### Parameters & Backend Usage
- **`name`**: The recipient's full name.
- **`honoric`**: A prefix title (defaults to "User" if omitted).

The `BuildEngine` parses the JSON string into a Python dictionary. It then uses `inspect.signature` to match these keys to the function arguments in `greet_user(name, honoric)`.

### Injection Logic
The function returns a formatted string: `f"Greetings, {honoric} {name}!"`. This string is swapped into the document at the tag's exact position.

**Result:** Greetings, Professor Raynier van Egmond!

---

## 3. LIG Component Automation (`LIG`)

This is a more complex example where the engine uses a sample from a data file for now. The sentence is:

`Bhíodh na hiascairí ag cur na mbád in oiriúint do shéasúr an earraigh`.

The phonetics engine transliterates this into:

<span class="ga-word">Bhíodh na hiascairí ag cur na mbád in oiriúint do shéasúr an earraigh<span class="ga-tooltip">/vʲɪːɔɣ nˠa hʲɪəʃcəɾʲɪː aɡ kʊɾˠ nˠa mˠaːd̪ˠ ɪnʲ ɔɪɾʲəʊːɪnʲtʲ d̪ˠɔ hɛːasˠəːɾˠ anˠ aɾʲəj/</span></span>

At a later stage the morphological parser will provide the input for the LIG injection process but for now the morphological data is hard-coded in the global injection context environment.

### Markdown Syntax
`
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
`


### Parameters & Backend Usage
- **`id`**: Key used to look up morphological data in `backend/data/lig_samples.json`.
- **`ortho`** (Optional): Overrides the source sentence display.

**Backend Flow:**
1.  **Data Retrieval**: The `lig_injector.py` fetches the 13-morpheme breakdown (Surface, Stem, Function) associated with the `id`.
2.  **HTML Generation**: The recursive rendering logic builds a complex nested flexbox structure using the premium glassmorphic CSS tokens.

### Injection Logic
Because the result is a complex multi-line HTML block, the engine treats it as a single chunk and replaces the tag. This allows for visually rich, aligned linguistic analysis to be inserted into a standard Markdown flow.

**Result:**

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

## 4. Automatic Build Metadata (`build_timestamp`)

### Markdown Syntax
`2026-03-18 19:35:49`

### Backend Process
The `get_timestamp()` function is called at build time, retrieving the current system clock. This ensures that every generated document has an accurate "Last Updated" marker.

**Result:** _Page generated at: 2026-03-18 19:35:49_
