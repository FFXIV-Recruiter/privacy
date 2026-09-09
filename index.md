---
title: Privacy Policy — Alpha
---

# Privacy Policy — Alpha

**Last updated:** 2026-09-09

Alpha is a recruitment-management bot operated for a single Final Fantasy XIV
community Discord server. It is not a public, listed bot and is not offered to
other servers. This policy explains what it stores, why, for how long, and how
you can have it deleted.

If you use the bot's registration features, this policy applies to you. If you
only chat on the server, the only processing that concerns you is the anti-scam
filter described in section 3.

## 1. Who operates the bot

Alpha is operated by the staff team of the community server it runs on. There is
no company behind it, no advertising, and no sale or sharing of data with third
parties beyond the technical providers listed in section 5.

**Contact:** reach the server's moderation team through the server's modmail.
If you no longer have access to the server, write to `<CONTACT ADDRESS>`
instead.

## 2. The recruitment registry

When you link your in-game character to your Discord account, the bot stores:

- **a SHA-512 digest of your Discord user ID** — not the ID itself;
- **a randomly generated identifier (UUID)** associated with that digest, which
  is what everything else is attached to;
- **your declared FFXIV character**: name, home world, data centre and Lodestone
  ID, plus the public character data the bot retrieves from those services
  (job, level, race, free company, portrait URLs, and similar);
- **your registration record** for the server's recruitment listings.

This is *pseudonymisation*, not anonymisation. The digest is deterministic, so
the bot recognises you if you return. We do not claim it is irreversible to
someone who already holds a list of candidate Discord IDs. It does mean the
registry itself contains no directly readable Discord identifier.

**Why:** this is the service you asked for — it is what makes character
verification and recruitment listings work. You provide it voluntarily and can
remove it at any time (section 7).

## 3. Anti-scam moderation

The server is a recurring target for fraudulent recruitment offers that push
members toward off-platform contact, phone numbers and malicious links. The bot
screens messages to detect them.

**Not every message is examined.** A local check runs first, inside the bot, and
a message goes no further unless it shows a fraud signal: a phone-number
pattern, an external link, or an author who is new to the server or has no
assigned roles. Staff, moderation and bot channels are excluded from screening
entirely. Messages that do not match are discarded immediately and are never
stored, transmitted or logged.

A message that does match is sent to a hosted classification model, which
returns only a verdict and a confidence level. **Message content is never
written to our database.** It exists briefly in an internal processing queue —
seconds, until consumed — and in the request to the classifier.

If a message is classified as fraudulent, the bot applies a graduated response
(deletion, then a temporary timeout, then a ban for repeat offences) and records
the decision in a private, staff-only channel inside the Discord server, where a
short excerpt of the offending message may appear so moderators can review it.

**Why:** protecting members from fraud is a legitimate interest of the server.
There is no opt-out, because a fraud filter that scammers could opt out of would
protect nobody. The scope is limited by the channel exclusions and the local
check described above rather than by consent.

## 4. Server and moderation records

The bot also stores:

- **server configuration**: the Discord IDs of the server and its owner, and the
  server's bot settings;
- **a moderation ledger of scam offences**: the Discord IDs of the user, server,
  channel and message involved, an offence weight, the detection stage and a
  timestamp. **No message content is stored here.**

The moderation ledger is kept for the security of the server. Deleting it when a
member leaves would make it trivially defeated by leaving and rejoining, so it
is retained beyond a member's departure.

## 5. Third parties

- **Discord** — the platform itself, under its own privacy policy.
- **A hosted AI classification provider** — receives the text or image of
  messages flagged by the local check, for classification only. Requests are
  sent with a data policy that **excludes providers which retain or train on
  request data**. This content is not used to train, fine-tune or evaluate any
  model, ours or theirs.
- **Square Enix Lodestone and FFLogs** — public game services the bot reads
  character and raid-progression data from. We send them your declared character
  name and world; we send them nothing about your Discord account.

We do not sell data, we do not use it for advertising, and we do not share it
with anyone else.

## 6. How long we keep it, and where

| Data | Retention |
|---|---|
| Recruitment registry (character link, registration) | Until you delete it, or until you leave the server — whichever comes first |
| Message content | Not stored; transient only (seconds in a processing queue) |
| Moderation ledger of scam offences | Retained for server security |
| Server configuration | While the bot is on the server |

Data is held in a self-hosted PostgreSQL database on hardware we control. The
database is **encrypted at rest**. Access is restricted to the server's
technical administrators.

## 7. Deleting your data

Three routes, no ticket required:

1. **Do it yourself in the bot.** `/unregister` erases your own record —
   character link, registration and membership row — immediately, without any
   moderator involvement. `/unlink` removes a character association on its own.
   `/unregister` requires one of the datacenter roles, which registration grants
   automatically; if the bot tells you that you lack permission, use route 3
   below.
2. **Leave the server.** Your registry data is deleted automatically, with no
   action needed from you.
3. **Ask a human.** Any server moderator can run the removal on your behalf.

The moderation ledger described in section 4 is the one exception: it is
retained for server security, as explained there. If you believe a record about
you is wrong, contact a moderator — entries can be reviewed and corrected.

## 8. Your rights

You can ask what is held about you, ask for it to be corrected, or ask for it to
be deleted, using the routes in section 7 or the contact above. If you are in
the EU or UK, you also have the right to object to processing and to lodge a
complaint with your national data protection authority.

## 9. Children

The bot follows Discord's Terms of Service, which require users to meet the
minimum age for their country. We do not knowingly hold data for anyone below
that age; tell a moderator if you believe we do, and it will be removed.

## 10. Changes

Material changes to this policy will be announced on the server. The date at the
top reflects the last revision.
