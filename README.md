# Revio sticker library

This public repository hosts versioned media releases for the Revio shared sticker library. The app fetches `library-manifest.json` from the latest GitHub release, checks each file's byte count and SHA-256, then stores accepted media in app-private storage for offline use.

## Release format

Each immutable release tag matches the manifest's `version` (for example `v1.0.0`). The release contains:

- `library-manifest.json`, with schema version, sticker metadata, paths, MIME types, sizes, and SHA-256 digests.
- One file per manifest asset, with a unique filename.

Do not replace assets under an existing tag. Publish a new version instead. The app has a 4 MiB manifest limit, a 512 MiB total-library limit, and per-file media validation.

## Updating

From the Revio app source checkout, prepare a fresh output directory and run:

```sh
python3 flutter_app/tool/build_sticker_library.py \
  --version v1.0.1 \
  --output /path/to/empty/output
```

Review the generated manifest and media before publishing. After the repository and catalog are updated, publish the versioned release with the app's reviewed release process.

GIPHY and Tenor API results are not mirrored here. The app continues to load those provider results directly.

## Media rights

Public availability here does not grant a license to reuse the media. Publish only media you own or have explicit rights to redistribute. The rights for each curated item in the initial pilot payload have not been independently audited; confirm those rights before treating this as a production library. No repository-wide media license is provided.
