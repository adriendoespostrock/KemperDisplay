# Publishing checklist

Kemper Display is distributed as a compiled macOS application. The source code is not published in this repository.

- [ ] Set the app version and build number
- [ ] Build the app in Release configuration
- [ ] Test the Release build on another Mac
- [ ] Sign the app with a Developer ID certificate
- [ ] Enable Hardened Runtime
- [ ] Notarize the public build with Apple
- [ ] Verify the notarized app launches correctly on a clean Mac
- [ ] Package the app as a `.zip` or `.dmg`
- [ ] Add screenshots to `Screenshots/`
- [ ] Create a GitHub Release
- [ ] Attach the signed/notarized `.zip` or `.dmg` to the Release
- [ ] Add release notes describing fixes, changes, and compatibility information
