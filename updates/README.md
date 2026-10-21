# Shift software update information

These files let Shift check which development build is current. They are public release metadata, not an app download or a distribution service. They contain no user, Pod, glucose or insulin data.

Current development build: **0.1.0 (5)**. Installation is through the developer's Xcode build. There is no public TestFlight or App Store release yet.

- `ios.json` is for `app.shift.ios`.
- `sim.json` is for `app.shift.sim`.
- The matching watch app and widget extension use the same version/build and are bundled with their iPhone app.

## Publishing an update

1. Build and validate the phone app and its embedded watch/widget targets.
2. Keep bundle identities unchanged; increment the build number for every distributed build. Use a three-part numeric marketing version.
3. Make the update and installation instructions available before announcing it.
4. Update the matching JSON file: version, build, notes and releaseURL. Links must stay under `https://github.com/matdoslb/Shift/`.
5. `criticalBuilds` is an explicit list of affected build numbers. Leave it empty unless a confirmed issue warrants an urgent notice. Never repurpose an old build number.

Shift checks on foreground, caches successful checks for 24 hours, and offers a manual check in Settings → Shift. Ordinary notices are limited to once a week per release; urgent notices to once a day. Notices are deferred when setup, delivery operations or modal flows are active. Offline failures retain a previously known notice and do not claim the app is up to date.

This metadata never installs software, modifies treatment settings, or disables Pod controls. Do not publish test urgent notices to the production files.
