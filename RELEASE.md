# Release Checklist

## Tag and publish

```bash
# Make sure your main branch is up to date and all tests pass
git checkout main
git pull origin
bun install
bun run all

# Update CHANGELOG.md - for major releases only

# These scripts prepare the files in the dist folder
bun run wikidata    # slow, about 10 minutes
bun run dist        # fast, version number updates automatically and will print to console

export VERSION=vA.B.C
git add . && git commit -m "$VERSION"
git tag "$VERSION"
git push origin main "$VERSION"
npm login    # if needed, session tokens last 2 hours
bun publish
```

<!-- sync:
version=1
source=https://github.com/rapideditor/agent-practices/blob/main/templates/RELEASE.md
Local override: NSI uses a custom manual release flow (wikidata fetch, dist build,
     `bun publish` to npm). The canonical template's `/release` workflow does not apply here.
-->
