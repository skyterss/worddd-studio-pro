# Word Studio Pro — Desktop-Grade Rich Text & Document Processor (`.DOCX`, `.DOC`, `.PDF`)

A self-contained, responsive **Microsoft Word Desktop Web App & Android Tablet/Foldable Application** engineered for hardware keyboards (Bluetooth, USB-OTG, and built-in pogo-pin folios), multi-format document processing (`.docx`, `.doc`, and `.pdf`), and on-screen virtual keyboard suppression.

## Features Included

1. **Desktop-Grade Ribbon UI & Paged Canvas**:
   - Classic Microsoft Word `#185ABD` Title Bar with Quick Access Toolbar (Save, Open, Undo, Redo, Print/PDF) and live Auto-Save status badge.
   - Full Ribbon tabs (`File`, `Home`, `Insert`, `Layout`, `Review`, `View`) with Font Family, Font Size (`8pt`–`48pt`), Grow/Shrink Font, Bold, Italic, Underline, Strikethrough, Subscript, Superscript, Font/Highlight colors, Lists, Indents, Line Spacing, Paragraph Alignment, Quick Styles (`Normal`, `H1`, `H2`, `H3`, `Quote`), Table generator, Image uploader, Vector Diagram inserter, Hyperlinks, Page Margins, Portrait/Landscape Orientation, Paper Size (`A4` / `US Letter`), Columns, Track Changes, Comments, Word Count Statistics, and Read Aloud TTS.
   - Interactive **Horizontal Ruler** with draggable Left & Right margin markers.

2. **Multi-Format Document Engine (`.DOCX`, `.DOC`, `.PDF`)**:
   - **`.DOCX` Import & Export**: Parses `.docx` files using **Mammoth.js** (with a built-in OpenXML `word/document.xml` stream fallback) and exports `.docx` files via **docx.js** (with a pure-JS OpenXML ZIP builder fallback).
   - **`.DOC` Import & Export**: Parses legacy Word 97–2003 `.doc` files (OLE2 binary UTF-16LE/ASCII text streams, RTF-encoded `.doc`, and Office HTML/XML `.doc`) and exports Word-compatible `.doc` documents with `WordSection1` page geometry.
   - **`.PDF` Import & Export**: Extracts multi-page `.pdf` documents using **PDF.js** coordinate reconstruction (with a native PDF `Tj` stream fallback) into editable paragraphs on the Word canvas, and exports paginated `.pdf` files via **html2pdf.js / jsPDF** + native `@media print` stylesheets.
   - **Built-in Format Verification Lab**: Click **DOCX / DOC / PDF Lab** in the top bar to synthesize and test real `.docx`, `.doc`, and `.pdf` binaries directly in-browser.

3. **Deep Hardware Keyboard & Virtual Keyboard Suppression**:
   - Full `keydown` interceptor (`Ctrl+B`, `Ctrl+I`, `Ctrl+U`, `Ctrl+Shift+>/<`, `Ctrl+E/L/R/J`, `Ctrl+S`, `Ctrl+O`, `Ctrl+Z`, `Ctrl+Y`, `Ctrl+F`, `Ctrl+P`, `Ctrl+K`, `Ctrl+Enter`, `Tab`/`Shift+Tab` table cell cycling, and `Enter` at the end of a table to append a row).
   - Floating & docked **Virtual Keyboard: Active / Hidden** toggle using both `navigator.virtualKeyboard.hide()` (`virtualKeyboardPolicy="manual"`) and `inputmode="none"` fallback so typing on a physical keyboard never triggers the on-screen soft keyboard.

## How to Upload to GitHub & Release the Android APK

1. Extract this archive and push all files to a new GitHub repository:
   ```bash
   git init
   git add .
   git commit -m "Initial release: Word Studio Pro (.DOCX, .DOC, .PDF) + Android APK project"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-repo>.git
   git push -u origin main
   ```
2. **Automatic GitHub Actions APK Build**:
   - As soon as you push to `main` (or trigger **Actions → Build & Release Android APK → Run workflow**), GitHub Actions compiles the native Android WebView wrapper (`WordStudioPro-Android-Universal.apk`) and publishes it to your repository's **Actions Artifacts** and **GitHub Releases**.
3. **Local APK Build (Android Studio / Gradle)**:
   ```bash
   cd android
   gradle assembleRelease
   ```
   The compiled APK will be output to `android/app/build/outputs/apk/release/app-release.apk`.
