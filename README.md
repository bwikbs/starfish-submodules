# Starfish test data

The bulk test data of the Starfish (LWE) test suites, kept out of the main
tree to keep that repository small. Starfish mounts this repository at
`tests/external`, and symbolic links in its `tests/` tree point here, so every
test keeps the path its lists and runners use:

| Here | Linked from Starfish | What it is |
|---|---|---|
| `internal-test/css/{position,position2,display,short-hand,zindex,zindex_img,background}`, `internal-test/click` | the same path under `tests/` | Internal pixel tests that step through style combinations, with one expected image per combination |
| `cdp/inspector-protocol` | `tests/cdp/inspector-protocol` | Chromium's inspector-protocol tests, unmodified (see `LICENSE`) |

Starfish opens a `file://` test by its real path, so a test here resolves its
relative references inside this repository. `internal-test/css/framework.js`
is therefore a link back to the helper in Starfish's `tests/internal-test/css/`,
which the pixel tests load as `../framework.js` (`../css/framework.js` from
`click/`).

Update this repository together with the Starfish change that needs it, then
commit the new submodule pointer in Starfish.
