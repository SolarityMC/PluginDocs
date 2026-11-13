---
id: chat-prompts
title: Chat Prompts
sidebar_position: 8
---

Some menu buttons ask you to type an answer in chat: a player name to invite, or the text for a
greeting, farewell or title flag. The menu closes and the question appears in chat.

- Your next chat message is the answer. It is never posted to public or town chat.
- You have `Prompts.TimeoutSeconds` to answer (default 120). A warning appears 5 seconds before the
  end, then a 3, 2, 1 countdown, then *Prompt expired.*
- If you send your answer just after it expired (within 15 seconds), it still isn't posted to chat;
  you are told it wasn't saved. Open the editor again to retry.
- `/lc cancel` closes the prompt without changing anything.
- You can have one prompt open at a time. Logging out cancels it.

Set `Prompts.TimeoutSeconds: 0` to remove the timer completely. The prompt then stays open until you
answer, cancel or log out.

The prompt, countdown and expiry messages are fixed text and not in `lang.yml`.
