<div align="center">

# capi

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

</div>

## <div align="center">About the Project</div>

**capi** is a Turkish-language study app for reviewing biology, chemistry, math, German, Turkish literature, and English with short, interactive quizzes. Choose a subject, practice across all its topics or focus on one, and review explanations after each answer.

## <div align="center">Features</div>

### Flexible Practice
Start a mixed round or choose a specific topic. Each round contains up to 10 questions, and questions you miss or have not seen are more likely to appear in future rounds.

### Multiple Question Types
Practice with multiple-choice, fill-in-the-blank, true/false, matching, ordering, and open-ended written questions. Many math questions come with a geometric figure, chart, or data table. Every answer includes feedback and an explanation.

### German Practice
The German course follows the *Essen und Trinken* unit: food vocabulary and articles, plurals, meals, likes and dislikes, shopping, prices, and recipes. Besides the usual question types it adds two Duolingo-style exercises:

- **Sentence building:** tap word blocks to build a sentence. The bank includes distractor blocks, a used block leaves an empty space behind, and other correct word orders are accepted too.
- **Listening:** a German text is read aloud (normal or slow) without showing it, and the student types the amounts they hear as digits, for example *zweihundert* → 200. Each box is checked separately, and the text appears after answering. Without speech support the text is shown instead.
- **Tile matching:** match pictures or words in a two-column grid. Correct pairs turn green right away, wrong pairs flash red and shake so the student can try again, and the question counts as correct once every pair is found.

The German course also has a **★ Altın Sorular** (golden questions) topic with the questions the teacher announced for the exam: a recipe with its ingredients and key verbs, *Was kostet / Was kosten*, *gerne / nicht gerne*, and breakfast and favorite food. It sits at the top of the topic list with its own lesson, and its questions carry an *Altın soru* badge in mixed rounds too.

German words in questions have **word hints**: words found in the German glossary are underlined with a dotted line, and tapping one opens a small pop-up with its meaning (nouns with their article) and a button to hear it. To avoid giving answers away, hints are hidden in questions that ask for a meaning and for words whose meaning appears in the question or its choices. The glossary lives in `docs/glossary-alm.json` and maps lowercase words or two-word phrases to their meaning, written as `der Apfel · elma` for nouns; a question can turn hints off with `"nohint": true`.

German sentences can be played aloud with the speaker button, using the browser's built-in speech synthesis.

### Literature Practice
The Edebiyat (Turkish language and literature) course is built for the 10th grade first-term first written exam (Maarif Modeli, *Sözün Ezgisi*): literary periods, poetry and meter, rhyme and *redif*, *koşuk* and *sagu*, *koşma* and the *âşık* tradition, *türkü* and *mani*, Sufi poetry, folk tales, noun and adjective phrases, and spelling. Definitions follow the MEB textbook.

- **Yazılı Provası:** a topic at the top of the list with original questions modeled on the open-ended written exam format (word meaning from context, dating a poem, T diagrams, harmony, noun and adjective phrases, a storyboard, spelling), each with its poem or text and a lesson on how points are given. The texts are either public-domain folk poems (Yunus Emre, Köroğlu, Karacaoğlan, anonymous *türkü*s, *Alp Er Tunga Sagusu*) or written for the app, such as a *koşuk*-style poem, a *mani*, and the tale *Altın Başak*.
- **Open-ended questions:** the student writes the answer (or ticks *Cevabı kâğıda yazdım* after writing it on paper), then sees a model answer and the scoring checklist from the answer key. The student ticks the points the answer covers, and the question counts as correct at 70% of the points or more.
- **Word hints:** old words in poems such as *yad*, *arif*, *mihman*, or *felek* are underlined; tapping one shows its meaning. The glossary lives in `docs/glossary-edb.json`.

Poems keep their line breaks in question cards and lessons; lesson steps can show a poem with the `poem` field.

### English Practice
The English course follows the 10th grade MEB coursebook: *Revision 1* (people, countries and capitals, personality, jobs), *Revision 2* (homes and smart houses), and *Theme 1: School Life & Education*. Questions are written in English and explained in Turkish. Topics:

