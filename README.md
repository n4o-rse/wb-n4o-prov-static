# wb-n4o-prov-static

Static, read-only copy of the Wikibase n4o-prov.wikibase.cloud, archived with wikibase-static. The pages are made with [wikibase-static](https://github.com/n4o-rse/wikibase-static) (0.30.0 or later) from a harvest of
[n4o-prov.wikibase.cloud](https://n4o-prov.wikibase.cloud). They look like those of a Wikibase, but nothing here can be edited; the data are those that the source delivered at the
date of the last harvest (`data/raw/manifest.json`).

The identifiers (`Q…`, `P…`) are those of the source. The URIs of the RDF export are not: they are under `n4o-rse.github.io/wb-n4o-prov-static`
and use the prefix `n4op:`, so nothing here points to the source as an identifier.

## Build

Needs Python 3.10 or later. In a Windows `cmd` window, in this folder:

    pip install -r requirements.txt && python main.py --strict

To read the source Wikibase again (network; it writes `data/raw/`, and only what changed):

    python main.py harvest --probe && python main.py harvest && python main.py --strict

1. `harvest --probe` makes one request and says whether the host answers as an API or with a bot challenge (Anubis). It writes nothing.
2. `harvest` compares the revision numbers with `data/raw/manifest.json` and fetches only what is new or changed.
3. The default run builds the pages, the search index, the RDF export and the SPARQL page.

`harvest.cmd` does harvest, build, commit and push in one go; `update.cmd` installs the pinned `wikibase-static` again and does the same without
the harvest. If the host answers with a bot challenge, the harvest stops (it never tries to get around it): save the entity JSON in a browser and
run `python main.py harvest --from-dir <folder>`.

## Related repositories

- [`n4o-rse/wikibase-static`](https://github.com/n4o-rse/wikibase-static): the package that turns a Wikibase into static pages, RDF and a SPARQL page.
- [`n4o-rse/fuzzy-sl-static`](https://github.com/n4o-rse/fuzzy-sl-static): a sibling site.
- [`n4o-rse/wb-squirrelbase-static`](https://github.com/n4o-rse/wb-squirrelbase-static): a sibling site.

## Licence and attribution

The code of this repository is under the [MIT licence](LICENSE). The data are those of [n4o-prov.wikibase.cloud](https://n4o-prov.wikibase.cloud); unless this repository says
otherwise they are offered as [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/). The logo: <!-- name author and licence here -->.
