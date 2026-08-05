# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A GitHub profile repo (repo name matches the `thediversecandidate`
account/org name, so its README renders on the GitHub profile page) meant
to index the other `thediversecandidate` projects — currently listing
GenesisAI, Realtime-voice-feedback-AI, EmailAnalysis, and itself as a "meta
repository coordinating all sub-projects."

## Current state — two things worth knowing before touching this repo

- **There is no active `README.md`.** The intended profile content lives in
  `README_backup.md` instead — GitHub only renders a file literally named
  `README.md` on the profile page, so as committed, the profile page is not
  showing this content. If asked to fix/update the profile page, that likely
  means renaming/restoring `README_backup.md` to `README.md` — but that's a
  visible, public-facing change, so confirm with the user before doing it
  rather than assuming it's a wanted side effect of an unrelated edit.
- **`index.html` is a stray file.** It's the default Create React App
  template shell (`<title>WebScraper React Frontend</title>`, `%PUBLIC_URL%`
  placeholders) — it belongs to the `webscraper-React-FrontEnd` repo's
  `public/index.html` and appears to have been committed here by mistake.
  It isn't part of this repo's actual purpose (a profile README) and
  doesn't do anything on its own without the React build pipeline it's
  missing.

## Working here

This repo's only real content is the project-index table. When one of the
listed sub-projects changes (renamed, archived, new project added), update
`README_backup.md` (or `README.md`, once restored) — there's no other
generated or templated source for that table.
