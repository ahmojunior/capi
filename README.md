<div align="center">

# capi

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

</div>

## <div align="center">About the Project</div>

**capi** is a Turkish-language study app for reviewing biology, chemistry, math, and German with short, interactive quizzes. Choose a subject, practice across all its topics or focus on one, and review explanations after each answer.

For one class (about 30 students) it also offers shared features backed by Firebase: sign-in with a nickname and PIN, a study timer, a class leaderboard, and a shared homework and events list. The quizzes never depend on them: without internet, or if Firebase fails to load, every quiz still works.

## <div align="center">Features</div>

### Flexible Practice
Start a mixed round or choose a specific topic. Each round contains up to 10 questions, and questions you miss or have not seen are more likely to appear in future rounds.

### Multiple Question Types
Practice with multiple-choice, fill-in-the-blank, true/false, matching, and ordering questions. Many math questions come with a geometric figure, chart, or data table. Every answer includes feedback and an explanation.

### German Practice
The German course follows the *Essen und Trinken* unit: food vocabulary and articles, plurals, meals, likes and dislikes, shopping, prices, and recipes. Besides the usual question types it adds two Duolingo-style exercises:

- **Sentence building:** tap word blocks to build a sentence. The bank includes distractor blocks, a used block leaves an empty space behind, and other correct word orders are accepted too.
- **Tile matching:** match pictures or words in a two-column grid. Correct pairs turn green right away, wrong pairs shake red, and the question counts as correct only without mistakes.

German sentences can be played aloud with the speaker button, using the browser's built-in speech synthesis.

### Skipping Questions
Not sure about an answer? Leave the question blank with **Boş bırak**. The correct answer and explanation are shown right away, skipped questions do not lower your accuracy, and they come back more often in later rounds. Wrong and skipped questions can be repeated together at the end of a round.

### Topic Lessons
Every topic has a short, step-by-step lesson narrated by Mikey. Open it with the **Konu anlatımı** button next to a topic; each step has a key idea, formulas, examples, and figures where helpful, and the last step leads straight into a practice round for that topic.

### Study Buddy
Mikey, a cheerful little mascot with a round golden head, joins every question and lesson across all subjects. It cheers when you get an answer right, gets sad when you miss one, stays calm when you skip, and celebrates answer streaks and finished rounds.

### Progress Tracking
See your topic accuracy and daily study streak. Progress is saved in your browser, so it stays available on the same browser and device. This local progress is separate from the class leaderboard and is never uploaded.

## <div align="center">Class Features</div>

The app has four tabs: **Çalış** (the quizzes), **Zamanlayıcı**, **Sıralama**, and **Ödevler**. The header greets the signed-in student ("Merhaba, Deniz!") and has a **Çıkış yap** button.

### Sign-In
Students sign in with their nickname from the class list and a 6-digit PIN. **Giriş** signs in to an existing account, and **İlk kez giriyorum** creates one, asking for the PIN twice. A nickname that is not on the class list is rejected before anything is sent to the server. Students stay signed in on their device.

**Giriş yapmadan devam et** opens guest mode: quizzes work as usual, but nothing is recorded for the leaderboard. If Firebase cannot be loaded, the app opens in guest mode on its own.

### Study Timer
**Başlat**, **Duraklat**, and **Sıfırla** control a large HH:MM:SS clock. It counts only while the page is visible: switching tabs or locking the phone pauses it, and it continues when you come back. Study time is saved about every 2 minutes, and the app also tries to save when you pause or leave the page. Time that cannot be saved yet (for example, when offline) waits on the device and is added later. **Sıfırla** clears the clock but never removes time that was already saved.

### Questions Solved
Every correct quiz answer of a signed-in student counts toward the leaderboard. Wrong and skipped answers do not count. Answers are saved in batches together with study time.

### Leaderboard
**Sıralama** ranks the class by correct answers or by study time, either this week or for all time. Weeks run from Monday to Sunday in Turkish time (Europe/Istanbul). Students with the same score share a rank, and your own row is highlighted.

### Homework and Events
**Ödevler** is a shared list of homework (**Ödev**) and events (**Etkinlik**) that every signed-in student can add, edit, and delete. Each card reads like *"Matematik Ders Kitabı – 55 ile 60. sayfaları tamamla – Son: 11/11/2026 – 4 gün kaldı"* and shows who added and who last edited it. Items are sorted by date and can be filtered by type. They stay visible until 7 days after their date.

