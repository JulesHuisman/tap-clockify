# tap-clockify

**Author**: Stephen Bailey (sbailey@immuta.com)

This is a [Singer](http://singer.io) tap that produces JSON-formatted data following the [Singer spec](https://github.com/singer-io/getting-started/blob/master/SPEC.md).

It can generate a catalog of available data in Clockify and extract the following resources:

- projects
- tags
- tasks
- time entries
- users
- workspaces

### Quick Start

1. Install

```bash
git clone git@github.com:immuta/tap-clockify.git
cd tap-clockify
pip install .
```

2. Get an [API key](https://clockify.me/developers-api) from Clockify

3. Create the config file.

There is a template you can use at `config.json.example`, just copy it to `config.json` in the repo root and insert your token

4. Run the application to generate a catalog.

```bash
tap-clockify -c config.json --discover > catalog.json
```

5. Select the tables you'd like to replicate

Step 4 generates a a file called `catalog.json` that specifies all the available endpoints and fields. You'll need to open the file and select the ones you'd like to replicate. See the [Singer guide on Catalog Format](https://github.com/singer-io/getting-started/blob/c3de2a10e10164689ddd6f24fee7289184682c1f/BEST_PRACTICES.md#catalog-format) for more information on how tables are selected.

6. Run it!

```bash
tap-clockify -c config.json --catalog catalog.json
```

### Acknowledgements

Would like to acknowledge the folks at Fishtown Analytics whose [`tap-framework`](https://github.com/fishtown-analytics/tap-framework) and [`tap-lever`](https://github.com/fishtown-analytics/tap-lever) packages formed the foundation for this package.

Copyright &copy; 2019 Immuta
