# Workflow

## Updating to new release

1. Check upstream Mailman release tag revision on https://bazaar.launchpad.net/~mailman-coders/mailman/2.1/changes
2. Go to files browsing page at tagged revision using icon in files column on the right.
3. Download and update `messages/mailman.pot` file to tagged release version from website (download icon on the right) with commit message like `Update messages/mailman.pot to upstream rev …`.
4. In `templates/en/` folder check "Latest Rev" column if there was an update since the last release. If so, update changed files with commit message like `Update templates/en to upstream rev …`.
5. In Poedit update `messages/pl/LC_MESSAGES/mailman.po` using `messages/mailman.pot`, save it (creating `messages/pl/LC_MESSAGES/mailman.mo`) and commit with message like `Update messages/pl to equivalent of upstream rev …`.
6. After updating `mailman.po` remember to rebuild `mailman.mo`.
7. Update README.md with information about release, commit with message like `Update readme (…)`.
8. Tag revision, `git tag …`.
9. Send changes to Github, `git push && git push origin --tags`.

## Mozilla specific changes

1. Create Mozilla specific branch like `git branch mozilla-2.1.… && git checkout mozilla-2.1.…`.
2. Import Mozilla specific changes, `curl --location https://github.com/aviarypl/mailman-l10n-pl/commit/bc6b995e0dca8333ed239038be6aaffa158b2d54.patch | git am && curl --location https://github.com/aviarypl/mailman-l10n-pl/commit/5e04a32a7c349158c3a1adff095dbc675d340eff.patch | git am`.
3. Tag revision, `git tag 2.1.…-mozilla`.
4. Send changes to Github and chackout back master, `git push --set-upstream origin mozilla-2.1.… && git push origin --tags && git checkout master`.
