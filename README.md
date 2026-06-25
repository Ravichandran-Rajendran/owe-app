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
- [ ] Create IAP: `com.ravicraj.loancalculator.pro.lifetime` ($2.99, Non-Consumable)
- [ ] Enable **iCloud** capability + CloudKit container `iCloud.com.ravicraj.loancalculator` in Apple Developer portal
- [ ] Enable **App Groups** `group.com.ravicraj.loancalculator` for app + widget targets
- [ ] Set `appStoreID` in `AppSupportConfiguration.swift` after App Store listing is created

## GitHub Pages settings

- **Source:** branch `main`, folder **`/docs`**

## Custom domain (optional)

Add in GitHub Pages settings without changing these files.
