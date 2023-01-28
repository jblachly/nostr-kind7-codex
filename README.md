# nostr Kind 7 Codex
_Unofficial Registry of nostr kind 7 events_

## Status

`Draft`

This document is informational. The catalogue is non-normative.

## Background

NIP-25 [1] defines event kind `7` as a reaction to a referenced note. The NIP suggests that clients SHOULD interpret `+` as like or upvote, and `-` as dislike or downvote.

With the proliferation of clients has come a little Wild West of kind 7 reaction texts, with no central catalogue of what is in use making it difficult for client (or relay) writers to confidently capture as many as possible.

Fortunately, what has emerged so far is logical, with for example a thumbs up emoji (👍) being emitted/interpreted like `+` and thumbs down emoji (👎) being emitted or interpreted like `-`.

Other clients, like nostr_console, use other kind 7 events as notes-to-self. For example, the `!` is used to hide a post. It is expected that other kind 7 messages will emerge with additional semantic meanings.

[One recent note](https://snort.social/e/note17wkwa42u4nn3ur8v94qcc73xksxj7crc0v9w738jwcsym8trz9lsw5ylnt) suggests consideration of emojis like ⚠️ and 🔞 which convey (relatively) obvious meanings to human readers, and are just as short as a binary serialization of some message like "inappropriate", "flagged", "NSFW", etc.

By providing a centralized record of who-supports-what and which-encodes-something, the nostr ecosystem might be able to more quickly coalesce around standardized kind 7 signals.

## Kind 7 event messages
_seen in the wild or widely implemented_

|   | Interpretation  | Reference         |
| - | --------------- | ----------------- |
| + | Like            | Defined in NIP-25 |
| - | Dislike or Flag | Defined in NIP-25 |
| ! | Hide post       | [nostr_console](https://github.com/vishalxl/nostr_console/blob/f376e58abcdcb87f8f95a81e0b8eaf01099fa423/lib/console_ui.dart#L1358) |
| ⚠️ | Report post     | [amethyst](https://snort.social/e/note17wkwa42u4nn3ur8v94qcc73xksxj7crc0v9w738jwcsym8trz9lsw5ylnt) |
| ❤️ | Like | |
| 🤙 | Like | |
| 👍 | Like | |
| 👎 | Dislike | |

## Client Support

| Client       | + | - | ❤️ | 🤙 | 👍 | ⚠️ |comments |
| ------------ |---|---|---|---| --- |---|-------- |
| Amethyst     | ✅ |   | 👀 | 👀 | 👀 | ✅ | + , 🤙 , 👍 are converted into ❤️ |
| astral       |   |   |   |   |   |   | no kind 7 reactions |
| Blockcore Notes | 👀 | 👀 |   |   | 👀 |   | Also recognizes 👎. Permits arbitrary emoji reaction. [Tallies and displays several kind 7](https://github.com/block-core/blockcore-notes/blob/733e246e5ff5a0952af3b7bbe0119ba0aa2f7fd0/src/app/services/thread.ts#L253) |
| Branle       |   |   |   |   |   | |   |
| Coracle      | ✅ | ✅ | 👀 | 👀 | 👀 |   | [also recognizes empty kind 7](https://github.com/staab/coracle/blob/59c4fec4f0ed0c621597a522e97aa881a87fa576/src/util/nostr.js#L63) |
| Daisy        | ✅ |   |   |   |   |   |   | |
| Damus        | 👀 | 👀 | 👀 | ✅ | 👀 | 👀 | Damus aggregates all reactions as "like". Originated the Shaka 🤙 |
| futur        |   |   |   |   |   |   | parsed but not emitted |
| Gossip       | ✅ |   |   |   |   |   | [also recognizes empty kind 7 as like](https://github.com/mikedilger/gossip/blob/56813ae772e02bd627d393da4f8cd8ca687ada14/src/globals.rs#L170) |
| Iris         | ✅ |   |   |   |   |   | |
| Minds        | ? | ? |   |   |   |   | |
| more-speech  |   |   |   |   |   |   | no kind 7 reactions |
| noscl        |   |   |   |   |   |   | does not support KindReaction |
| nostr-java   | ✅ | ✅ |   |   |   |   | |
| Nostrid      | ✅ |   |   |   |   |   | [also recognizes empty kind 7 as like](https://github.com/lapulpeta/Nostrid/blob/fa28e2b99736573b5be8dd9a4fb7cb3154314a21/Nostrid.Core/Shared/NoteViewer.razor#L231) |
| snort.social | 👀 | 👀 | 👀 | 👀 | 👀 |   | [also recognizes 💯 and empty kind 7 as like; also 👎 as dislike](https://github.com/v0l/snort/blob/3cbec9f2727825558aec7be457d0b42074d8ffdf/src/Util.ts#L103) |

✅ Emits
👀 Recognizes

## Relay Support

_TBD_; filtering and interpretation is likely to be mostly client-side, but Relays will probably be informed by kind 7 reactions in the future.


## References
1. Reactions, defined in [NIP-25](https://github.com/nostr-protocol/nips/blob/master/25.md)
2. [Client list](https://github.com/aljazceru/awesome-nostr#clients)
