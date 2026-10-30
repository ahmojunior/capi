<div align="center">

# Yazılı Antrenman

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![JSON](https://img.shields.io/badge/Question_Banks-JSON-5E5E5E?style=for-the-badge)

</div>

## <div align="center">About the Project</div>

**Yazılı Antrenman** is a Turkish-language study app for reviewing biology and chemistry with short, interactive quizzes. Choose a subject, practice across all its topics or focus on one, and review explanations after each answer.

## <div align="center">Features</div>

### Flexible Practice
Start a mixed round or choose a specific topic. Each round contains up to 10 questions, and questions you miss or have not seen are more likely to appear in future rounds.

### Multiple Question Types
Practice with multiple-choice, fill-in-the-blank, true/false, matching, and ordering questions. Every answer includes feedback and an explanation; missed questions can be repeated at the end of a round.

### Progress Tracking
See your topic accuracy and daily study streak. Progress is saved in your browser, so it stays available on the same browser and device.

## <div align="center">Question Banks</div>

- **Biology:** 90 questions across 4 topics
- **Chemistry:** 201 questions across 7 topics

Question banks live in `docs/questions-bio.json` and `docs/questions-kim.json`. Each entry includes an `id`, `unit`, `type`, question text (`q`), and explanation (`why`), plus fields specific to its question type:

| Type | Answer data |
| --- | --- |
| `mc`, `fill` | `choices` and a zero-based `answer` index |
| `tf` | Boolean `answer` (`true` or `false`) |
| `match` | `pairs`, each containing two values to match |
| `order` | `items` in the correct order |

The app validates question entries when loading the banks and skips invalid entries.

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
├── questions-bio.json
└── questions-kim.json
```

<div align="center">
  <i>Study a little, learn a lot.</i>
</div>
