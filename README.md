# Does This Make Me Look Fat? 🛋️

> A branching narrative game with no good answers. Only one path wins. Good luck finding it.

---

## What is this?

A deceptively deep question game built around loaded questions — the kind where every possible answer feels wrong. Players navigate a branching tree of passive-aggressive relationship questions, choosing between two responses at each stage.

The catch: one wrong turn doesn't immediately end the game. Instead, it silently poisons your path. You'll keep playing, answering question after question, convinced you're doing fine — until the inevitable sofa.

**There is exactly one path to victory. It is not the obvious one.**

---

## How to play

Open `index.html` in any browser. No install. No dependencies. No server required.

Or play it live at: *(add your Vercel/Netlify URL here once deployed)*

---

## The mechanics

- **15 questions** on the golden path to victory
- **3 doom corridors** of 5 questions each — shared across multiple wrong turns
- **One hidden variable** tracks how poisoned your path is; the heart icon in the corner very subtly reflects this
- **Wrong answers funnel** into shared doom corridors — two players who went wrong at completely different points may be answering identical questions without knowing it
- **The winning secret** is revealed only on victory — and it will surprise you

---

## Project structure

```
does-this-make-me-look-fat/
│
├── index.html          # The entire game — engine, content, and styles in one file
│
└── README.md           # You are here
```

The game is intentionally a single file for now. As it grows, it will be split into:

```
src/
├── engine.js           # Game state, branching logic, doom mechanics
├── questions.json      # The entire question tree — the content bible
└── styles.css          # Visual design and animations

index.html              # Shell only — imports the above
```

---

## The team & who owns what

| Area | Owner | What to touch |
|---|---|---|
| Game engine & mechanics | *[game designer friend]* | `engine.js` — state management, branching logic, poison mechanic |
| Question tree & content | *[creative friend]* + Brad | `questions.json` — all questions, answers, and branching paths |
| Visual design & UI | Brad | `styles.css` — typography, colour, animation, tone |

---

## Contributing — how we work

### Adding questions

The question tree lives in the `TREE` object inside `index.html` (soon `questions.json`). Each node looks like this:

```json
{
  "q99": {
    "q": "Your question text here.",
    "a": [
      { "t": "Answer option A", "n": "next_node_id" },
      { "t": "Answer option B", "n": "another_node_id" }
    ]
  }
}
```

To add a doom corridor node, add `"doom": 1` to the node object. This increments the hidden poison score and subtly dims the heart icon.

### Golden path rules

- The golden path node IDs run `q1` through `q15` and terminate at `WIN`
- Golden path answers should be counter-intuitive — uncomfortable honesty wins, smooth reassurance loses
- Every other answer should eventually route to `SOFA` via a doom corridor
- Doom corridor nodes are prefixed `da`, `db`, `dc` etc.

### Git workflow

- Work on a branch: `git checkout -b your-name/what-youre-doing`
- Keep commits small and descriptive
- Open a pull request when ready — don't push directly to `main`

---

## Roadmap

- [ ] Add `index.html` game file to repo
- [ ] Expand question tree to 40+ golden path questions
- [ ] Split into `engine.js` / `questions.json` / `styles.css`
- [ ] Deploy to Vercel with shareable URL
- [ ] Add Open Graph share card for WhatsApp/Twitter previews
- [ ] Add analytics (question drop-off tracking, win rate)
- [ ] iOS & Android (React Native port — after web version validated)
- [ ] Leaderboard: "furthest question reached" public shame board
- [ ] Multiple scenarios beyond the original (the restaurant, the family holiday, the group chat...)

---

## The design philosophy

The game should feel like it's on your side right up until it isn't. Questions should be recognisable. Answers should feel reasonable. The doom should creep, not slam.

The tone is: **dry, cutting, and entirely plausible.** Not cartoonish. Not absurd. The kind of thing that actually gets said.

---

## License

MIT — do what you want with it, just credit the original.

Built with 🛋️ and regret.
