# Speak to Lichess 2.1 

Provides Speech Recognition to Lichess.org games. Uses the Web Speech API to process speech and the Lichess Board API to read the board state and submits moves. API move submission available in Rapid, Classical, and Correspondence time formats. Blitz or faster time formats require some keyboard input and the use of SAN format moves specifically.

Supports standard games; alternative modes (such as crazyhouse, 'from position', etc.) should support UCI format moves, but will likely be unable to correctly process SAN format moves.

Check out the 'Using this Extension' section to learn how to effectively dictate moves.

2.1 Board State Tracking Demo: 

2.0 Demo (SAN moves and text input sections out of date): https://www.youtube.com/watch?v=FB0uJwfo87k

Chrome Web Store: https://chrome.google.com/webstore/detail/speak-to-lichess/ldiiocggpmgljihlkgpngjlhnggpapig 

Commands, SAN and UCI examples, and well-recognized words: https://docs.google.com/spreadsheets/d/1g6cGDRYvjGPj2gqeEMUVYwbZG3xjz_SrX_2q9z0Tsxo/edit?usp=sharing

### Adding Your API Token

A personal Lichess API token is required to use automatic submission. From the options page, you can navigate to Lichess's personal token creation page. The name and required scope will already be set; do not add any additional permissions. Simply press the blue 'submit' button and copy the generated token. Close this page and paste your token into the appropriate field in options; then press 'enter' or submit. The red Icon will turn green if a valid token is provided.

The 'delete stored token' button will delete your token from this extension. Note, however, that the token is still valid for your Lichess account. If you feel your token has been compromised, make sure to delete it on Lichess as well: https://lichess.org/account/oauth/token

**--Warning: Do not add additional permissions to your token! Token is stored in plain text!--**

Read more about the Lichess Board API here: https://lichess.org/blog/XlRW5REAAB8AUJJ-/welcome-lichess-boards

### Using this Extension

Now that you have provided an API key, the extension is ready for use. It's recommended that you play a rapid, classical, or correspondence game against the computer first to get a feel for the extension. Be sure to read the "Successful Dictation" section below.

The 'ctrl' key is used for either 'toggle' or 'push-to-talk' recording. You should see the message at the bottom right of the board change to 'listening...' when the extension is recording. Say your move clearly. When you are finished speaking, the extension will attempt to use your processed voice data to create a valid chess move. You should see a 'success' or 'failure' message below the board. You can also view the console (f12) for more info.

Correctly interprets 'capture', 'take', 'short', 'long', 'castle', 'promote', 'equals' into chess notation. Note that supplemental words such as 'capture' and 'promote' can be omitted. 

### Successful Dictation

**To specify a column, you will have much more success saying a word that begins with that letter, such as "delta" for the d column, than you will saying the actual letter. The speech processing service has a very difficult time discerning individual letters.**

Examples:

"Knight charlie 3" -> Nc3

"Delta four" -> d4

"Queen edge 7" -> Qe7

**The word 'to' will always be interpreted as '2'; phrases such as 'knight to delta four' will be interpreted as 'N2d4'.**

### Word Correction

You may come across a word that is frequently mistaken for another word by the recognition service. For example "rook" is almost always (in my experience) interpreted as "Brooke"*. The extension provides word correction to help provide a more consistent experience.

Pin the extension to your chrome toolbar and click the icon to open the word replacement popup menu. It will display the most recently heard word or phrase, text fields for the word to replace and what to replace it with, and a button that navigates to the options page. In the options page you may view your replaced-words list, search for words being replaced/ being substituted in, and delete entries. 

Non-English language users could also theoretically replace English piece names with piece names in their preferred language. For example, a Spanish-speaking player could tell the extension that any time it hears 'torre', to interpret it instead as 'rook'. 

Note that you can use any word you want to identify a piece (e.g. 'noon' for Knight, 'rock' for Rook, etc.) with ONE exception: Bishops. Any word that starts with 'b' other than 'bishop' will be interpreted as a pawn move. You must either say 'bishop', or use the word correction feature to replace your preferred word with 'bishop' specifically. 

*The extension comes preloaded with some problematic words already replaced, including "Brooke".

Technical stuff/why this is necessary: The Web Speech API, which is currently considered an 'experimental technology', is set up to use the SpeechGrammar interface. This interface represents a set of words or patterns of words that the recognition service should look for specifically. Unfortunately, the recognition service provided by Chrome currently ignores this list. See the 'Handling errors and unrecognized speech' section of this page: https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API/Using_the_Web_Speech_API 

More command examples, and words that are generally interpreted well, can be found here https://docs.google.com/spreadsheets/d/1g6cGDRYvjGPj2gqeEMUVYwbZG3xjz_SrX_2q9z0Tsxo/edit?usp=sharing

### Text Input Box submission

For Blitz or faster formats, or if you are unable to/uninterested in using an API token, you may use Lichess's text input box to submit moves. This requires you to press 'enter' to submit moves, and that you use SAN format moves.

1. On Lichess, enable text input by going to https://lichess.org/account/preferences/game-behavior and enabling "Input moves with the keyboard". Optional: to turn on move playback, enter a game and click on your name in the top right-> sound -> Speech.

2. Make sure the extension is listening for your input using the 'ctrl' key. You should see the message to the bottom right of the board change to "Listening...".

3. Dictate your move in SAN format. When you are finished, you should see the message near the input box display your move. Press enter to submit the displayed move to the input box, or dictate another move if the displayed move is incorrect.

### Additional Commands:
You may interact automatically with certain html elements on game pages using the following commands:

resign
offer draw
take back
accept
decline
abort
rematch
flip board
analyze game
new game
rage quit

### Install Guide:

--Chrome Web Store: https://chrome.google.com/webstore/detail/speak-to-lichess/ldiiocggpmgljihlkgpngjlhnggpapig

--From Github:

1. Download the latest release zip file from GitHub (usually somewhere on the right of the page), or clone the repository. 

2. Unzip the package; take note of where the resulting folder is located. 

3. Go to chrome://extensions 

4. Toggle on developer mode in the top right, then click 'load unpacked' on the top left; select the "Speech-to-Text-Lichess" folder that you extracted in step 2.

5. Done! You should see Speak to Lichess on your extension page. Make sure it is enabled.

6. At the top right of chrome, click the puzzle piece icon, and pin Speak to Lichess. This will let you use the pop up menu to specify words that the speech recognition software is mishearing and manage your list of replaced words. 

### Notes:

The Web Speech API: https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API

The Lichess Board API: https://lichess.org/blog/XlRW5REAAB8AUJJ-/welcome-lichess-boards, https://lichess.org/api#tag/Board 

Speak to Lichess is Open Source. Feedback welcome here on Github or sent to speak2lichess@gmail.com

### Other/Known issues:

Some users have reported very poor recognition results; this will have to do with the speech recognition software. Until the speech recognition provided by Chrome correctly uses the SpeechGrammar interface, this may be a persistent issue. The best advice I can give is to keep trying different words until you find a set that the software recognizes more consistently for you, and to make use of the word correction feature. 

Speech recognition does offer alternative results, which might be used in the future to help the extension more accurately interpret moves. 

I had plans to port this extension to Firefox, where I (somehow) got the impression that the SpeechGrammar interface would be correctly referenced as a vocabulary list. It turns out, unfortunatel, that Firefox does not support the Web Speech API's speech recognition at all!