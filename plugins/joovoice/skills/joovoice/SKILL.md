---
name: joovoice
description: Make a phone call for the owner with JooVoice and report what was said: bookings, appointments, changes, cancellations, refunds, questions, or a personal call like a birthday wish. Use when the owner wants someone called, or asks about a call JooVoice made.
---

# JooVoice

JooVoice makes phone calls for the owner, to businesses and (with a Start link they
open first) to people. The JooVoice tools guide
every step themselves, so this skill only says when to use them and how to work
with their replies.

- Start with `check_account`, then follow its `next`.
- If JooVoice's tools are missing from this chat, or a call says authentication
  is required, JooVoice needs the owner to sign in again. Never say the tools are
  unavailable, and don't ask whether to start: they already asked for the call.
  In Codex, run `codex mcp login joovoice` right away, outside the sandbox
  (it needs the network and a local callback: ask for escalated permissions with
  the reason "Sign in to JooVoice"), and give them the link it prints, in one line: "JooVoice needs you to sign in. Open this link and
  we'll carry on: <link>". They open it on this computer; the JooVoice page
  lets them sign in there or approve on their phone. Keep that command running
  and keep checking it (in Codex, poll the running command) rather than asking
  them to say when they're done: it exits by itself the moment sign-in
  finishes, usually within a minute or two. Then call `check_account` and
  carry on with their request. If it hasn't finished after 10 minutes, ask
  whether the page opened. If the tools still don't appear after it finishes,
  ask them to start a new chat. If the command says no server by that name, run
  `codex mcp list`, find the JooVoice server's name there and log in with it.
  Never add, edit or remove MCP servers or config yourself. Not seeing it there
  doesn't mean it's gone (the terminal's Codex can differ from this app's), so
  don't suggest reinstalling. If signing in still can't
  start, don't drop their request or send them elsewhere: say in one line how to
  sign in themselves (in Codex, run `codex mcp login joovoice` in a terminal or
  use the JooVoice plugin's sign-in), keep what they asked for, and carry on the
  moment JooVoice answers. Elsewhere, point them to this app's sign-in for
  JooVoice. Never ask for their JooVoice password or sign-in codes in the chat.
- Every reply has `meaning` (for you), `sayToOwner` (tell the owner, in your own
  words) and `next` (the calls to make). Follow `next`; don't guess or skip ahead.
- Calls go to businesses, or to a person who first says yes through a Start link
  JooVoice prepares (a personal call). Never offer to call the owner's own number.
- When gathering a call, ask in the same message what to do if their first choice
  isn't available (another time, another day, the nearest slot), unless you
  already know what they'd want. Offer the choices; don't pick for them. For a
  call to a person, also ask what to tell them first and whether they may have
  the owner's number.
- When JooVoice has questions, judge each one: answer what you're confident of
  from the conversation with `answer_questions`, and ask the owner only what is
  unclear, theirs to decide, or speaks for them (a message in their name,
  sharing their number) unless they already said. When there is something to
  ask, use `ask_owner` if you have it: a short form opens here in this chat
  (say so; it's not a website), with what you know in `prefill`. If it closes,
  ask in chat. If they asked you to handle it ("just book it", "you decide"),
  choose preferences yourself and tell them what you chose. Never invent facts
  only they know: names, numbers, references.
- Every question can be answered here, card details and codes included: ask
  only for what's needed, send it, and never repeat it back.
- For a personal call you may write the short note on their Start link
  (`invitationNote`); ask about it only if it seems to matter. The final review
  shows it.
- If a call needs Premium or more credits, say so plainly and make the payment
  link `next` offers (`get_payment_link`); don't call it a price to review.
- When a call reaches final review, goes live or finishes, show it with
  `show_call` (a card in this chat that follows the call, with Approve and Stop
  buttons) rather than retyping it, then answer what the owner asks.
- When a reply links to a JooVoice page (sign-in, approval), give the owner the
  link, then use the wait tool it names.
- If this app blocks a JooVoice tool call (for example, approvals are turned
  off in this session), JooVoice is still connected; don't tell the owner the
  tools are unavailable. Say which step was blocked and offer the button on the
  call card or the JooVoice link for it.
