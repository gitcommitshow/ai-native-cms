# ai-native-cms

Imagine the easiest way to publish and manage content on the go, with automated guardrails and quick human review


## Spec

The project must cover common needs for any business at a ridiculously fast pace and quality controls

1. Can publish a new static page in a min (from idea to live on production)
2. Change content from any where - browser, IDE, mobile/tablet
3. Can track changes via git
4. Can provide the content as a simple markdown or as a complex html
5. Can go from Idea/Issue to PR to the preview ready for human review (edit/approve) autonomously using AI
6. Can go from prompt to live staging preview within 30 secs
7. Can show dynamic data from API or DB or a file in repo (json, xml, yaml)
8. Can collect user inputs (forms) without additional setup
9. Quick access to the agentic editor e.g. add aicms.github.com/org/repo to open the editor with live preview + new branch + ai chat
10. Automated checks to maintain standard and identify issues early

## Design

WIP - need to think of alternative implementation ideas

### Plan A : GitHub repo template

A Node.js app with claude, netlify, codesandbox, lighthouse github action/app.
Some context files for claude.
Some code to route UI form submissions to a database (or to a file in the same repo).

How it works

1. User creates a GitHub issue
2. Claude raises a PR and requests review from the editor
3. Netlify gh action creates a preview link
4. Codesandbox creates the editing link
5. Reviewer opens the codesandbox link
6. Reviewer edits
7. Pushes the changes
8. Claude reviews
9. Editor review
10. Reviewer approves and merges
11. Netlify deploys to production and comments the link
12. Action that watches the latest changes for issues (broken link, lighthouse score)

Pros
- Familiar process

Cons
- No-go for mobile
- Claude fails sometimes
- Netlify charges
- Will take more than a min
