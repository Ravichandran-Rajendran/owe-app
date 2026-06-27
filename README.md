# Owe — GitHub Pages site

Live site: **https://ravichandran-rajendran.github.io/owe-app/**

## Pages

| File | App Store use | Live URL |
|------|---------------|----------|
| `index.html` | Support URL | https://ravichandran-rajendran.github.io/owe-app/ |
| `privacy.html` | Privacy Policy URL | https://ravichandran-rajendran.github.io/owe-app/privacy.html |
| `terms.html` | Terms / EULA | https://ravichandran-rajendran.github.io/owe-app/terms.html |

These URLs are wired in `AppSupportConfiguration.swift` and Settings → Legal.

## App Store Connect checklist

- [ ] **Privacy Policy URL:** `.../privacy.html`
- [ ] **Support URL:** `.../`
- [ ] Subscriptions: `com.ravicraj.loancalculator.pro.monthly`, `com.ravicraj.loancalculator.pro.yearly`
- [ ] Grandfathered lifetime (no longer sold): `com.ravicraj.loancalculator.pro.lifetime`
- [ ] Enable **iCloud** capability + CloudKit container `iCloud.com.ravicraj.loancalculator` in Apple Developer portal
- [ ] Enable **App Groups** `group.com.ravicraj.loancalculator` for app + widget targets
- [ ] Set `appStoreID` in `AppSupportConfiguration.swift` after App Store listing is created
- [ ] After editing legal pages, push to `main` so GitHub Pages updates the live URLs

## GitHub Pages settings

- **Source:** branch `main`, folder **`/docs`**

## Custom domain (optional)

Add in GitHub Pages settings without changing these files.
