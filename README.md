<div align="center">

# capi

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

</div>

## <div align="center">About the Project</div>

**capi** is a Turkish-language study app for reviewing biology, chemistry, and math with short, interactive quizzes. Choose a subject, practice across all its topics or focus on one, and review explanations after each answer.

## <div align="center">Features</div>

### Flexible Practice
Start a mixed round or choose a specific topic. Each round contains up to 10 questions, and questions you miss or have not seen are more likely to appear in future rounds.

### Multiple Question Types
Practice with multiple-choice, fill-in-the-blank, true/false, matching, and ordering questions. Many math questions come with a geometric figure, chart, or data table. Every answer includes feedback and an explanation.

### Skipping Questions
Not sure about an answer? Leave the question blank with **Boş bırak**. The correct answer and explanation are shown right away, skipped questions do not lower your accuracy, and they come back more often in later rounds. Wrong and skipped questions can be repeated together at the end of a round.

### Topic Lessons
Every topic has a short, step-by-step lesson narrated by Mikey. Open it with the **Konu anlatımı** button next to a topic; each step has a key idea, formulas, examples, and figures where helpful, and the last step leads straight into a practice round for that topic.

### Study Buddy
Mikey, a cheerful little mascot with a round golden head, joins every question and lesson across all subjects. It cheers when you get an answer right, gets sad when you miss one, stays calm when you skip, and celebrates answer streaks and finished rounds.

### Progress Tracking
See your topic accuracy and daily study streak. Progress is saved in your browser, so it stays available on the same browser and device.

## <div align="center">Question Banks</div>

- **Biology:** 90 questions across 4 topics
- **Chemistry:** 201 questions across 7 topics
- **Math:** 192 questions across 6 topics

Question banks live in `docs/questions-bio.json`, `docs/questions-kim.json`, and `docs/questions-mat.json`. Each entry includes an `id`, `unit`, `type`, question text (`q`), and explanation (`why`), plus fields specific to its question type:

| Type | Answer data |
| --- | --- |
| `mc`, `fill` | `choices` and a zero-based `answer` index |
| `tf` | Boolean `answer` (`true` or `false`) |
| `match` | `pairs`, each containing two values to match |
| `order` | `items` in the correct order |

Any question can also carry an optional `fig` (a figure as a list of drawing commands) or `table` (`h` for the header row and `r` for the rows). Figure coordinates are precomputed from the actual measurements given in each question.

Topic lessons live in `docs/lessons-bio.json`, `docs/lessons-kim.json`, and `docs/lessons-mat.json`, keyed by topic name. Each step has Mikey's line (`say`) and a `title`, plus optional `text`, formulas (`f`), a bullet `list`, `fig`, `table`, a `tip`, and a mascot `mood`.

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
├── index.html
├── lessons-bio.json
├── lessons-kim.json
├── lessons-mat.json
├── questions-bio.json
├── questions-kim.json
└── questions-mat.json
```

<div align="center">
  <i>Study a little, learn a lot.</i>
</div>
