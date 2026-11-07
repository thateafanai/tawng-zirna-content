# Ṭawng Zirna content

Content for the Ṭawng Zirna language-learning app by BABFO. The app reads these
files when a learner taps **More → Check for updates**. It only downloads; it
never sends anything.

Published at <https://thateafanai.github.io/tawng-zirna-content/> (GitHub Pages).

## Files

| File | What it is |
|---|---|
| `index.json` | The list of packs and their versions. The app reads this first. |
| `packs/core.json` | English, Hindi and Mizo starter content (pack `core`). |
| `packs/community-<code>.json` | Later: approved community words for one language, e.g. `community-nnp` (Wancho). Only learners of that language download it. |
| `spelling/nnp.json` | Wancho spelling list for typing suggestions: 24,073 words with how often each is used, from the Otsao Baibel (Bible Society of India, 2012). Words only, never verses; names left out. Only Wancho learners download it. |

## Spelling lists

Made on the computer with the app's `tool/make_spelling_list.py` (see the
instructions at the top of that file). To update one, run it with
`--version` raised by 1, raise the `version` in `index.json` too, check, push.

## Publishing an update

1. Edit the pack (add or correct entries, or list removed uids in `deleted`).
2. Raise the pack's `version` by 1, **in the pack and in `index.json`**.
3. Check it, from the app's project folder:
   `dart run tool/check_content.dart ../tawng-zirna-content`
4. Commit and push. Phones get it the next time they check for updates.

## Rules

- **Never change or reuse a published `uid`.** Remove an entry by listing its uid
  in `deleted`.
- A pack only changes what it brought itself: a community pack adds its language
  to an entry but never changes the core pack's English, Hindi or Mizo.
- A learner's own words always win over pack content on their phone.
- Mizo marked `"status": "draft"` has not been checked by a native speaker yet.
- A community pack's `language` field in `index.json` must be the language's
  shared code (ISO 639-3, e.g. `nnp` for Wancho).
