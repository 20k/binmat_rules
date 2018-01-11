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
- [Win Conditions](#win-conditions)

## The Binmat Deck

6 suits, 78 cards, 13 cards per suit, one deck for the whole game. Not two decks

\& - FORM

\% - KIN

\+ - DATA

\! - CHAOS

\^ - VOID

\# - CHOICE

Cards in a suit go from 2-10, as well as:

\@ - TRAP

\* - WILD

\? - BOUNCE

\> - BREAK

These cards are known as 'modifiers'.

## Game Setup

One player is attacker, one is defender

6 parallel lanes between attacker and defender, completely independent


Deal thirteen face up cards in a deck at the defender's end of the right three lanes.
Deal thirteen face down cards in a deck at the defender's end of the left three lanes.

These decks are referred to as 'lane decks'.

Enough space for another deck should be left behind (defender's perspective) the decks in each lane, as this is the location of the 'lane discard pile'.


The attacker conceptually has two unique spaces, the ‘attacker deck’ and the ‘attacker discard pile’. Attempting to draw from an empty attacker deck shuffles in the attacker discard pile

If the competitive rules are being followed, the BINMAT app (explained in section 3) may now be placed equidistant from the attacker and defender at one side of the play area.

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

Not shown are the position of the attacker's discard pile, and 

## Game Structure

The game is composed of 110 turns (55 for the attacker, 55 for the defender).
Under competitive rules, each turn is 5 seconds long, but this can be ignored

If competitive rules are being used, the BINMAT app (available for iOS and Android) provides an effective timer and turn counter. If not, any method of counting down from 110 to 0 can be used.

The defender always takes the first turn.

## Gameplay

### Taking A Turn

On each of their turns, a player may perform one action or pass. The following actions are available to both attacker and defender:

#### Draw a card from a deck.
For a description of how to draw cards, see [Drawing A Card](#drawing-a-card)

#### Play a card from your hand to a lane's stack.
A card from your hand can be played into your 'stack' - in front of the lane deck for defenders, at your end of the lane for attackers. If an existing face-up stack is present here, cards played to it must also be face-up. The only modifier that can be played face up on a face-down stack is break

All face-up stacks can be inspected by any player at any time. You are also allowed to inspect your own face down cards

The third action is only available to the attacker, except with the use of the break modifier

#### Initiate combat in a lane.
For a description of combat, see [Combat](#combat)

### Drawing A Card
The defender can draw cards from any of the six lane decks.
The attacker can draw from only lane decks without a defender stack in front of them.
The attacker can also draw from a special 'attacker deck' which is at the side of the play area, in front of the attacker discard pile.

When a draw is attempted from an empty deck, the following ta##kes place:
The deck's corresponding discard pile is shuffled into the deck.
The draw can then take place as normal.

Any deck which has its discard pile shuffled into it is to be placed face down.
This includes lane decks which were previously face up.

### Combat

When combat is initiated in a lane, the cards in both attacker and defender stacks are revealed.
If a TRAP modifier is present, resolve its effect now.
If a BOUNCE modifier is present, resolve its effect now.
The number cards present in the stacks should have their sum calculated. Any present WILD modifiers should
be resolved now.
If the sum is not now a power of two, the stack has attack power zero. Otherwise, its attack power is the power of two to which the sum is equivalent.

If the attacker stack has a lower attack power, then the attacker stack goes to the lane's discard pile and the defender stack remains in its lane, face up.

If the attacker stack has an attack power equal to or greater than the defender stack, then the following takes place:

If a BREAK modifier was not played by the attacker this turn:

    Calculate the absolute difference between attack powers, and then add one to it. This is the damage value.

If a BREAK modifier was played by the attacker this turn:

    The damage value is the attack power of the attacker deck.

While the damage value is greater than zero:
	If there are cards left in the defender's stack, send the most recently played card there to the attacker discard pile.
	Else if there are not, but there are cards remaining in the lane's lane deck, send the top card from the lane deck to the attacker's hand.
	Else if there are no cards remaining in the lane deck either, the attacker has won the game. (section 5)
	Subtract one from the damage value.
 
The attacker stack is now sent to the attacker discard.

### Modifiers

\@ - TRAP
The TRAP modifier is played to your stack like a normal card.
When it is revealed (face-down to face-up) during combat, the most recently played card in the opposing stack is sent to the appropriate discard pile - defender TRAPs send cards to the lane discard pile, attacker TRAPs to the attacker discard pile.
If both stacks in combat reveal a TRAP, then the TRAP of the player who initiated combat is resolved first.

\? - BOUNCE
The BOUNCE modifier can be played face-down or face-up. (normal placing rules apply)
If a bounce card is played face up on a face up stack as a defender, nothing happens immediately, but bounce applies after the attacker attacks (or break is applied as the defender). A bounce card cannot be played face up on a face down stack. A bounce card only initiates combat if it is played face up by an attacker on an empty stack
When a bounce is involved in combat, it happens after any trap card. All damage is 0, and additionally:
The attacker stack is sent to the attacker discard pile.
The defender stack remains in its lane.
BOUNCE cards played are then sent to the opposite discard pile. (lane discard pile if attacker's, attacker discard pile if defender's). If the attacker and defender each have a bounce card, they go to each others discard piles

\* - WILD
The WILD modifier is played to your stack like a normal card.
During combat resolution, it brings the sum of its stack up to the next highest power of two.
If it is the only card in a stack, its value is 2 for the purposes of sum evaluation.
Multiple WILD cards keep increasing the power of two level

\> - BREAK
The BREAK modifier can be played face up or face down on a stack, but cannot be played on an empty stack. If a face down break is revealed by the other player, it servers as ‘trap fodder’. If an attacker initiates an attack with a break face down, the break applies
When the defender plays a BREAK, this modifier initiates standard combat in that lane.
When the attacker plays a BREAK, the modifier initiates combat in its lane with modified
combat resolution rules, as described in section 4c.
A BREAK cannot be played on a stack which already contains a BREAK.

## Win Conditions
- The game is won by the defender if all 110 turns have elapsed without the attacker achieving victory.
- The game can also be won by the defender if the attacker is unable to draw any cards from the lane decks, and has no cards in attacker stacks or in their hand.
- The game is won by the attacker if they deal more damage to a lane deck than the lane deck has cards. This is mentioned in combat resolution (see 4a.iii)
- The game is won by the attacker if a card is drawn from an empty lane deck with 0 cards, and there are also 0 cards in the lane’s discard pile
