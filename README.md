# Language Tutor

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)]
(https://colab.research.google.com/github/renabracha/language_tutor/blob/main/Language_Tutor.ipynb)

## Acknowledgment
I would like to thank the following individuals and organisations that made this project possible.
* Groq for providing me free access to their API key and thereby allowing me to gain hands-on experience in making API calls without having to constantly worry about token limits.

## Abstract
I understand the hype around AI language tutors. You can practice your language skills interactively by having a conversation, which is much more effective than trying to memorise words from a textbook. However, I was not satisfied with the user reviews I read. Apparently, even paid apps were not up to par. So I thought to myself: I know how I want to learn, I know what I need — I will build one myself. This project is the result.
<br>
The program operates in the following sequence:
1. Collect the user's personal details (e.g. name), the language they want to learn (e.g. Spanish), and the preferred gender of the Tutor.
2. Prompt the user to provide a free-text description of the learning scenario. For example: “I want to practice interacting with a shop assistant in a clothing store.”
3. The AI Tutor introduces itself using a name and tone appropriate to the selected language and gender, and the interaction begins in the chosen setting.
4. The AI Tutor engages with the learner in the target language and can switch between languages to explain words and expressions, following the learner’s cues.
5. The program terminates when the learner types a sentinel value ("quit," "exit," or "bye" in English).

## Development Notes
* The AI Tutor is designed to:<br>
  o interact through typing so the learner can learn correct spelling in the target language<br>
  o read aloud the Tutor's response via a “Listen” button so the learner can hear correct pronunciation. (Checking the learner’s pronunciation is outside the scope of this project.)<br>
  o maximise interaction in the target language. The Tutor explains words or expressions in the target language unless otherwise requested<br>
  o let learners ask questions in the target language, English, or any other language, and it responds by switching languages accordingly. As noted in Anthropic's 2025 paper "Tracing the thoughts of a large language model," LLMs gain a language-agnostic grasp of concepts and can express them fluently in multiple languages — much like polyglots who, once they understand an idea, can explain it in any language they know. This project leverages that ability, allowing learners to ask how to express a culturally nuanced phrase or idea from one language in another<br>
  o assume the persona appropriate to the scenario. For instance, if the learner selects a café setting, the Tutor plays the role of a waiter<br>
  o lead the conversation by introducing relevant topics and vocabulary based on the context. As demonstrated in Google’s 2017 landmark paper *Attention Is All You Need*, and confirmed by my own experience, context is crucial in language learning. You internalise how and when to use a word by actively performing related actions. For example, you truly grasp the meaning of 'ordering a coffee' when you imagine yourself standing at a bustling café counter, speaking to a barista in your target language.<br>
* The learner's input field is sized for a single line of text, as conversation typically involves short utterances rather than long monologues.
* The Tutor's response is stored temporarily and can be read aloud directly by clicking the "Listen" button. This method is more efficient than saving responses as .mp3 files to Google Drive and loading them when they are requested.
* Specifying the learner’s gender and selecting an opposite-gender for the Tutor allows the program to showcase gender-specific verb conjugation in the target language.
* Selecting a gender for the Tutor that is opposite to that of the learner allows the learner to see verb conjugation in the target language for both genders.
* The model’s temperature parameter is set to 0.8 to foster creative, natural-sounding dialogue.

## Challenges
* To display the “Listen” button under the Tutor’s response, I had to use tools compatible with Google Colab. This required a trade-off: while I could leverage Colab's temporary audio storage, I could not specify the voice’s gender, which occasionally led to a mismatch between the Tutor’s stated gender and the voice used. Claude helped adapt the implementation to work smoothly in Colab.
* Initially, clicking the “Listen” button did not play the audio unless I interrupted the execution of the “Run the tutor” cell. Claude required several attempts to resolve the timing issue.
* I experienced in this project that prompt engineering is truly an iterative process. Through testing, I realised I needed to embed the scene description into the prompt and align the Tutor’s identity with the role-play character to maintain gender-appropriate conjugation and avoid confusing the learner with three participants instead of two.
* The memory used to summarise the ongoing conversation proved unreliable. In one café scenario, the Tutor-waiter forgot the conversation history after just six turns and asked me again what I wanted to order. Claude proposed a custom class to improve memory persistence, but I chose not to pursue that for this project. That will be an area for future improvement.

## Web app in action
![Alt text for screen reader](https://github.com/renabracha/language_tutor/blob/main/screenshot.jpg?raw=true)