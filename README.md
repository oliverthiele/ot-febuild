# Extension ot_febuild

This extension provides a single target for my webpack frontend build. 
This keeps your own site package free from compiled data and makes it easier to fully synchronize with the IDE.

The build instructions also copy all other necessary files in the Resources/Public/Assets folder.

By using this extension, TYPO3 can automatically include version numbers (timestamps) in the file names (versionNumberInFilename).
For example, TYPO3 v12/v13 also automatically creates a symlink under public/_assets/ for the public folder.

## Integration in TypoScript

**Example of including the CSS and JS via the TypoScript code:**

```typo3_typoscript
page {
    includeCSS.styles = EXT:ot_febuild/Resources/Public/Assets/Css/Main.css
    includeJs.script = EXT:ot_febuild/Resources/Public/Assets/JavaScript/Main.js
}
```

All other resources that the build process has processed are then located, for example, in the path:

`packages/ot_febuild/Resources/Public/Assets/...`

This also includes Fontawesome icons, which can be found in the SVG subfolder (If my frontend build configuration is used)

## Example update from DDEV to dev.example.com website

1. via Deployment
2. via rsync (without --dry-run)

```shell
rsync -avzP -e 'ssh -p 22' --progress --dry-run \
    /var/www/html/vendor/oliverthiele/ot-febuild/Resources/Public/Assets/ \
    user@dev.example.com:/usr/home/user/public_html/typo3-dev/packages/ot_febuild/Resources/Public/Assets
```