- **★ Word List:** the coursebook word list, from *capital* and *generous* to *empathy* and *abroad*, with definitions, Turkish meanings, and phrases such as *not my cup of tea* and *think globally, act locally*. It sits at the top of the topic list.
- **Vocabulary topics:** People and Places, Homes and Smart Houses, Types of Schools, School Life (facilities, clubs, exam anxiety, and the theme's social language such as *Rise and shine!*), and Global Citizens (Erasmus+, eTwinning).
- **Grammar topics:** Present Simple & Continuous, Adverbs of Frequency, Question Tags, *Must* and *Can't* for deductions, Object & Indefinite Pronouns, and Intonation.
- **Reading, listening, and writing:** short texts with True / False / Not Mentioned questions, listening questions with times and numbers read aloud in British English, sentence building from Turkish, and open-ended writing tasks (a profile, a dream school, smart houses) with a scoring checklist.

All texts are written for the app; they practise the coursebook's vocabulary and structures without copying its reading or listening texts. English words in questions have word hints from `docs/glossary-ing.json`.

### Skipping Questions
Not sure about an answer? Leave the question blank with **Boş bırak**. The correct answer and explanation are shown right away, skipped questions do not lower your accuracy, and they come back more often in later rounds. Wrong and skipped questions can be repeated together at the end of a round.

### Topic Lessons
Every topic has a short, step-by-step lesson narrated by Mikey. Open it with the **Konu anlatımı** button next to a topic. Lessons borrow tricks from popular language apps to stay short and interactive:

- **Bite-sized steps:** each step opens one piece at a time; **Devam** reveals the next paragraph, formula, short list, or figure before moving on.
- **Flip cards:** two-column vocabulary tables become cards you tap to flip. German words can be played aloud.
- **Guess, then reveal:** in larger tables such as verb conjugations, only the first column is shown; tap a cell to check your guess, or use **Hepsini göster**.
- **Quick checks:** short questions appear inside the lesson with instant feedback and XP. They come from the step's `check` field or are generated from its vocabulary table, and **Devam** waits until you answer.
- **Final check and celebration:** each lesson ends with two questions from the topic's question bank and a summary of XP and accuracy. Finished lessons are marked with a check on the topic list, and the last screen leads straight into a practice round.

### Study Buddy
Mikey, a cheerful little mascot with a round golden head, joins every question and lesson across all subjects. It cheers when you get an answer right, gets sad when you miss one, stays calm when you skip, and celebrates answer streaks and finished rounds.

### Progress Tracking
See your topic accuracy and daily study streak. Progress is saved in your browser, so it stays available on the same browser and device.

## <div align="center">Question Banks</div>

- **Biology:** 90 questions across 4 topics
- **Chemistry:** 201 questions across 7 topics
- **Math:** 192 questions across 6 topics
- **German:** 212 questions across 8 topics
- **Literature:** 244 questions across 12 topics
- **English:** 234 questions across 12 topics

Question banks live in `docs/questions-bio.json`, `docs/questions-kim.json`, `docs/questions-mat.json`, `docs/questions-alm.json`, `docs/questions-edb.json`, and `docs/questions-ing.json`. Each entry includes an `id`, `unit`, `type`, question text (`q`), and explanation (`why`), plus fields specific to its question type:

| Type | Answer data |
| --- | --- |
| `mc`, `fill` | `choices` and a zero-based `answer` index |
| `tf` | Boolean `answer` (`true` or `false`) |
| `match`, `tiles` | `pairs`, each containing two values to match |
| `order` | `items` in the correct order |
| `build` | `words` in the correct order, optional distractor `extra` words, and optional `alt` word orders that also count as correct |
| `listen` | `tts` text read aloud and `blanks`, each with a `label` shown next to the box and a numeric `answer`; only digits are compared, so a time such as `7:30` also accepts `7.30` |
| `write` | `rubric`, a list of scoring points (`t` text and `p` points), and an optional `model` answer |

Any question can also carry an optional `fig` (a figure as a list of drawing commands) or `table` (`h` for the header row and `r` for the rows), a `gold` flag (`true` for golden exam questions), plus a `src` sentence shown in a card and a `tts` text that can be played aloud in the subject's language. In `build` questions, words other than nouns are stored in lowercase (in English, everything except `I` and proper nouns); the app capitalizes the first word of the sentence, and answers are compared without regard to case or punctuation. Figure coordinates are precomputed from the actual measurements given in each question.

Topic lessons live in `docs/lessons-bio.json`, `docs/lessons-kim.json`, `docs/lessons-mat.json`, `docs/lessons-alm.json`, `docs/lessons-edb.json`, and `docs/lessons-ing.json`, keyed by topic name. Each step has Mikey's line (`say`) and a `title`, plus optional `poem`, `text`, formulas (`f`), a bullet `list`, `fig`, `table`, a `tip`, a mascot `mood`, and a quick `check` (a question with `q`, `choices`, a zero-based `answer`, and `why`; leave out `choices` and use a boolean `answer` for true/false). A check can also be a list of such questions.

The app validates question and lesson entries when loading them and skips invalid entries.

## <div align="center">Technology</div>

The app is built with plain **HTML, CSS, and JavaScript**. It has no build step or package dependencies; the question banks are loaded as JSON files. The interface adapts to small screens, supports light and dark themes, and respects reduced-motion preferences.

## <div align="center">Getting Started</div>

You need Python 3 to serve the app locally. From the project root, run:

```bash
python -m http.server 8000 --directory docs
```

Then open [http://localhost:8000](http://localhost:8000) in your browser. On Windows, use `py -m http.server 8000 --directory docs` if the `python` command is unavailable.

The app uses `fetch` to load the question banks, so it must be served over HTTP rather than opened directly as a local file.

## <div align="center">Project Structure</div>

```text
docs/
├── glossary-alm.json
├── glossary-edb.json
├── glossary-ing.json
├── index.html
├── lessons-alm.json
├── lessons-bio.json
├── lessons-edb.json
├── lessons-ing.json
├── lessons-kim.json
├── lessons-mat.json
├── questions-alm.json
├── questions-bio.json
├── questions-edb.json
├── questions-ing.json
├── questions-kim.json
└── questions-mat.json
```

<div align="center">
  <i>Study a little, learn a lot.</i>
</div>
