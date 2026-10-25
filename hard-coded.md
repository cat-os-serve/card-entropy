# Pre-calculated entropy values
This is a list of how to extract common entropy values from common decks of cards.
They are extra `.md` files stored in `card-entropy/hard-coded/`, and are sorted by deck type, then by entropy
"class" (0-255 bits, and 256-1024 bits).

Examples are `card-entropy/hard-coded/52/255-.md` for 0-255 bits extracted from a single 52-deck of cards and
`card-entropy/hard-coded/54x2/256+.md` for 256-1024 bits extracted from two 54-decks of cards shuffled
together.

Pre-calculated values, and runtime-calculated values, are made using approximations of a worst-case, with a 10-bit buffer. The target entropy for calculations will be 10 bits above the requested entropy. This is to allow safe transferal between a large integer between, for example, 0 and 52!-1, into a proper binary string. Using a large factor of 1024 allows only a very small amount of outputs to be weighted differently. The actual entropy returner also adds a random string from `/dev/random`, as it moves the biased region randomly within the output space, though no practical attack is possible even without this addition.

The calculated entropy returned is also a worst-case of entropy returned. For two examples: when shuffling two decks into one, it assumes all selected cards, when shuffling less than all of the cards together to read out an output, are duplicated, as this is the scenario that removes the most entropy; and when shuffling a subset of a deck together, it assumes the cards in the subset are already known, allowing a user to simply take the top n cards and shuffle them.