Deleting asks **Emin misin?** first and moves the item to **Silinenler**, where anyone can restore it with **Geri al** for 7 days. Nothing is ever permanently deleted from the database.

### When the Server Is Unreachable
The leaderboard and homework pages show *"Sunucuya bağlanırken hata oluştu, ahmojunior ile iletişime geç."* when the server cannot be reached. The quizzes are not affected.

## <div align="center">Question Banks</div>

- **Biology:** 90 questions across 4 topics
- **Chemistry:** 201 questions across 7 topics
- **Math:** 192 questions across 6 topics
- **German:** 172 questions across 7 topics

Question banks live in `docs/questions-bio.json`, `docs/questions-kim.json`, `docs/questions-mat.json`, and `docs/questions-alm.json`. Each entry includes an `id`, `unit`, `type`, question text (`q`), and explanation (`why`), plus fields specific to its question type:

| Type | Answer data |
| --- | --- |
| `mc`, `fill` | `choices` and a zero-based `answer` index |
| `tf` | Boolean `answer` (`true` or `false`) |
| `match`, `tiles` | `pairs`, each containing two values to match |
| `order` | `items` in the correct order |
| `build` | `words` in the correct order, optional distractor `extra` words, and optional `alt` word orders that also count as correct |

Any question can also carry an optional `fig` (a figure as a list of drawing commands) or `table` (`h` for the header row and `r` for the rows), plus a `src` sentence shown in a card and a `tts` text that can be played aloud in the subject's language. In `build` questions, words other than nouns are stored in lowercase; the app capitalizes the first word of the sentence, and answers are compared without regard to case or punctuation. Figure coordinates are precomputed from the actual measurements given in each question.

Topic lessons live in `docs/lessons-bio.json`, `docs/lessons-kim.json`, `docs/lessons-mat.json`, and `docs/lessons-alm.json`, keyed by topic name. Each step has Mikey's line (`say`) and a `title`, plus optional `text`, formulas (`f`), a bullet `list`, `fig`, `table`, a `tip`, and a mascot `mood`.

The app validates question and lesson entries when loading them and skips invalid entries.

## <div align="center">Technology</div>

The app is built with plain **HTML, CSS, and JavaScript**. It has no build step or package dependencies; the question banks are loaded as JSON files. The interface adapts to small screens, supports light and dark themes, and respects reduced-motion preferences.

The class features use **Firebase Authentication** (email and password) and **Cloud Firestore** on the free Spark plan. The Firebase modular SDK (version 13.1.0) is loaded from `www.gstatic.com` inside a `<script type="module">`, so there is still no build step. The page works without it.

## <div align="center">Firebase Setup</div>

