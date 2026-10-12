---
name: set-up-booking-website
description: Set up or extend a BunnyOwn booking website from a description of what the business rents or sells, using the BunnyOwn connector's tools for types, listings, pages and the booking process.
---

# Set up a booking website on BunnyOwn

Use this when someone wants their BunnyOwn website to take bookings for
something new: villas, boats, tours, tables, events, rentals. It also covers
a first setup. Every step uses the BunnyOwn connector's tools on the
workspace the person connected.

## 1. Look before changing anything

1. Call `list_websites`. If there is none, stop and explain that a website
   is created on the BunnyOwn dashboard first; `install_booking_process`
   also needs one. If there are several, ask which website this is for.
2. Call `get_content_model` and `list_entity_types`. Reuse an existing type
   when it fits, rather than creating a near-duplicate.
3. Ask the person, in plain words, about anything you cannot infer:
   - what is booked;
   - how it is booked: whole nights (`stay`), fixed sittings (`slots`),
     dated events (`event`) or tours with departures (`tour`);
   - the price and its currency;
   - the languages their website uses.

## 2. Shape the type (only if no existing type fits)

Draft the type, then show it to the person before saving it:

- slug and localized name;
- the properties and their kinds;
- the site roles (title, image, summary);
- the booking block and its mode.

Name only property kinds and booking fields that `get_content_model`
returned. Then call `create_entity_type`. If the server refuses, read the
message: it names the property or field at fault. Fix that and try again.

## 3. Add the listings

For each listing:

1. Call `get_entity_type`.
2. Call `create_entity` with attributes in every language the website
   declares.
3. For photos the person gives as public https addresses, call
   `import_media` with alternative text in every language. Then attach the
   returned media ids with `update_entity`.

New listings are drafts. They appear on the website only after
`publish_entity`.

## 4. Pages

Draft the pages the person wants with `create_page`, using the sections the
content model describes. Typical pages are a home page with a collection of
the listings, an about page and a contact page. Pages stay drafts until
`publish_page`.

## 5. Connect the booking process

1. Call `list_workflows`. If `booking-request` is missing, explain what
   `install_booking_process` does, then call it. It installs the stock
   booking and messaging process and its stock messages, and sends nothing
   while installing.
2. Call `bind_workflow` with the type's slug and `booking-request`. From
   then on, website requests for that type follow the process.

## 6. Publish only with a yes

Publishing changes the public website and rebuilds it. List exactly what
will go live: each listing and page, and the website. Ask for a clear yes.
Only then call `publish_entity` and `publish_page`. If publishing is
refused because a language is missing, add that language's text and try
again.

## Finish

Summarize:

- what was created;
- what is live, and what is still a draft;
- the website address from `list_websites`.

Suggest a test booking from the website. Mention that guest messages can be
reworded with the "edit a guest message" task.
