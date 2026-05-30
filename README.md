# Hex Editor with Colors

Fork of Microsoft [Hex Editor](https://marketplace.visualstudio.com/items?itemName=ms-vscode.hexeditor) VS Code extension, with colors.

## Changes

- Reduce decoded text cell width (fixes [#566](https://github.com/microsoft/vscode-hexeditor/issues/566), [PR](https://github.com/microsoft/vscode-hexeditor/pull/601))
- Add "Open in Hex Editor" command
- Remove telemetry
- Add rendering styles: colors for both bytes and decoded text, and glyphs for decoded text

## New settings

### Color scheme

- [`hexeditor.style.byteColorScheme`](vscode://settings/hexeditor.style.byteColorScheme): Color style for bytes
- [`hexeditor.style.decodedTextColorScheme`](vscode://settings/hexeditor.style.decodedTextColorScheme): Color style for decoded text

Values:

- `default`: Default monochrome (mimics original extension)
- `rainbow` and `rainbowLight`: Color choosen by high nibble
- `categories` and `categoriesLight`: Color choosen by category (non-printable ASCII, printable ASCII, non-ASCII)
- `gradient`: Color gradients

### Character tables

- [`hexeditor.style.nonPrintableAsciiCharacter`](vscode://settings/hexeditor.style.nonPrintableAsciiCharacter): Rendering style for non-printable ASCII within the decoded text
- [`hexeditor.style.printableAsciiCharacter`](vscode://settings/hexeditor.style.printableAsciiCharacter): Rendering style for printable ASCII within the decoded text
- [`hexeditor.style.nonAsciiCharacter`](vscode://settings/hexeditor.style.nonAsciiCharacter): Rendering style for non-ASCII within the decoded text

Values:

- `dot`: Renders a regular dot
- `middot`: Renders a middle dot (lighter than a regular dot)
- `bullet`: Renders a bullet
- `cross`: Renders a cross (a multiplication sign)
- `symbol`: Renders a glyph that represents the control code
- `ascii`: Renders the actual ASCII character
- `braille`: Renders a braille glyph based on the byte value

Table:

| Category            | `dot`  | `middot`  | `bullet`  | `cross`  | `symbol` | `ascii` | `braille` |
|---------------------|--------|-----------|-----------|----------|----------|---------|-----------|
| `nonPrintableAscii` | `dot`* | `middot`* | `bullet`* | `cross`* | `symbol` |         | `braille` |
| `printableAscii`    |        |           |           |          |          | `ascii` | `braille` |
| `nonAscii`          | `dot`  | `middot`  | `bullet`  | `cross`  |          |         | `braille` |

&ast; Particularly relevant characters (NUL 0x00, TAB 0x09, LF 0x0A, CR 0x0D, whitepace 0x20, and DEL 0x7F) will use their own glyphs

## Credits

- Original [Hex Editor](https://marketplace.visualstudio.com/items?itemName=ms-vscode.hexeditor) VS Code extension Copyright &copy; Microsoft Corporation
- Rainbow palettes inspired by [_"your hex editor should color-code bytes"_](https://simonomi.dev/blog/color-code-your-bytes/) blogpost by [simonomi](https://github.com/simonomi)
- Color gradients, and braille glyph rendering, both inspired by [this contribution](https://github.com/sharkdp/hexyl/pull/247) by [aticu](https://github.com/aticu) to [hexyl](https://github.com/sharkdp/hexyl)
