# MSAI-631 Traditional Chatbot

**Created by:** Rajesh Sahoo
**Assignment:** Prototype Simple Traditional Chatbot Project
**Week:** 3
**Course:** MSAI-631 — Artificial Intelligence for Human-Computer Interaction
**Institution:** University of the Cumberlands

---

## Overview

This project is a prototype of a simple **traditional (non-LLM) chatbot** built in Python using the NLTK library's pattern-matching `Chat` engine. It serves as the foundation for a follow-on assignment in which the bot will be extended by connecting it to an AI-as-a-Service offering (Azure Cognitive Services).

The chatbot is implemented as a Google Colab notebook so it can be opened and run in the browser without any local environment setup.

---

## Features

The chatbot satisfies the three functional requirements of the assignment:

1. **Responds to multiple prompts** — greetings, identity questions, time, jokes, small talk, thanks, and farewells.
2. **Lists its own capabilities** — when the user types `help` or `what can you do`, the bot returns the full list of intents it understands.
3. **Handles malformed or unknown input** — anything outside the rule set returns a polite fallback message guiding the user back to `help`.

Additional design considerations:

- A single `get_response(user_input)` entry point isolates all response logic, making the bot easy to extend with an external AI service in the next assignment.
- Empty input is handled separately from unknown input for a cleaner user experience.
- The pattern list is ordered so common intents (greeting, help, exit) match first.

---

## Files

| File | Purpose |
|---|---|
| `traditional_chatbot.ipynb` | The complete Colab notebook — 6 cells, from setup through interactive chat. |
| `README.md` | This file. |

---

## How to Run

### Option 1 — Google Colab (recommended)

1. Open `traditional_chatbot.ipynb` in this repository.
2. Click the **Open in Colab** badge at the top of the notebook.
3. From the Colab menu choose **Runtime → Run all**.
4. Scroll to the last cell and type messages into the input box that appears below it.

### Option 2 — Local Jupyter

```bash
pip install nltk
jupyter notebook traditional_chatbot.ipynb
```

Then run each cell top-to-bottom.

---

## Example Conversation

```
HelpBot v1.0: Hi! Type 'help' to see what I can do, or 'bye' to quit.

You: hello
HelpBot: Hi there!

You: help
HelpBot: Here's what I can do:
- Greet you (try: hi, hello)
- Tell you what I can do (try: help, what can you do)
- Tell you my name (try: who are you, what is your name)
- Tell the current time (try: what time is it)
- Tell a joke (try: tell me a joke)
- Do basic small talk (try: how are you)
- Say goodbye (try: bye, quit, exit)

You: what time is it
HelpBot: The current time is 01:47 AM

You: tell me a joke
HelpBot: Why did the developer go broke? Because he used up all his cache.

You: asdfghjkl
HelpBot: I didn't understand that. Try asking for 'help' to see what I can do, or rephrase your question.

You: bye
HelpBot: Goodbye!
```

---

## Technology Stack

- **Language:** Python 3 (Google Colab default)
- **Library:** [NLTK](https://www.nltk.org/) — `nltk.chat.util.Chat` for regex-based pattern matching and `reflections` for pronoun swapping
- **Environment:** Google Colab (no local installation required)

---

## Chatbot Development Lifecycle Mapping

This prototype illustrates the early phases of a chatbot development lifecycle:

| Lifecycle Phase | In This Project |
|---|---|
| Requirements | Three functional requirements drawn from the assignment instructions. |
| Persona / User Identification | Implicit — a general end-user trying out a help bot. |
| Conversation Design | Capability list, intents, and fallback message authored before coding. |
| Implementation | Rule-based pattern matching with NLTK. |
| Testing | Interactive testing covering greeting, help, time, joke, malformed input, and exit. |
| Iteration | Patterns reordered to ensure correct precedence (greeting → help → specific intents). |
| Extensibility | `get_response()` seam reserved for the next-assignment AI-as-a-Service hook. |

---

## Next Steps (Future Work)

- Replace the fallback branch in `get_response()` with a call to **Azure Cognitive Services** (Language / Text Analytics) so the bot can interpret unknown inputs with NLP rather than returning a canned message.
- Add sentiment-aware responses by routing user messages through Azure sentiment analysis.
- Capture conversation logs for evaluation and iteration.

---

## License

This project was created for academic coursework at the University of the Cumberlands and is shared here for instructor review.
