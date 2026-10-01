# Dart for Deck

The Dart and Flutter language server, plus the Awesome Flutter snippets.

Claims `.dart`, and a project is anything with a `pubspec.yaml`.

## The server

Found by searching for the SDK rather than by name. `dart` on PATH is usually `dart.bat`, a shim
that `std::process::Command` cannot launch, so `lsp.rs` resolves the real `dart.exe` out of the
SDK — the one case in Deck where finding a server needs more than a name, and the reason this
definition uses the `exe-search` strategy.

Needs a Flutter or Dart SDK on PATH. Nothing to install beyond that.

## The formatter width is not here

It comes from Deck's `formatLineLength` editor setting, injected when the server is configured.
Pinning it in this file would make it a property of the language rather than of your preference.

## Snippets

`snippets/awesome-flutter.json` is [Awesome Flutter Snippets](https://github.com/Nash0x7E2/awesome-flutter-snippets)
by Neevash Ramdial, MIT licensed, with `stless` and `stful` prefix aliases added.

## Installing it

From inside Deck: **Settings -> Plugins -> Browse**, pick it, and it loads straight away.

By hand: copy this folder into `%APPDATA%\Deck\languages\` (`Deck-Dev` for a debug build).
`docs/languages.md` in the Deck repository documents the format.

## What a definition can and cannot do

It is **data**, not code. `language.json` is parsed field by field and never executed, which is
why a language is a different kind of thing from a plugin even though both are folders Deck
reads at startup. The worst a malformed one can do is skip itself.
