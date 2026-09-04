# Migration checklist

Because this replaces the experimental repository structure, preserve the current known-good commit first.

Recommended:

1. Create a Git tag or backup branch from the current working state.
2. Delete the old tracked experimental files from the repository working tree.
3. Copy the contents of this package into the repository root.
4. Commit the cleanup as one dedicated commit.
5. Push to `master`.
6. Run `Build Keychron B1 Pro`.
7. Confirm the build passes the hardware verification step and uploads `keychron-b1-pro-firmware`.
8. Flash only if you want to verify the cleaned repository end-to-end.

The old matrix-probe workflows, probe keymaps, build.yaml, and Kyria-specific files are intentionally not included in this clean B1 Pro repository package.