Do these steps once in the [Firebase console](https://console.firebase.google.com/) for the `capi-study` project.

1. **Web API key.** In *Project settings → General → Your apps*, copy the web app's `apiKey` and paste it into `firebaseConfig` near the end of `docs/index.html`, replacing `BURAYA_FIREBASE_API_ANAHTARINI_YAPISTIR`. The web config is public by design; the security rules protect the data.
2. **Sign-in method.** In *Authentication → Sign-in method*, enable **Email/Password**. Leave Anonymous disabled. Keep *Email enumeration protection* on (*Authentication → Settings → User actions*).
3. **Authorized domains.** In *Authentication → Settings → Authorized domains*, add your GitHub Pages domain, for example `ahmojunior.github.io`. `localhost` is already listed for local testing.
4. **Security rules.** In *Firestore Database → Rules*, replace everything with the contents of [`firebase/firestore.rules`](firebase/firestore.rules) and select **Publish**.
5. **Class list.** Edit [`docs/students.json`](docs/students.json) (see below) and push it.
6. **Admin bootstrap.** The security rules read the class list from Firestore, so the first admin has to be added by hand. In *Firestore Database → Data*, start a collection named `students` and add one document:
   - Document ID: your student ID (see below), for example `mikey` for the nickname `Mikey`
   - Field `alias` (string): your nickname exactly as in `students.json`, for example `Mikey`
   - Field `admin` (boolean): `true`
7. **First sign-in and sync.** Open the app, choose **İlk kez giriyorum**, and create your account with your nickname and a PIN. Then open **Ayarlar** in the header (visible only to admins) and select **Sınıf listesini senkronize et**. This writes every student from `students.json` to Firestore. Run it again whenever you change the class list.

### The Class List
`docs/students.json` lists every student who may sign in:

```json
{
  "students": [
    { "alias": "Mikey", "admin": true },
    { "alias": "Deniz", "admin": false }
  ]
}
```

- `alias` is the nickname students type and see (up to 40 characters).
- `admin: true` lets that student run the class list sync.
- Each student's ID is made from the nickname: it is lowercased the Turkish way, `ç ğ ı ö ş ü` become `c g i o s u`, other accents are dropped, and anything other than `a–z` and `0–9` is removed. "Çağlar", "çağlar", and "CAGLAR" all become `caglar`. If two nicknames give the same ID, or a nickname gives an empty ID, the later entry is skipped and an error is printed in the browser console.
- Removing a student from the file and syncing does not delete them from Firestore. To remove someone, delete their `students/<id>` document in the console.

### Accounts and PINs
Each account is a Firebase Authentication user with the email `<id>@capi-study.app`. This address is not real and no email is ever sent. The 6-digit PIN is the account password. Firebase Authentication stores and checks it; the app never saves or logs PINs, and they are never written to the browser's storage. Very easy PINs such as `000000` or `123456` are refused.

If a student forgets their PIN, delete the user `<id>@capi-study.app` in *Authentication → Users*. The student then signs up again with **İlk kez giriyorum**. Their leaderboard scores are kept, because scores are stored by student ID.

### Data Model
| Collection | Fields | Who can write |
| --- | --- | --- |
| `students/{id}` | `alias`, `admin` | Admins (create and update) |
| `stats/{id}` | `alias`, `totalCorrect`, `totalSeconds`, `weekKey` (e.g. `2026-W45`), `weekCorrect`, `weekSeconds`, `updatedAt` | Only the student with that ID |
| `tasks/{autoId}` | `type` (`homework` or `event`), `subject`, `title`, `description`, `dueDate`, `createdBy`, `createdByAlias`, `createdAt`, and when set `editedBy`, `editedByAlias`, `editedAt`, `deletedAt`, `deletedBy` | Every student on the class list |

All data can be read only by signed-in students on the class list. Nothing can be hard-deleted.

### Score Limits
The rules check every save so that scores cannot be faked casually:

- Totals never decrease, and the `alias` must match the class list, so nobody can post under another student's name.
- Study time can be added only when at least 60 seconds have passed since the previous save, and by at most the time that really passed plus 60 seconds.
- Correct answers grow by at most 25 per save, need at least 10 seconds since the previous save, and cannot grow faster than about one every 2 seconds.
- Weekly values reset only when the week changes, and only to the current week in Turkish time.

The app follows these limits on its own: whatever cannot be saved yet waits on the device for the next save.

### Known Limitations
- The class list is public (`docs/students.json`), so anyone who knows a nickname could create that account before the real student does. Ask everyone to sign up early. If an account is taken by the wrong person, delete it in *Authentication → Users*.
- A 6-digit PIN is short. Firebase slows down repeated wrong attempts, but students should not share or reuse their PIN.
- The score limits make cheating slow and visible, not impossible. Someone who scripts saves can still add time at up to about twice the real rate.
- Studying on two devices at the same time can make some saves wait longer.

### Testing Locally with the Emulators
With the [Firebase CLI](https://firebase.google.com/docs/cli) installed (it is not needed for the app itself), you can try the class features without touching the real project:

```bash
firebase emulators:start --only auth,firestore --project capi-study
```

Then serve the app as described in Getting Started and open [http://localhost:8000/?emulator](http://localhost:8000/?emulator). On `localhost`, the `?emulator` parameter connects the app to the local emulators instead of Firebase. The emulators need a format-valid `apiKey` in `docs/index.html`, but they accept any value.

## <div align="center">Getting Started</div>

You need Python 3 to serve the app locally. From the project root, run:

```bash
python -m http.server 8000 --directory docs
```

Then open [http://localhost:8000](http://localhost:8000) in your browser. On Windows, use `py -m http.server 8000 --directory docs` if the `python` command is unavailable.

The app uses `fetch` to load the question banks, so it must be served over HTTP rather than opened directly as a local file.

## <div align="center">Project Structure</div>

```text
docs/                  published site (GitHub Pages)
├── index.html
├── students.json      class list
├── lessons-alm.json
├── lessons-bio.json
├── lessons-kim.json
├── lessons-mat.json
├── questions-alm.json
├── questions-bio.json
├── questions-kim.json
└── questions-mat.json
firebase/              not published
└── firestore.rules    Firestore security rules
```

<div align="center">
  <i>Study a little, learn a lot.</i>
</div>
