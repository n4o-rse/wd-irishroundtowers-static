# wd-irishroundtowers-static

A static, read-only Wikibase of the Irish round towers, early medieval monastic bell towers in Ireland (and a few in Scotland), as recorded in the Wikidata WikiProject IrishRoundTowers. The items are taken from [Wikidata](https://www.wikidata.org/): every instance of Irish round tower (Q1335799) or of a subclass, as in the WikiProject IrishRoundTowers.
The site is built with [wikibase-static](https://github.com/n4o-rse/wikibase-static) (0.28.1 or later) and has no model of its own: its
properties are made from the Wikidata properties that the items use.

Every item, class and property of the site has an id of its own (`Q100` and up, `P100` and up), and its Wikidata id is kept as a twin (`P4`,
"Wikidata equivalent"). The RDF export uses the prefix `irt:` and an address under `n4o-rse.github.io`, not those of Wikidata.

## Build

Needs Python 3.10 or later. In a Windows `cmd` window, in this folder:

    pip install -r requirements.txt && python main.py --strict

To read the items from Wikidata (network; these two steps write `data/`):

    python main.py seeds-from-sparql && python main.py import-wikidata && python main.py --strict

1. `seeds-from-sparql` runs the queries of `data/seeds/wikidata-*.rq` at the Wikidata Query Service, adds the ids of `data/seeds/wikidata-qids.txt` and writes `data/csv/seeds-wikidata.csv`.
2. `import-wikidata` reads those items (and the properties they use) from Wikidata and writes the tables of `data/csv/`; `dist/wikidata-import.txt` and `dist/wikidata-gaps.csv` report what could not be taken over. It runs with `--generic --provenance item`.
3. The default run builds the pages, the search index, the RDF export and the SPARQL page.

`update.cmd` installs the pinned `wikibase-static` again, builds with `--strict`, and commits and pushes only if something changed.

## Related repositories

- [`n4o-rse/wikibase-static`](https://github.com/n4o-rse/wikibase-static): the package that turns the CSV tables into the static Wikibase pages, RDF and SPARQL page.
- [`n4o-rse/wd-ogham-static`](https://github.com/n4o-rse/wd-ogham-static): a sibling site.
- [`n4o-rse/wd-holywells-static`](https://github.com/n4o-rse/wd-holywells-static): a sibling site.
- [`n4o-rse/wd-govanstones-static`](https://github.com/n4o-rse/wd-govanstones-static): a sibling site.

## Licence and attribution

The code of this repository is under the [MIT licence](LICENSE). The data come from [Wikidata](https://www.wikidata.org/) and are available under
[CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/). The images are not copied: they stay at Wikimedia Commons, each under its own licence,
and are only linked.
