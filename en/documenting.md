---
title: "Contributing documentation"
description: "Where is the documentation and how to contribute."
category: organization
lang: en
ref: documenting
order: 100
version: 1
---

There are currently 4 sources of documentation for Symbol. Feel free to jump to the one you are interested in.

- [Technical documentation](#technical-documentation): Tool guides, developer tutorials and SDK reference guides.
- [Symbol handbook](#symbol-handbook): The syndicate's Handbook explaining its vision and organization.
- [Working documentation](#working-documentation): Meeting minutes, Community logs, stuff that changes often.
- [NIS1 documentation](#nis1-documentation): Old NIS1 guides, pending assimilation into the Symbol technical docs.

## Technical documentation

**Site** | [docs.symbolplatform.com](https://docs.symbolplatform.com)
**Source repo** | [github.com/symbol/symbol-docs](https://github.com/symbol/symbol-docs)
**Host** | [GitHub pages](https://github.com/symbol/symbol.github.io)
**Engine** | [Sphinx](https://www.sphinx-doc.org)
**Format** | [reStructuredText](https://docutils.sourceforge.io/rst.html)
**Intended readers** | The world at large.
**Intended writers** | The Symbol technical writers.
**Editing workflow** | Git-based: Check out the source repository, make modifications and submit pull requests.
**Localization** | [Transifex](https://www.transifex.com/nemtech/symboldocs/)
**Maintainers** | [Xavi](https://github.com/segfaultxavi)
{: .info_table }

### Content

This is the main technical reference. It contains (or will contain):

- **User guides** for the different tools (Wallet, CLI, Explorer, etc.), intended for non-heavily-technical readers, including screenshots and step-by-step instructions on how to solve common problems.
- **Developer tutorials** with source code examples in different languages, organized by topics. Ranging from Getting Started to in-depth guides on specific topics.
- **Concept definitions** required to understand the Symbol protocol.
- **Technical reference** guides describing every API and REST endpoint.

Due to the complexity of the technical content, the [Sphinx](https://www.sphinx-doc.org) engine and [reStructuredText](https://docutils.sourceforge.io/rst.html) is used instead of the simpler MarkDown format. This enables much more flexibility, so we can use multi-language (tabbed) code snippets, Python macros which automatically retrieve content from GitHub or have more formatting options for complex tables, for example.

### Editing

This repository follows the doc-as-code approach, meaning that you treat the documentation as if it was source code.

To contribute you need to check out the Git repository, make your changes and submit a [Pull Request](https://docs.github.com/en/github/collaborating-with-pull-requests) to GitHub. The repository maintainers will review your contribution, suggest changes if required and eventually merge it.

### Testing

Before submitting a pull request it is a good idea to test your changes locally, to ensure that everything shows as expected and nothing breaks.

You first need to [Install Sphinx](https://www.sphinx-doc.org/en/master/usage/installation.html).

After that you can trigger a build by running from the repository's root:

```bash
make livehtml
```

This will monitor your source folder and regenerate the output when changes are detected. It also instantiates a web server on `localhost:8000` for your convenience.

> **NOTE:**
> On Windows you have a handy `make-win.bat` that does the same thing but takes care of some Windows shenanigans.

### Deployment

The GitHub repository is linked to [Travis](https://travis-ci.com/github/symbol/symbol-docs), so on every push to the `main` branch a full build is triggered (See `.travis.yml` and the `travis` folder for details). This involves several steps besides the generation of the output documentation:

- **Source snippets validation**: The guides include lots of source code examples which are actually snippets from complete programs. These programs must **compile** and pass **lint checks** at all times and Travis makes sure of this. Right now only the TypeScript programs are checked.
- **Link checking**: All pages are examined to find broken links using `make linkcheck`. Throttling is enabled to avoid pestering servers too much and getting `HTTP 429 Too Many Requests` errors. Still, sometimes your build fails because of this. If you detect such error in the Travis logs just try again.
- **Localization**: Text strings are extracted from every page using `make gettext` and uploaded to Transifex (see next section).
- **Publishing**: The built HTML pages are pushed to a different git repository ([symbol/symbol.github.io](https://www.github.com/symbol/symbol.github.io)) where they are served via GitHub pages.

Due to this process, pushes to `main` normally take up to 5 minutes to go live.

### Localization

Right now almost every page is available in Japanese besides the original English, but the repository is ready to accept more languages.

[Transifex](https://www.transifex.com/nemtech/symboldocs/) is integrated in the deployment process, so after every push to `main` any changed strings are uploaded to Transifex where translators can provide text in their own language. So far this process has been done by the Symbol community.

When new translations are available the repo maintainer can download them from Transifex as `.po` files and commit them, or translators can provide the `.po` files directly via a Pull Request.

## Symbol handbook

**Site** | [docs.symbolplatform.com/handbook](https://docs.symbolplatform.com/handbook)
**Source repo** | [github.com/symbol/handbook](https://github.com/symbol/handbook/tree/gh-pages)
**Host** | [GitHub pages](https://github.com/symbol/handbook/tree/gh-pages)
**Engine** | [Jekyll](https://jekyllrb.com/)
**Format** | [Kramdown](https://kramdown.gettalong.org/) (A flavor of Markdown)
**Intended readers** | Syndicate members and contributors.
**Intended writers** | Syndicate members and contributors.
**Editing workflow** | Edit pages directly on GitHub or HackMD and submit a pull request.
**Localization** | Manual. There is a folder for each language and anybody can provide translations.
**Maintainers** | [Xavi](https://github.com/segfaultxavi)
{: .info_table }

### Content

These are documents related to the Symbol Syndicate rather than the Symbol Protocol. The main categories are:

- **Philosophy**: The vision behind Symbol.
- **Education**: Documentation aimed at bringing new syndicate members up to speed.
- **Organization**: How things are done in the syndicate. Coding guidelines, commit message format, how to contribute (this page, for instance).

### Editing

These documents are reviewed by the syndicate's technical writers before publishing, but they can be provided by anybody. That is why they use the simpler Markdown format which has a learning curve of about 10 minutes.

There are three ways to provide content for this repository, from simpler to more complex:

- **Directly on HackMD**: Pages marked with the ![hackmd-github-sync-badge](https://hackmd.io/afJzrT-RTAamp4uQTTLhHw/badge){: .inline_image } badge are linked to [HackMD](https://hackmd.io/team/syndicate) so you can edit them there, using a comfortable editor with Markdown preview, and push to GitHub when done.

  The preview you get on HackMD won't match the final result because it lacks style information.

  These pages must be tagged `Handbook` so they are properly categorized in the HackMD directory. Add this at the end of the document:

  ```markdown
  ###### tags: `Handbook`
  ```

- **Directly on GitHub**: Changes can be done directly on GitHub using its editor. It's not as comfortable as HackMD but it has preview too (without style information).

  You can conveniently access this editor using the **Edit ✎** button at the top of every page in the Handbook.

  At the bottom of the editor you have a button to submit your changes for review as a Pull Request.

- **Local checkout**: This method gives you the greatest flexibility but it is the most complex.

  Check out the Git repository, make your changes and submit a [Pull Request](https://docs.github.com/en/github/collaborating-with-pull-requests) to GitHub. The repository maintainers will review your contribution, suggest changes if required and eventually merge it.

  You can preview your changes completely, with style information and automatic tooltip injection if you [install Jekyll](https://jekyllrb.com/docs/installation/) and run this from the repository's root:

  ```bash
  bundle exec jekyll serve
  ```

  This will monitor your source folder and regenerate the output when changes are detected. It also instantiates a web server on `localhost:4000` for your convenience.

### Testing

When deployed (locally or on GitHub Pages), there is a Liquid script (Jekyll's templating language) that parses all pages and automatically injects Glossary tooltipsfor certain words (like XYM or NEM). However, the script is a bit crude and sometimes it messes up the format. If you suspect this is happening, add `notooltips: true` to the frontmatter (between the `---` lines at the top of the document). If this fixes your problem, [open a GitHub issue](https://github.com/symbol/handbook/issues/new) and report!

### Deployment

All commits to the `gh-pages` branch of the repository are automatically built and published by GitHub Pages. It normally takes less than a minute for the changes to go live.

If you want to preview changes, you can push to the `new-structure` branch which is monitored by [Netlify](https://app.netlify.com/teams/symbol-bot/overview). This integration is still a Work in Progress.

### Localization

There is no automated handling of translations in the Handbook. Instead, each language is kept in a separate folder and anybody can provide translations.

There are a few structures in place to simplify translation, though:

- There is a language selector at the top of the Handbook. It switches between all the available languages **of the current document**.

- All documents have a `version` field in the frontmatter (between the `---` lines at the top of the document). When the English original is changed the version number should be increased. In this way, it is easy to see if a translation is outdated.

- The main [Table of Contents](https://docs.symbolplatform.com/handbook) of the handbook has special tags related to translations:

  - **Missing translation**: Shown when a document does not exist in the currently selected language. Click on the tag to create a new file and provide the missing document.
  - **Outdated translation**: The original English document has changed and this translation needs reviewing. Click on the tag to edit the document and update the translation.

## Working documentation

**Site** | [hackmd.io/team/syndicate](https://hackmd.io/team/syndicate)
**Source repo** | [hackmd.io/team/syndicate](https://hackmd.io/team/syndicate)
**Host** | [hackmd.io/team/syndicate](https://hackmd.io/team/syndicate)
**Engine** | HackMD
**Format** | [Markdown](https://www.markdownguide.org/)
**Intended readers** | Syndicate members.
**Intended writers** | Syndicate members.
**Editing workflow** | Edit pages directly on HackMD.
**Localization** | None
**Maintainers** | Every syndicate member.
{: .info_table }

This is meant as a scratch pad for collaborative editing, or as a means of storage for documents that change too often or are too big or numerous to be in the Handbook.

Examples are:

- Documents being worked on (they are live, or waiting approval to go into the Handbook)
- Meeting minutes (there are too many of them)
- Test results (they change continuously)

To keep this area organized all documents should be **tagged**. Please add this line at the bottom of your document:

```markdown
###### tags: `tag1` `tag2`
```

Use any tag you want, but please look at the other documents and try to be consistent.

## NIS1 documentation

**Site** | [docs.nem.io/en](https://docs.nem.io/en) <br> [nemproject.github.io](https://nemproject.github.io/)
**Source repo** | ?
**Host** | ?
**Engine** | ?
**Format** | ?
**Intended readers** | The world at large.
**Intended writers** | The Symbol technical writers.
**Editing workflow** | ?
**Localization** | ?
**Maintainers** | ?
{: .info_table }

This section is still being figured out. Stay tuned.
