# Themekit for GitHub Actions

This GitHub action is part of a list of my Actions : https://github.com/bjt-smilelove/actions.

## Usage

To use the action simply add the following lines to your workflow .yml file.

```yaml
...
  steps:
      - uses: actions/checkout@v1
      - name: Shopify
        uses: bjt-smilelove/action-shopify@master
        env:
          SHOPIFY_PASSWORD: ${{ secrets.SHOPIFY_PASSWORD }}
          SHOPIFY_STORE_URL: ${{ secrets.SHOPIFY_STORE_URL }}
          SHOPIFY_THEME_ID: ${{ secrets.SHOPIFY_THEME_ID }}
          THEME_PATH: ${{ secrets.THEME_PATH }}
          ACTION: deploy
```
* **ACTION**: `deploy` or `download` (defaults to `download`).

You can see a repository with this action here : https://github.com/pgrimaud/shopify-debut

### Required Secrets

First, generate a private app API KEY on Shopify. [Shopify API Access](https://shopify.github.io/themekit/#get-api-access).

Second, setup the following secrets in [GitHub secrets](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/creating-and-using-encrypted-secrets#creating-encrypted-secrets).

* **SHOPIFY_PASSWORD**: Your password from your private app previously created.
* **SHOPIFY_STORE_URL**: Your store url. (e.g. `demo.myshopify.com`).
* **SHOPIFY_THEME_ID**: Your theme id on your Shopify Store.
* **THEME_PATH**: Path of your theme on your GitHub repository. If your theme is at the root of your repository, just use `./`.

### Optional Arguments

You can add optional arguments to improve theme deployment. Optional argument descriptions are available on [Theme Kit help](https://shopify.github.io/themekit/configuration/#flags).

#### Examples

```yaml
...
  steps:
      - uses: actions/checkout@v1
      - name: Shopify
        uses: bjt-smilelove/action-shopify@master
        env:
          SHOPIFY_PASSWORD: ${{ secrets.SHOPIFY_PASSWORD }}
          SHOPIFY_STORE_URL: ${{ secrets.SHOPIFY_STORE_URL }}
          SHOPIFY_THEME_ID: ${{ secrets.SHOPIFY_THEME_ID }}
          THEME_PATH: ${{ secrets.THEME_PATH }}
        with:
          args: --ignored-file=sections/*
```

Your can also combine multiple arguments : 

```yaml
...
  steps:
      - uses: actions/checkout@v1
      - name: Shopify
        uses: bjt-smilelove/action-shopify@master
        env:
          SHOPIFY_PASSWORD: ${{ secrets.SHOPIFY_PASSWORD }}
          SHOPIFY_STORE_URL: ${{ secrets.SHOPIFY_STORE_URL }}
          SHOPIFY_THEME_ID: ${{ secrets.SHOPIFY_THEME_ID }}
          THEME_PATH: ${{ secrets.THEME_PATH }}
        with:
          args: --ignored-file=sections/* --timeout=30
```

## License

The Dockerfile and associated scripts and documentation in this project are released under the [MIT License](LICENSE).
