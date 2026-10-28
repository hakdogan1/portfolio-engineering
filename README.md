# Hasan Akdogan — Portfolio Engineering

**A personal engineering portfolio built and operated like a real production system** — a working project with its own test suite, CI pipeline, and a custom-built, safety-first deployment process, documented here as a technical case study rather than a static resume page.

`PHP` `TypeScript` `Vite` `Playwright` `Python` `GitHub Actions`

**Live site:** [www.hakdogan.com](https://www.hakdogan.com/) · **QA Handbook:** [/qa-handbook](https://www.hakdogan.com/qa-handbook/) · **Test Automation:** [/test-automation](https://www.hakdogan.com/test-automation/) · **QA Practice:** [qapractice.hakdogan.com](https://qapractice.hakdogan.com/)

### At a Glance

| | |
|---|---|
| Deployment engine test suite | 43 targeted safeguard tests |
| Isolated release rehearsal | 168 files exercised, including interrupted-deployment recovery |
| First production deployment | Completed and verified — October 28, 2026 |

---

## 1. Project Purpose & Engineering Objectives

This project exists to demonstrate QA and software engineering skill through working software rather than a list of claims. Every section below is backed by real, running code, automated tests, and a documented engineering process.

The objectives behind the project:
- Build a fast, accessible, maintainable static site without unnecessary framework overhead.
- Treat quality assurance as a feature visitors can interact with, not just a claim on a résumé.
- Operate a deployment pipeline with the rigor a production system handling real user traffic would require, even on a personal project.

## 2. Key Features & Interactive QA Demonstrations

- **QA Handbook** — a structured reference covering the SDLC, STLC, test strategy, test planning, test case design, and QA terminology, written as practical guidance.
- **Interactive QA labs** — small TypeScript/Vite applications that let a visitor practice QA work directly in the browser: a guided bug-finding exercise, a simplified CI pipeline simulator, and an API-mocking exercise.
- **AI-assisted chat feature** — a chat assistant backed by a PHP API endpoint with its own request-rate limiting, answering visitor questions about the site's content.
- **Digital business card** — a self-contained contact page, exportable as a standard contact file.
- **QA Practice** — a separate, dedicated site offering hands-on exercises for QA learners, covering UI testing, form scenarios, and framework fundamentals with Playwright and TypeScript.

## 3. Technical Architecture & Technologies

- **Frontend:** semantic HTML, CSS, and vanilla JavaScript for the core site; TypeScript compiled with Vite for the interactive labs, built as isolated, independently buildable bundles.
- **Backend:** PHP for the small set of endpoints that need server-side logic — contact form delivery and the rate-limited chat API — kept narrow and single-purpose rather than built on a general framework.
- **Testing:** Playwright for browser-level regression checks, Python for release-provenance and link/SEO checks, and PHP for the deployment engine's own safeguard tests.
- **CI/CD:** GitHub Actions running a multi-language pipeline (Node.js, Python, PHP) on every push and pull request.
- **Deployment:** a custom-built, manually-triggered deployment engine, written in PHP because it's the only reliable CLI runtime available on the hosting account, which has no SSH, SFTP, or rsync access.

Each choice matches the actual constraints of the hosting environment rather than technology preference for its own sake.

## 4. QA Strategy, Test Automation & Quality Checks

- **Browser regression tests (Playwright):** verify key pages and interactive features behave correctly, run against local servers in CI so results are deterministic.
- **Static content validation:** automated checks of internal links and SEO hygiene across every page, run in CI so a broken link or missing metadata fails the build before reaching production.
- **Deployment engine test suite (PHP):** 43 targeted safeguard tests covering the deployment engine itself — backup and restore correctness, permission handling, interrupted-deployment recovery, and deliberate misuse scenarios such as an expired or tampered approval. This suite runs twice in CI, once with PHP's `symlink()` function disabled, matching a real limitation of the hosting environment and confirming the engine's symlink protections hold without it.
- **Release provenance checks (Python):** confirm that what CI builds matches exactly what the deployment manifest expects, so no untracked or mismatched file can slip through.

## 5. CI/CD and Guarded Production Deployment

Every push and pull request runs the full CI pipeline above. **A passing CI run does not deploy anything by itself.** Deployment is a deliberate, manually-triggered action, gated by several independent checks:

1. CI must be green on the exact commit intended for release, producing a **SHA-256 hash-verified release receipt** — a per-file content hash, not a cryptographic signature. It proves file integrity between CI and the server, not authenticity on its own; the operator still has to manually confirm it came from a trusted, authenticated CI run.
2. An operator manually pulls that exact commit onto the server and manually triggers the deployment task. No webhook, cron job, or automatic trigger exists anywhere in the pipeline.
3. The deployment engine independently re-verifies the receipt against the files it's about to copy and refuses to proceed on any mismatch.
4. A separate, single-use, time-limited approval record — created fresh for that one release, including a recent check of available server storage — must be present and valid. It's consumed the moment it's used and can't be replayed.

This was a deliberate design decision: on shared hosting with no SSH access, the usual "push to deploy" convenience isn't available, and recreating it artificially would have meant weakening the review step a production deployment deserves.

## 6. Deployment Safety, Rollback, and Verification

The deployment engine only ever touches an explicit, reviewed list of files — never a wildcard copy, and never a deletion of anything it doesn't recognize. A short list of critical files (including the site's server configuration file) is excluded from being overwritten entirely and is instead hash-verified before, during, and after any deployment; a mismatch stops the process rather than proceeding silently.

