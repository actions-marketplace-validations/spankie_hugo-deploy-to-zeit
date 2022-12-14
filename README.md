# GitHub Action to build and deploy a Hugo site to zeit

This GitHub action will build your [Hugo site](https://gohugo.io/), and deploy it to [Vercel](https://vercel.com).

## Secrets

- `ZEIT_TOKEN`: A token provided on your Vercel (formerly zeit) dashboard, to allow deployment to Vercel

## Environment Variables

- `HUGO_VERSION`: This allows you to control which version of Hugo you want to use. There is a default within the action, but this may be out of date.

## Example

```shell
name: Build with hugo and deploy to zeit
on:
  push:
    branches:
      - master

jobs:
  build:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
      - name: Checkout master
        uses: actions/checkout@v1

      - name: Deploy the site
        uses: spankie/hugo-deploy-to-zeit@master
        env:
          HUGO_VERSION: 0.59.1
          ZEIT_TOKEN: ${{ secrets.ZEIT_TOKEN }}
```

This will:

- Build the repository into the `public` folder.
- Deploy the app to vercel using the now command

This action was inspired by [benmatselby's](https://github.com/benmatselby/hugo-deploy-gh-pages) action
