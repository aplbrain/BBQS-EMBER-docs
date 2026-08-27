# BBQS EMBER Documentation Web Application

This repo contains user documentation for the EMBER Archive.

The documentation site is built with [Markdown](https://www.markdownguide.org/) and [MkDocs](https://www.mkdocs.org/). Documentation is written as a collection of markdown files, and MkDocs is used to render the documentation as a website.

## Requirements

- [uv](https://docs.astral.sh/uv/). Installation instructions can be found [here](https://docs.astral.sh/uv/getting-started/installation/)

## Development

### Edit Content

- Open the `.md` you'd like to edit
- Makes changes & save
- Add the filename to [mkdocs.yml](/mkdocs.yml) under the `nav:` section to define how the file should appear in the table of contents 

### Preview Changes

Run the following command:
```bash
uv run mkdocs serve --livereload
```
Then, open your browser to http://localhost:8080.

## Contributing

Contributions are welcome through pull requests. Please notify the BBQS EMBER team for review.
