# The Diverse Candidate

Tools for data center and power systems commissioning, built by a
commissioning manager. Two threads of work, one shared knowledge base.

## Thread 1: Commissioning knowledge and the tools that deliver it

The source of truth is a hand-authored MV switchgear commissioning
workbook plus a curated set of California commissioning regulatory
citations. Everything below either stores that knowledge or hands it to
someone who needs it during a project.

| Repo | What it is | State |
|---|---|---|
| [GenesisAI](https://github.com/thediversecandidate/GenesisAI) | The hub. Ingests the workbook and regulatory citations into a full-text index and serves cited passages over a small HTTP API. Retrieval only, no LLM, every result traces to a source section. | Working, tested |
| [cxms-platform](https://github.com/thediversecandidate/cxms-platform) | Commissioning management backend (FastAPI + PostgreSQL). Models assets, signed gate snapshots, documentation-tier revision events, and the regulatory rules engine that GenesisAI's citations are curated from. | Backend and tests, no frontend yet |
| [EmailAnalysis](https://github.com/thediversecandidate/EmailAnalysis) | Thin client of GenesisAI. Classifies a project email (RFI, NCR, test report, schedule, question) and assembles a reply from cited passages. | Working end to end; no live inbox yet |
| [Realtime-voice-feedback-AI](https://github.com/thediversecandidate/Realtime-voice-feedback-AI) | Thin client of GenesisAI. Watches a call transcript and surfaces cited passages when a substantive question is asked. | Working end to end; no live audio yet |

The workbook and test template themselves currently live in a private
config repo and are copied into GenesisAI's `knowledge/` folder. Moving
them into a public repo of their own is planned.

## Thread 2: Tech news scraping and search

An earlier line of work: crawl data center industry news, store and index
it, and search it. GenesisAI has a stubbed source for pulling this feed in
as a fourth knowledge source, pending an API token rotation.

| Repo | What it is | State |
|---|---|---|
| [Webscraping](https://github.com/thediversecandidate/Webscraping) | Django 5.2 REST API. Crawls tech news sites into PostgreSQL, indexes into Elasticsearch, runs jobs with Celery. | Working; needs Postgres, Elasticsearch, Redis |
| [webscraper-React-FrontEnd](https://github.com/thediversecandidate/webscraper-React-FrontEnd) | React + Vite search UI for the Django API: search, article list, word cloud, timeline. Ships several experimental local backends, some of which return mock data and are labeled as such. | Working, 0 npm audit findings |
| [ElasticSearchPOC](https://github.com/thediversecandidate/ElasticSearchPOC) | macOS SwiftUI client for the same Django API. | Proof of concept |
| [SwiftWebCrawlerUI](https://github.com/thediversecandidate/SwiftWebCrawlerUI) | Standalone iOS app that runs a breadth-first crawler on device. Not connected to the Django API. | Prototype, known thread-safety bug |

## Scaffolding and learning repos

These contain templates, tutorials, or single demo scripts, not product
code. Kept for history.

`SwiftServerSideScraper` (unmodified Vapor template, not a scraper),
`Webscraping-Maketing` (one example.com fetch), `Python-BeautifulSoup-`
(one DataCamp notebook), `my-first-project` (unmodified NVIDIA AI Workbench
template), `github-slideshow` and `desktop-tutorial` (GitHub tutorials),
plus forks of `conda`, `Critical-Path-Method`, `sitemap-visualization-tool`,
`Latest-News-Classifier`, and `aws-elastic-beanstalk-express-js-sample`.

## Principles across all repos

- Retrieval before generation. Tools return real, cited source material.
  Anything synthesized or mocked is labeled as such, never blended in.
- No secrets in tracked files. Config comes from environment variables.
- Every repo carries a `CLAUDE.md` describing what it is, what it
  deliberately does not do yet, and how to run its tests.
