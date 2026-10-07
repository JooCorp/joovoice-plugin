---
name: onboarding
description: Set up JooVoice after install, when the owner chooses Set up for JooVoice or asks to get started. Checks the account, finishes setup and offers the welcome call.
---

# Set up JooVoice

Call `check_account` with `{}` and follow its `next`.

- Do each setup step here when a reply's `next` offers it (asking for their name
  and saving it, starting the welcome call). For the rest, give the owner the link
  from the reply and call `wait_for_setup` until it's done.
- The welcome call is a short free call to the owner's own verified number that
  shows what a JooVoice call sounds like. Offer it as a choice: start it with
  `start_welcome_call` once they say they're ready to pick up, or skip it with
  `skip_welcome_call` if they'd rather not.
- Credits are bought on JooVoice's own page: for the credits step, give them the
  link from the reply straight away, and call `wait_for_setup` while they buy.
  For every step you can do here, they never need to open JooVoice.
- Once setup is done, ask who they'd like called first. If they installed JooVoice in
  the middle of a task, carry on with that task in this conversation.
