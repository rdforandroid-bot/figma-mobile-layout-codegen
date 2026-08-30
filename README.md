# Figma Mobile Layout Codegen

Visual Studio Code extension — install from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=android-ios-layoutcodegen.android-ios-layoutcodegen).

Cursor extension — install from the [Cursor extension](https://open-vsx.org/extension/android-ios-layoutcodegen/android-ios-layoutcodegen).

Layout and screen codegen from Figma for **native mobile** — **separate outputs per platform**, not a single cross-platform codebase.

## Videos

1. [Figma ZIP file into a live app demo](https://www.youtube.com/watch?v=QOVnilCZAAQ)
2. [Canvas Selection + SoM Prompt Composer](https://www.youtube.com/watch?v=G10twPJXWu0)
3. [JSON & Image ZIP Export Figma Plugin](https://www.youtube.com/watch?v=tqI2a4K4CB4)
4. [SoM + Prompt Composer（Cursor / VS Code）](https://www.youtube.com/watch?v=_-o53kWRggQ)
5. [Create RecyclerView Demo](https://www.youtube.com/watch?v=9EkmLbXcRCk)
6. [Create BottomNavigationBar Demo](https://www.youtube.com/watch?v=dxT2NnOLbmQ)
7. [Create Tab Bar Demo](https://www.youtube.com/watch?v=LUGZOeqyQ_U)

## Demos

### Figma export → mobile codegen

Export a ZIP from Figma, open it in the extension, then export native mobile layouts to your project.

![Figma export ZIP to mobile codegen](https://raw.githubusercontent.com/rdforandroid-bot/figma-mobile-layout-codegen/main/figmaToApp.gif)

### Prompt Composer + SoM

Tag elements on the canvas, submit in **Prompt Composer**, and get SoM JPEG screenshots with numbered markers plus `.spec_prompt.md`.

![Prompt Composer Submit generating SoM screenshots and spec_prompt.md](https://raw.githubusercontent.com/rdforandroid-bot/figma-mobile-layout-codegen/main/composer%20and%20AI%20agent.gif)


## Platforms

- **Android:** Java with XML, Kotlin with XML, Kotlin with Jetpack Compose
- **iOS:** Swift with SwiftUI, Swift with UIKit
- **Flutter:** In development (Flutter with Dart)

Includes a Figma-driven layout editor, platform-aware export, and context menus for native UI patterns (lists, navigation, sheets, dialogs, and more).

All export modes are **token-free** (rule-based codegen, not LLM generation).
Image assets stay on your machine and are not uploaded to the server; only Figma JSON is sent when server-side processing is needed.

## Export modes

- **Export UI Layouts Only** — UI files only, no ViewModel
- **Export MVVM Template** — Optional MVVM scaffold (View + ViewModel); layouts and structure, not full app or business logic
- **Export Interactive Preview** — Runnable preview with sample data (default)
- **SoM + Prompt Composer** — On Prompt Composer Submit, generates SoM JPG screenshots with numbered markers and a `.spec_prompt.md` file; does not export plugin-generated code in this mode

## Prompt Composer

Open the **Prompt Composer** tab in the right panel.

- **Select exact elements** — Tag UI on the **canvas** or in **Layers** (Ctrl/Cmd+click); the prompt binds to the exact target.
- **Assign product behavior** — e.g. “this button signs the user in”, “this field validates email”.
- **AI edits without guessing** — Structured references (file paths, locators, IDs) instead of vague “the button on the home screen”.
- **SoM numbered visual references** — Optionally adds Set-of-Mark (SoM) JPEG screenshots with numbered markers for tagged components, so the AI can locate each target visually.
- **Ready for your AI editor** — Writes `.spec_prompt.md` with **# Context** and **# References**; clipboard includes **# Task** for Chat.

## Usage

1. Install the [JSON & Image ZIP Export Figma plugin](https://www.figma.com/community/plugin/1647672984943418293) and export your design as a ZIP from Figma
2. Command Palette → **Figma Mobile Layout Codegen: Open Editor**
3. Import the Figma export ZIP
4. Right-click on the canvas or in Layers to create lists, navigation, sheets, dialogs, etc.
5. Set export path and run **Export All** (or another export mode)
6. Use **Prompt Composer** to tag elements and submit structured prompts to your AI assistant

## UI icons (licensing)

Icons in the webview UI (Layers panel, context menus, toolbar, page tree, visibility toggles, expand chevrons, and related controls) are **inline SVG assets defined in this project** (`webview/app.js`). They are simple stroke icons created for this extension.

- They are **not** taken from third-party icon fonts or packs (e.g. Font Awesome, Material Icons, Lucide).
- **No separate attribution** is required for those UI icons when you ship or use this extension commercially.
- npm dependencies remain subject to their own licenses (see `package.json` / `node_modules`).

## Tech stack

- **Webview UI**: HTML, CSS, JavaScript (`webview/`)
- **Extension**: TypeScript, VS Code Extension API (`src/` → `out/`)
- **Layout**: Flexbox-based responsive panels
- **Theme**: Light/dark styling aligned with the editor UI
