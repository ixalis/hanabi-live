List of Features
================

The server was originally an attempt to emulate the [Keldon Hanabi server](http://keldon.net/hanabi/) and was written in Node.js. Since then, it has been completely rewritten in Go.

<br />

## Major Features

#### Clue Indication

* The cards last touched by a clue are indicated by arrows.
* Yellow borders around a card signify that it has been "touched" by one or more clues.
* Color pips (that match the suits of the stack) and black boxes (that match the number possibilities) will appear on cards in a player's hand. The pips and boxes will automatically disappear as more information is learned about the card.
* You can left-click on someone else's card to see how it appears to them. (This is referred to as "empathy".)
* A clue log is also shown in the top-right-hand corner. When mousing over a card, the positive clues that have touched the card will turn white and the negative clues that have touched the card will turn red.
* As a helpful shortcut, you can click on a specific clue in the clue log to go to the exact turn when the clue was given.

#### Notes

* Players can right-click on any card to add a note to it. Afterward, by hovering over a card, a tooltip will appear with the written note.
* This is useful for storing contextual information about a card for later.
* Since notes are tracked by the server, players can switch computers mid-game and keep any notes written.
* Notes are saved in the database and will persist into the replay.
* Everyone's notes are combined and shown to spectators, which is fun to see.

#### Spectators

* All games have the ability to be spectated by other idle players.
* Spectators will see all of the hands.
* The list of current spectators can be seen by hovering over the "👀" icon in the bottom-right-hand corner.

#### In-Game Replay

* In the middle of a game, players can click on the arrow button in the bottom-left-hand corner to open the in-game replay feature.
* Using this feature, players can go back in time to see the exact game state at a specific turn.

#### Game History and Profiles

* After a game is completed, it will be recorded in the database.
* Players will be able to see all of their past games in the "Show History" screen.
* You can click on a player's name in the lobby to view their profile, which will show all of their past games and some extra statistics.

#### Replays

* Any past game can be viewed as a replay or a shared replay.
* Similar to an in-game replay, in a post-game replay, you can review the game turn by turn.

#### Shared Replays

* A shared replay is similar to a normal replay, but others can join to have a coordinated review session.
* At the end of each game, you will automatically be put into a shared replay with everyone who played the game.
* The leader controls what turn is being shown. By default, the leader will be the person who created the game or created the shared replay.
* The leader can right-click on a card to highlight it with a red arrow (to point out things to the other players).
* The leader can shift + left-click on a card to morph it into an arbitrary card.
* The current leader can be seen by hovering over the "👑" icon in the bottom right-hand corner.
* The leader role can be transfered by right-clicking on the crown.

<br />

## Custom Game Options

#### Variants

* The server implements several official and unofficial Hanabi variants, which are listed on [a separate page](https://github.com/Zamiell/hanabi-live/tree/master/docs/VARIANTS.md).

#### Timed Games

* Each game has the option to be created with as a "Timed Game".
* Similar to chess, each player has a bank of time that decreases only during their turn.
* By default, each player starts with 2 minutes and adds 20 seconds to their clock after performing each move.
* If time runs out for any player, the game immediately ends and a score of 0 will be given.
* In non-timed games, there is an option to show the timers anyway. They will count up instead of down to show how long each player is taking.

#### Bottom Deck Blind Plays

* Each game has the option to allow a special "house" rule.
* If enabled, when there is 1 card left in the deck, players are allowed to blind play it.
* This is done by dragging the deck on to the play area.
* A golden border will appear around the deck when there is 1 card left in order to signify that this is possible.
* This feature can prevent losses that occur from being "bottom decked" by a 3 or a 4 that was impossible to save in the early or mid-game.

#### Empty Clues

* By default, it is not possible to give an "empty" clue, which is a clue that touches 0 cards.
* Each game has the option to allow empty clues.
* More information on the history of empty clues can be found in the [Hyphen-ated conventions repository](https://github.com/Zamiell/hanabi-conventions/blob/master/other-conventions/Empty_Clues.md#history).

#### Detrimental Character Assignments

* Each game has the option to enable "Detrimental Character Assignments". When enabled, it will restrict players in additional ways beyond the normal rules.
* The characters are loosly based on [this post](https://boardgamegeek.com/thread/1688194/hanabi-characters-variant) from Sean McCarthy on the Board Game Geek forums.
* More information on the characters are listed on [a separate page](https://github.com/Zamiell/hanabi-live/tree/master/docs/CHARACTERS.md).

#### Password-Protected Games

* Each game has the option to be created with a password.
* This allows private tables to be created.
* Note that all passwords are [salted](https://en.wikipedia.org/wiki/Salt_(cryptography)) and [hashed](https://en.wikipedia.org/wiki/Cryptographic_hash_function) (with [SHA256](https://en.wikipedia.org/wiki/SHA-2)) before being sent to the server.

<br />

## Other Options

#### Color-Blind Mode

* Each player has the option to toggle a color-blind mode that will add a letter to each card that signifies which suit it is.

#### Efficiency Statistics

* Each player has the option to toggle efficiency statistics about the current game. They are shown at the bottom of the clue log.

#### Reverse Hand Direction

* Each player has the option to toggle a "reverse hand direction" option, in which the user interface will display the hand from right-to-left instead of from left-to-right.
* This is useful for players that are used to drawing cards from the right side instead of from the left.

<br />

## Sounds

* A sound is played each time a player takes an action.
* A different sound is played when it reaches your turn.
* There is a custom sound for a failed play.
* There is a custom sound for a blind play.
* There is a custom sound for multiple blind plays in a row (up to 4).
* There is a custom sound for discarding a critical card.

<br />

## Keyboard Shortcuts

* For the lobby:
  * Create a table: `Alt + c`
  * Show history: `Alt + h`
  * Start a game: `Alt + s`
  * Leave a table: `Alt + l`
  * Return to tables: `Alt + r`
* For in-game:
  * Play a card: `a` or `+` (will prompt an alert for the slot number)
  * Discard a card: `d` or `-` (will prompt an alert for the slot number)
  * Clue:
    * `Tab` to select a player
    * `1`, `2`, `3`, `4`, `5` for a number clue
    * Or `q`, `w`, `e`, `r`, `t` for a color clue
    * Then `Enter` to submit
* For in a replay:
  * Rewind back one turn: `Left`
  * Fast-forward one turn: `Right`
  * Rewind one full rotation: `[`
  * Fast-forward one full rotation: `]`
  * Go to the beginning: `Home`
  * Go to the end: `End`

<br />

## Similar Deals and Competitive Play

* Normally, when a game is started, the server will find a deal in the database (based on a seed) that none of the players have played before.
* If there were no old seeds that matched this criteria, the server will generate a new random deal.
* After the game is complete, you can see the other players who played the same deal by using the "Other Scores" button on the game history screen. You can even view the replay of their game to see how they played it.
* If two groups of Hanabi players want to compete against each other, then there are two ways to play a non-randomly generated deal:
  * Start a game with `!seed [seed]` to play a deal generated by that specific seed. For example: `!seed showmatch-jan-2050-game-1`
  * Start a game with `!deal [deal]` to play a deal specified by a text file. The text file must already be present on the server in the `specific-deals` directory. If necessary, you can contact an administrator to upload a new text file. For example: `!deal showmatch-jan-2050-game-1`

<br />

## Other Quality of Life Improvements (over Keldon's Server)

* The action log is improved:
  * It will show what slot a player played or discarded from.
  * It will show "(blind)" for blind plays.
  * It will shows "(clued)" when discarding clued cards.
  * It will show 3 actions instead of 1.
  * It will show how many cards were left in the deck at the start of each message. (This only occurs when you click the action log to see the full log.)
  * At the end of the game, in timed games, it will show how much time each player had left. In non-timed games, it will show how much time that the game took in total.
* The clue log will still continue to function if you mouse over played and discarded cards.
* The "No Clues" indicator is much easier to see.
* Replays of other games will no longer show "Alice", "Bob", etc., and will instead show the real player names. This way, if you have a question about what they did, you can message them and ask.
* Upon refreshing the page, if you are in the middle of the game, you will be automatically taken into that game from the lobby.
* You will no longer have to refresh the page after resizing the browser window.
* The "Clues" text on the game UI will be red while at 8 clues.
* Each suit name is listed below the stack in the middle of the screen during games with the multi-color variants.
* All lobby chat will be replicated to (and from) the Hanabi Discord server.
* The lobby has been completely rehauled:
  * The nice-looking user interface is [Alpha from HTML5UP](https://html5up.net/alpha).
  * The username box on the login box will now be automatically focused and you can press enter to login.
  * Your name will be bolded in the user list.
  * The ambiguous checkboxes in the lobby have been converted to a "Status" indicator, showing exactly what the person is doing.
* You can now view a replay (or share a replay) by ID number.
* When you create a game, the server will suggest a randomly generated table name for you.
* Idle games and idle shared replays will automatically be ended by the server after 30 minutes.

<br />