Before any file is replaced, the engine backs it up and verifies that backup's integrity. Every change is staged privately and hash-verified before it touches a live file, with replacement happening one file at a time and each step recorded — so an interruption midway leaves a resumable trail instead of a half-finished site. Recovery uses the same approval mechanism: a rollback requires its own fresh, explicit approval, restores exactly what changed, and never deletes a file it can't positively identify.

**Validation history:**
- The engine — including backup, rollback, and two deliberately injected mid-deployment failures — was first exercised end-to-end in a fully isolated rehearsal on the real hosting account, using a private location that never touched the live site. This proved the recovery path before it was ever needed for real.
- The first real production deployment through this pipeline completed on October 28, 2026 (commit `8c3816f643bc6019e64ea3d453e9304e0ab6e7a3`), recorded as verified. Manual post-deployment HTTPS smoke tests confirmed the main website and both protected sites responded with HTTP 200, confirming the deployment didn't affect anything outside its intended scope.

## 7. Engineering Challenges and Solutions

- **No SSH, SFTP, or rsync on the hosting account.** Solved by building the deployment mechanism around the one capability the host does offer — pulling a Git commit and running a PHP CLI task — rather than working around the limitation with something riskier.
- **No cryptographic signing available on this host to prove a deployment's authenticity.** Solved with the SHA-256 release receipt and manual operator confirmation covered in Section 5, rather than assuming a stronger guarantee the hosting environment can't actually provide.
- **Risk of a deployment overwriting server-only configuration or another hosted site.** Solved with an explicit, reviewed file list, hash-guarded protected files, and filesystem checks that refuse to write near another hosted site's directory.
- **`symlink()` unavailable in the hosting environment's PHP configuration.** The test suite runs twice — once simulating the missing function — to prove the engine's symlink defenses hold without it, rather than skip that protection.
- **Validating a risky, hard-to-reverse process safely.** Solved by building a separate rehearsal harness that runs the real, unmodified deployment engine against private, isolated fixtures — including injected failures — so the recovery path was proven before the first real release.

## 8. Evidence and Live Links

- Website: https://www.hakdogan.com/
- QA Handbook: https://www.hakdogan.com/qa-handbook/
- Test Automation: https://www.hakdogan.com/test-automation/
- Digital business card: https://www.hakdogan.com/links/
- QA Practice: https://qapractice.hakdogan.com/

All functionality described above reflects what is implemented and tested as of this writing. Where something is a rehearsal or simulation rather than a live production outcome, it is labeled as such rather than presented as a deployed result.

## 9. My Role and Contributions

I designed, built, and tested this project individually. That includes:
- The site's content, structure, and front-end implementation.
- The interactive QA labs, written from scratch in TypeScript.
- The PHP backend endpoints and their safeguards.
- The CI pipeline configuration across three languages.
- The design and implementation of the custom deployment engine, its 43-case safeguard test suite, and the isolated rehearsal harness used to validate it before the first real release.
- The documentation describing the deployment process, its guarantees, and its current status.

---

*This README describes the engineering behind the project. It does not include internal infrastructure details, credentials, or private configuration.*
