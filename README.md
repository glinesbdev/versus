# Versus

[![Netlify Status](https://api.netlify.com/api/v1/badges/3c4627f0-0421-45c1-8c42-45b328224db9/deploy-status)](https://app.netlify.com/sites/magnificent-cendol-bd7127/deploys)

This is an open sourced, community driven, living document, which means that it will be updated as time goes on to include more examples, correct erratum, etc. provided by both the maintainer as well as members of the community, like you!

Created with [Honkit](https://github.com/honkit/honkit)

## Getting Started

To create and preview content locally, do the following:

```bash
$ git clone git@github.com:glinesbdev/versus.git
$ cd versus
$ npm install
$ npx honkit serve
```

> You can also use `npm run dev` to start the development server.

Then head to <http://localhost:4000> to view the book. Any changes you make to content will be automatically reloaded by your browser.

> When adding any new variables or partials, please update this document!

## Variables

Honkit allows you to create custom variables to use in your views. Below are the current registered variables.

| Variable | Value |
| -------- | ----- |
| partials.path | /partials |
| partials.images_path | /partials/images |
| examples.path | /examples |
| external.links.fortnite_create | https://create.fortnite.com |
| external.links.fortnite_creative_discord | https://discord.gg/fortnitecreative |
| external.links.fortnite_creative_team_docs| https://dev.epicgames.com/documentation/en-us/uefn/creating-teams-in-creator-portal-in-unreal-editor-for-fortnite |
| external.links.uefn | https://www.fortnite.com/news/unreal-editor-for-fortnite-and-creator-economy-2-0-are-here-new-worlds-await |
| external.links.uefn_collaboration | https://dev.epicgames.com/documentation/en-us/uefn/collaborating-in-unreal-editor-for-fortnite |
| external.links.uefn_docs | https://dev.epicgames.com/documentation/en-us/uefn/unreal-editor-for-fortnite-documentation |
| external.links.uefn_download | https://store.epicgames.com/en-US/p/fortnite--uefn |
| external.links.uefn_unreal.revision_control | https://dev.epicgames.com/documentation/en-us/uefn/unreal-revision-control-in-unreal-editor-for-fortnite |
| external.links.uefn_verse.common_types | https://dev.epicgames.com/documentation/en-us/uefn/common-types-in-verse |
| external.links.uefn_verse.learn | https://dev.epicgames.com/documentation/en-us/uefn/learn-programming-with-verse-in-unreal-editor-for-fortnite |
| external.links.uefn_verse.language_reference | https://dev.epicgames.com/documentation/en-us/uefn/verse-language-reference |
| external.links.uefn_verse.api_reference | https://dev.epicgames.com/documentation/en-us/uefn/verse-api |
| external.links.uefn_glossary.device | https://dev.epicgames.com/documentation/en-us/uefn/unreal-editor-for-fortnite-glossary#device |

These are used in Markdown files with the following syntax: `{{ book.partials.path }}`.

> To register new variables, update the `variables` key in the [book.json](./book.json) file.

## Partials

Partials are files that you can include into other files for re-use or to add modularity. These files are located in the [src/partials](./src/partials/) directory.

Refer to the [Honkit Documentation](https://honkit.netlify.app/templating/conrefs.html) for more information

## Issues

Find something that needs fixing? If you have the knowledge and know-how to fix it, please contribute back! For anything else, please [create an issue](https://github.com/glinesbdev/versus/issues).

## Contributing

1. Please read and familiarize yourself with our [Document for Contributors](CONTRIBUTING.md). By contributing to this project, you agree to abide by the rules of the Contributing Document.
2. Fork the repo.
3. Make changes in your local repo.
4. Push it to your forked branch.
5. Create a new [Pull Request](https://github.com/glinesbdev/versus/pulls).
