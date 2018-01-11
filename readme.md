# Hackmud - Documentation

## Credits
Thx Alic

## Index

- [The Binmat Deck](#the-binmat-deck)
- [Game Setup](#game-setup)
- [Game Structure](#game-structure)
- [Gameplay](#gameplay)
- - [Taking A Turn](#taking-a-turn)
- - [Drawing A Card](#drawing-a-card)
- - [Combat](#combat)
- - [Modifiers](#modifiers)
- - - [TRAP](#---trap)
- - - [BOUNCE](#---bounce)
- - - [WILD](#---wild)
- - - [BREAK](#---break)
- [Win Conditions](#win-conditions)

## The Binmat Deck

6 suits, 78 cards, 13 cards per suit, one deck for the whole game. Not two decks

\& - FORM

\% - KIN

\+ - DATA

\! - CHAOS

\^ - VOID

\# - CHOICE

Cards in a suit go from 2-10, as well as the special cards:

\@ - TRAP

\* - WILD

\? - BOUNCE

\> - BREAK

These cards are known as 'modifiers'.

## Game Setup

One player is attacker, one is defender. These never change over the course of a game

6 parallel lanes are set up between attacker and defender. These are completely independent of one another

Where the lane decks go in the below diagram, deal thirteen face down cards in each space, then flip the top card on the 3 right hand decks face up. These 3 decks are the face up decks and always have the top card face up, even if they become empty and discard piles are shuffled in

These are altogether the lane decks. You are not allowed to inspect the face up lane decks

Enough space for another deck should be left behind (defender's perspective) the decks in each lane, as this is the location of the 'lane discard pile'.


The attacker conceptually has two unique spaces, the ‘attacker deck’ and the ‘attacker discard pile’. Attempting to draw from an empty attacker deck shuffles in the attacker discard pile

If the competitive rules are being followed, the BINMAT app may now be placed equidistant from the attacker and defender at one side of the play area.

The following is an ASCII representation of the play area at the conclusion of setup:

```
                                attacker sat here
								
                       _____ _____ _____ _____ _____ _____   
                      |     |     |     |     |     |     |
                      | ATK | ATK | ATK | ATK | ATK | ATK | - position of potential attacker stacks
                      |     |     |     |     |     |     |
            +----+    |_____|_____|_____|_____|_____|_____|
phone with  |    |    |     |     |     |     |     |     |
BINMAT app  |    |    | DEF | DEF | DEF | DEF | DEF | DEF | - position of potential defender stacks
            |    |    |     |     |     |     |     |     |
            |    |    |_____|_____|_____|_____|_____|_____|
(optional)  +----+    | +-+ | +-+ | +-+ | +-+ | +-+ | +-+ |
                      | |h| | |h| | |h| | |2| | |6| | |@| | - lane decks, 13 cards at the start in each
                      | +-+ | +-+ | +-+ | +-+ | +-+ | +-+ |
                      |_____|_____|_____|_____|_____|_____|
                      |     |     |     |     |     |     |
                      |     |     |     |     |     |     | - space for potential lane discard piles
                      |     |     |     |     |     |     |
                      |_____|_____|_____|_____|_____|_____|  
					   
                                defender sat here
```

Not shown are the position of the attacker's discard pile, and the attackers deck

## Game Structure

The game is composed of 110 turns (55 for the attacker, 55 for the defender).
Each turn is exactly 5 seconds long under competitive rules, but this can be ignored for casual play

If competitive rules are being used, the BINMAT app (available for iOS and Android) provides an effective timer and turn counter. If not, any method of counting down from 110 to 0 can be used.

The defender always takes the first turn.

## Gameplay

### Taking A Turn

On each of their turns, a player may perform one action or pass. The following actions are available either both players, the attacker, or the defender

#### Both - Draw a card from a deck.
For a description of how to draw cards, see [Drawing A Card](#drawing-a-card)

#### Both - Play a card from your hand to a lane's stack.
A card from your hand can be played into your 'stack' - in front of the lane deck for defenders, at your end of the lane for attackers. If an existing face-up stack is present here, cards played to it must also be face-up. The only modifier that can be played face up on a face-down stack is break

All face-up stacks can be inspected by any player at any time. You are also allowed to inspect your own face down cards. You cannot inspect discard piles

Defenders must play cards face down on an empty stack

#### Attacker only - Initiate combat in a lane.
For a description of combat, see [Combat](#combat)

An attacker cannot initiate combat with an empty stack

#### Defender only - Discard card one card to the discard pile in a lane as an action

### Drawing A Card
- The defender can draw cards from any of the six lane decks.

- The attacker can draw from only lane decks without a defender stack in front of them.

- The attacker can also draw from a special 'attacker deck' which is at the side of the play area, in front of the attacker discard pile.

When a draw is attempted from an empty deck, the following takes place:

- The deck's corresponding discard pile is shuffled into the deck.
- The draw then immediately takes place as normal.

Any deck which has its discard pile shuffled into it is to be placed face down, except the face up lane decks which still have their top card remain face up

### Combat

When combat is initiated in a lane, the cards in both attacker and defender stacks are revealed.

- If a TRAP modifier is present, resolve its effect now.

- If a BOUNCE modifier is present, resolve its effect now.

- The number cards present in the stacks should have their sum calculated. Any present WILD modifiers should be resolved now.

If the sum is not now a power of two, the stack has attack power zero. Otherwise, its attack power is the power of two to which the sum is equivalent.

- If the damage value of both stacks is 0-0, combat resolves as a bounce. 

If the attacker stack has a lower attack power, then the attacker stack goes to the lane's discard pile and the defender stack remains in its lane, face up.

If the attacker stack has an attack power equal to or greater than the defender stack, then the following takes place:

If a BREAK modifier was not played by the attacker this turn:

- The damage value is the absolute difference between attack powers, +1

If a BREAK modifier was played by the attacker this turn:

- The damage value is the attack power of the attacker deck.

While the damage value is greater than zero:
- If there are cards left in the defender's stack, send the most recently played card there to the attacker discard pile.
- Else if there are not, but there are cards remaining in the lane's lane deck, send the top card from the lane deck to the attacker's hand.
- Else if there are no cards remaining in the lane deck either, the attacker has won the game. ([Win Conditions](#win-conditions))
- Subtract one from the damage value.
 
The attacker stack is now sent to the attacker discard.

### Modifiers

### \@ - TRAP
- **Primary effect**: If a TRAP goes from face down to face up, the most recently played card on the opposite stack goes to the friendly discard pile (attacker discard if attacker, lane discard if defender)

- TRAP cards are played to your stack like a regular card

- If a TRAP is placed face up on a face up stack, it does nothing. It absorbs damage like a regular card

- If a TRAP goes from face down to face up, its primary effect is triggered

- When a TRAP is involved in combat, it has no special effect. Its effect triggers on face down to face up

- After a TRAP is revealed or used in combat, it acts as a normal card and is not removed (unless destroyed as per normal card rules)

- A TRAP acts before BOUNCE, and before BREAKS. It cannot cancel the combat initiation of a break, but it will cancel the damage modification

- In the event that both stacks reveal a TRAP, the player who initiated combat's TRAP activates first

### \? - BOUNCE

- **Primary effect**: When involved in combat, the attacker stack goes to the attacker discard pile, all defender cards remain in lane. All damage is 0. The BOUNCE goes to the opposite discard pile - an attacker bounce goes to lane discard, a defender's bounce goes to attacker discard

- BOUNCE cards are played to your stack like a regular card

- If a BOUNCE is played face up on a face up stack, it has no immediate effect. It triggers as normal if attacked by the attacker

- If a BOUNCE goes from face down to face up, it has no special effect

- When a BOUNCE is involved in combat, its primary effect is triggered

- After a BOUNCE is used in combat, it goes to the opposite discard pile

- A BOUNCE acts after TRAPS and BREAKS

- In the event that both stacks reveal a BOUNCE, each BOUNCE goes to the opposite discard pile

- A BOUNCE card can only initiate combat if it is played as a face up card on an empty stack as attacker. There are no other circumstances where it can initiate combat

### \* - WILD
- **Primary effect**: WILD cards bring the sum of the stack up to the next highest power of two. 7 goes to 8, or 8 goes to 16. Multiple WILDs stack

- WILD cards are played to your stack like a normal card.

- When a WILD is involved in combat, it brings the sum of its stack up to the next highest power of two

- If it is the only card in a stack, its value is 2 for the purposes of sum evaluation.

- Multiple WILD cards keep increasing the power of two level

- A WILD affects only damage calculation and can be affected by a TRAP

### \> - BREAK
- **Primary effect**: BREAK cards initate combat for attackers and defenders. After this, its secondary effect is invoked

- **Secondary effect**: If the attacker stack contains a BREAK, combat rules are modified. This does not occur if the attacker's BREAK is removed by a TRAP

- **Combat Modification**: BREAK damage rules trigger if the attacker has a surviving BREAK card in their stack: the damage value of the stack is the damage of the attacker stack, not the net + 1. Combat resolves normally otherweise

- BREAK cards are the only card that can be played face up on a face down stack. They can be additionally played face down on a face down stack. They cannot be played on an empty stack. A stack cannot contain two BREAKs, and you cannot play a BREAK on a stack that has a BREAK card in it

- If a BREAK is played face up on a face up or down stack, its primary effect triggers

- If a BREAK goes from face down to face up, it has no immediate special effect

- When a BREAK is involved in combat in the attacker's stack, its secondary effect is applied

- A BREAKs combat initiation applies immediately when played face up and acts before any other cards. Its secondary effect occurs after TRAP cards

## Win Conditions
- The game is won by the defender if all 110 turns have elapsed without the attacker achieving victory.
- The game can also be won by the defender if the attacker is unable to draw any cards from the lane decks, and has no cards in the attacker deck and in their hand, and attempts to draw. This condition is apparently made up
- The game is won by the attacker if they deal more damage to a lane deck than the lane deck has cards
- The game is won by the attacker if a card is drawn from an empty lane deck with 0 cards, and there are also 0 cards in the lane’s discard pile
