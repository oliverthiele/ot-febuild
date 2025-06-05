# ot_febuild – Webpack Build Target Extension for TYPO3

This TYPO3 extension provides a clean, Composer-friendly target for frontend
build artifacts (e.g. from Webpack). It helps keep your sitepackage free from
compiled output and allows better IDE synchronization and
version control separation.

The build process should output all assets (CSS, JS, fonts, icons, etc.)
into the folder:

`EXT:ot_febuild/Resources/Public/Assets/`

TYPO3 automatically handles cache busting via `versionNumberInFilename`
and – in TYPO3 v12 and v13 – symlinks the public directory under:

`public/_assets/`

---

## ✅ Benefits

- Keeps generated files out of your sitepackage and Git history
- TYPO3 can resolve paths via `EXT:ot_febuild/...` for JS/CSS includes
- Compatible with `versionNumberInFilename` and TYPO3 v12+ public asset handling
- Ideal for use in Composer-based installations

---

## 📦 Installation

```bash
composer require oliverthiele/ot-febuild
```

## 🔧 Integration via TypoScript

Example configuration:

```typo3_typoscript
page {
    includeCSS.styles = EXT:ot_febuild/Resources/Public/Assets/Css/Main.css
    includeJs.script = EXT:ot_febuild/Resources/Public/Assets/JavaScript/Main.js
}
```

Additional assets (e.g. icons, fonts) are also available under:

`EXT:ot_febuild/Resources/Public/Assets/`


If you're using the corresponding frontend build configuration, Font Awesome SVG icons are available in:

`EXT:ot_febuild/Resources/Public/Assets/SVG/`

---

## 🔁 Deployment Example (DDEV → Live Server)

```shell
rsync -avzP -e 'ssh -p 22' --progress --dry-run \
    /var/www/html/vendor/oliverthiele/ot-febuild/Resources/Public/Assets/ \
    user@dev.example.com:/usr/home/user/public_html/typo3-dev/packages/ot_febuild/Resources/Public/Assets
```
You can automate this as part of your deployment or build pipeline.

---

## 📝 License

This project is licensed under the GNU General Public License v2.0 or later
(GPL-2.0-or-later).

---
