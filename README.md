# planship-docs

Welcome to the official [Planship documentation](https://docs.planship.io) project.

Our docs are built using [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/).

## Local development

To run locally, use

```sh
mkdocs serve
```

## Styling

Extra styling can be defined in `docs/stylesheets/extra.css`.

You can also use [Tailwind](https://tailwindcss.com) by defining styles in `docs/stylesheets/tailwind.css`. After adding your own styles you must generate a new Tailwind `output.css` with the following command:

```sh
npx tailwindcss build -i docs/stylesheets/tailwind.css -o docs/stylesheets/output.css
```
