# Range Swapper — OnlyOffice Plugin

An OnlyOffice spreadsheet plugin that lets you select two cell ranges and swap their contents in one click.

![Plugin panel showing Range A and Range B slots with a Swap button](resources/img/icon.png)

## Features

- **Two-step range selection** — click Set, select cells in the sheet, click Confirm
- **Formulas moved as-is** — references are not adjusted
- **Ranges retained after swap** — swap back instantly without re-selecting
- **Size validation** — prevents swapping ranges with different cell counts
- **Overlap warning** — alerts you if ranges overlap, with option to continue

## Installation (OnlyOffice Desktop)

1. Download `RangeSwapper.plugin` from the [Releases](../../releases) page
2. Open OnlyOffice Desktop Editors
3. Go to **Plugins → Plugin Manager → Install from file**
4. Select `RangeSwapper.plugin`

## Usage

1. Open a spreadsheet and click the **Range Swapper** button in the Plugins tab
2. Click **Set Range A**, select cells in the sheet, click **Confirm ✓**
3. Click **Set Range B**, select cells in the sheet, click **Confirm ✓**
4. Click **Swap ↕**

## Web / Self-Hosted Installation

To use this plugin on an OnlyOffice Document Server, add the hosted `config.json` URL to your server's `local.json`:

```json
{
  "plugins": {
    "enabled": true,
    "pluginsData": [
      "https://yourusername.github.io/range-swapper-plugin/config.json"
    ]
  }
}
```

## Building the `.plugin` file

Run from the project root in PowerShell:

```powershell
Remove-Item "RangeSwapper.plugin" -ErrorAction SilentlyContinue
Compress-Archive -Path "config.json","index.html","plugins.js","resources" -DestinationPath "RangeSwapper.zip" -Force
Rename-Item "RangeSwapper.zip" "RangeSwapper.plugin"
```

## Plugin structure

```
├── config.json       # Plugin manifest
├── index.html        # UI and logic
├── plugins.js        # OnlyOffice SDK
└── resources/
    └── img/
        ├── icon.png       # 40×40 px
        └── icon@2x.png    # 80×80 px (HiDPI)
```

## License

MIT
