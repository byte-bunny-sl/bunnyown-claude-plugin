---
name: edit-guest-message
description: Reword an email that BunnyOwn sends to guests or staff, such as a booking confirmation, safely - read it and its placeholders, preview the result with sample data, and save only after the person agrees.
---

# Edit a guest message on BunnyOwn

Use this when someone wants to change the wording of a message their
booking process sends. Examples are the confirmation, the "request
received" mail, the decline, or the payment link. A saved message is what
every future guest receives, so nothing is written until the person has
seen the result and agreed.

## 1. Find the message

1. Call `list_message_templates`.
2. Match the person's description to a message id and language. The
   template's subject and body show what each message is.
3. If more than one could match, or the language is unclear, ask.

## 2. Read it

Call `get_message_template` for that id and language. Note:

- the text in force, and whether it is `stock` or the business's own
  (`custom`);
- the placeholders the message may use, with what each stands for.
  Only these placeholders are filled in;
- `fallback: true`, which means the language has no text of its own and
  guests get the English one.

## 3. Draft and preview

1. Write the new subject and body in the person's voice.
2. Keep every placeholder that carries something the guest needs, such as
   dates, links and the booking title. Use only placeholders from the list.
3. Call `preview_message_template` with the draft. It renders sample
   booking data and stores nothing.
4. Show the person the rendered subject and body, and say which
   placeholders were added or removed.

If they want changes, revise and preview again.

## 4. Save only with a yes

When the person agrees with the preview, call `put_message_template` with
the same id, language, subject and body. Leave out `decisions` so the
message keeps its own action links.

Confirm what was saved. Mention that a later reinstall of the booking
process keeps the business's own wording.

## Going back

If the person wants the platform's original text back, tell them that
`reset_message_template` overwrites their wording for that message and
language. Call it only after they confirm.

## Not covered here

- WhatsApp texts are changed and submitted on the dashboard's Messages
  screen.
- The tools cannot send a test message to a guest.
