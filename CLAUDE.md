# CLAUDE.md - Tuneiversity (Mandarin Pronunciation Tutor)

## Project Overview

AI-powered Mandarin pronunciation tutor that helps users practice Chinese pronunciation through song lyrics. Users record themselves reading lyrics line-by-line and receive clarity/tone feedback. Currently a UI prototype with mock scoring — no backend or real audio analysis yet.

## Tech Stack

- **Framework:** Next.js 16 (App Router, Turbopack)
- **Language:** TypeScript (strict mode)
- **Styling:** Tailwind CSS 3 (class-based dark mode, CSS variables)
- **UI Components:** Shadcn/ui (Radix UI primitives) in `components/ui/`
- **Icons:** Lucide React
- **Fonts:** Inter (sans), Noto Sans SC (Chinese characters)
- **Package Manager:** pnpm

## Commands

- `pnpm dev` — Start dev server (Turbopack, port 3000)
- `pnpm build` — Production build
- `pnpm start` — Start production server
- `pnpm lint` — Run ESLint

## Project Structure

```
app/
  layout.tsx          # Root layout (fonts, metadata)
  page.tsx            # Main practice page (core app logic)
  globals.css         # Global styles, CSS variables
components/
  ui/                 # Shadcn/ui primitives (~52 components)
  audio-controls.tsx  # Recording & playback with waveform animation
  lyrics-display.tsx  # Character/pinyin display with tone colors
  practice-header.tsx # Song info, progress bar, video
  feedback-section.tsx# Clarity score display
  verse-mode.tsx      # Full verse practice mode
  song-report.tsx     # Performance report with recommendations
hooks/                # Custom hooks (use-toast, use-mobile)
lib/utils.ts          # cn() utility (clsx + twMerge)
```

## Code Conventions

- All interactive components use `"use client"` directive
- Named exports (not default exports)
- Props interfaces suffixed with `Props`
- Tailwind-only styling; use `cn()` for conditional class merging
- Path alias: `@/*` maps to project root
- State management via React hooks only (useState, useCallback) — no global state library
- Mobile-first responsive design (`max-w-lg`, `md:` breakpoints)

## Tone Color System

Pinyin characters map to tones via regex detection:
- Tone 1 (ā ē ī ō ū ǖ) → `text-primary` (teal)
- Tone 2 (á é í ó ú ǘ) → `text-chart-5` (orange)
- Tone 3 (ǎ ě ǐ ǒ ǔ ǚ) → `text-chart-3` (gray)
- Tone 4 (à è ì ò ù ǜ) → `text-destructive` (red)

## Notes

- TypeScript build errors are currently ignored in `next.config.mjs` (`ignoreBuildErrors: true`)
- Song data is hardcoded in `page.tsx` (小幸运 by Hebe Tien)
- Audio recording, AI analysis, database, and auth are not yet implemented — all feedback is mock data
- No test framework is configured
