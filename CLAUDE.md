# CLAUDE.md — Nalarin Learn Architecture & Development Guidelines

Nalarin Learn adalah platform pembelajaran interaktif Tes Kemampuan Akademik (TKA) Matematika berbasis penalaran konseptual (*"Bukan cuma hafalin. Nalarin"*).

---

## 1. Tech Stack & Dependensi Inti
- **Framework:** Next.js (App Router, TypeScript, React 19)
- **Styling:** Tailwind CSS (Mobile-first, Dark mode default via class/media)
- **Notasi Matematika:** `react-katex` & `katex` (Stylesheet: `katex/dist/katex.min.css`)
- **Backend & Database:** Firebase SDK (Authentication, Cloud Firestore, Firebase Storage)
- **AI Runtime:** `@google/genai` (Gemini Flash untuk endpoint route handler server-side)
- **Icons:** `lucide-react` (jika diperlukan)

---

## 2. Struktur Direktori Proyek
Proyek ini menggunakan struktur root direktori langsung tanpa folder `src/`:

```text
nalarin-learn/
├── app/                      # Next.js App Router (pages & API routes)
│   ├── api/                  # Server-side API handlers (Gemini runtime, AI hint)
│   │   ├── hint/route.ts
│   │   └── diagnose/route.ts
│   ├── lesson/[id]/page.tsx  # Dynamic route untuk halaman materi
│   ├── quiz/[domain]/page.tsx# Dynamic route untuk domain mastery quiz
│   ├── studio/page.tsx       # CMS publisher internal
│   ├── layout.tsx            # Root layout & global providers
│   ├── globals.css           # Global Tailwind CSS + KaTeX import
│   └── page.tsx              # Homepage / Library discovery
├── components/               # Reusable React components
│   ├── LessonRenderer.tsx    # Core dynamic block parser
│   ├── Navbar.tsx            # Navigation, dark mode toggle, user auth state
│   ├── interactive/          # MiniChallenge, multiple choices, quizzes
│   └── simulations/          # Canvas / SVG visualizers (NumberLine, etc.)
├── context/                  # React Contexts (AuthContext.tsx, ThemeContext.tsx)
├── lib/                      # Helper & initializations (firebase.ts, gemini.ts)
├── types/                    # TypeScript interfaces & types (lesson.ts, quiz.ts)
├── public/                   # Static assets
├── .env.local                # Secret keys (Git-ignored)
└── CLAUDE.md                 # Agent development guidelines