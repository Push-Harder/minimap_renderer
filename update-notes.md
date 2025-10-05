Typical Update Procedure:

1.  Delete old `res_extract`, and run the extraction script.

    python extract.py
    

2.  Move resources.
    1.  `texts/en/LC_MESSAGES/global.mo` to `resources/`.
    2.  `content/GameParams.data` to `resources/`.
    3.  Delete old `maps/spaces` and `spaces/` to `maps/`.
    4.  Create new directory with version name in `src/replay_unpack/clients/wows/versions/`. Move `scripts/` into this directory. Copy and paste the rest of the (Python) files in the previous version.
    5.  Various resources are copied from `gui/` to `src/renderer/resources/`. Unfortunately, the extract script doesn't get everything the renderer needs, but it does get the most common ones. The renderer also expects some assets (such as buildings) in a different format, should really be fixed.
3.  Run scripts.
    1.  `create_data.py` writes to JSON files.
    2.  `maps/spaces.py` adds empty `__init__` files that are necessary.
4.  Move more files
    1.  Create new directory with version name in `src/renderer/versions/`. Copy contents of last version, but replace contents of `/<version>/resources/` with `generated/*`.
    2.  Replace `src/renderer/resources/spaces` with `maps/spaces`.
5.  Update tests.
    1.  Add test replay(s) to `replays`.
    2.  Add path to `tests/test_all.py`.
    3.  Run it through `render.py` and visually confirm it looks reasonable.

A collection of useful constants (containing most used by this library) is available at [https://github.com/padtrack/wows-constants/blob/main/data/latest.json](https://github.com/padtrack/wows-constants/blob/main/data/latest.json).