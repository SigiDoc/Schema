# Release Guidelines

## Release a new schema version

1. Make changes to `sigidoc.odd` on the `main`branch.
2. Create and push a tag named `vX.Y`, e.g. `v1.2`.
3. The release action will run and create a draft release.
4. Go to _Releases_, find the new draft release, fill in the release information with a description of the changes made and publish.

## GitHub Action workflows

### Build SigiDoc Schema release

This action is triggered when a tag with the name pattern `vX.Y` is created on the main branch. It will:

- Compile the ODD to an RNG
- Publish the release on GitHub Pages
  - Copy the ODD and RNG to a new release directory on the `gh-pages` branch under `schema/X.Y`
  - Copy the ODD and RNG to the `schema/latest` directory on `gh-pages`, overwriting the older versions
  - Create directory indices on `gh-pages`
- Update the `latest` branch with the current `main` branch
- Create a release draft on GitHub

### Build EpiDoc Development Schema

This action is triggered each time the ODD is modified on the main branch. It compiles and publishes the current development version of the schema to GitHub Pages under `schema/dev`.

### Update SigiDoc landing page from README

This action is triggered each time the `README.md` file is modified on the main branch. It uses `pandoc` to convert it to HTML and publishes it to GitHub Pages.
