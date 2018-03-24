card application

- create a deck
- shuffle the deck
- deal a hand of cards
- check to see if a hand contains a specific card
- save a hand of cards to file system
- load a hand of cards from a file system

Mix command

    - creates projects, compiles projects, runs tasks, manages dependencies
    - `mix new cards` creates a new application called cards

application directory:

    - lib/cards.exe - creates module, collection of methods/functions

method structure:

def hello do
  "hi there"
end

- ruby but with `do`, implicit return

elixir's irb
    iex -S mix

`recompile` to reload! iex


```def create_deck do
  ["Ace", "Two", "Three"]
end```

OO Approach
- methods like shuffle, save, load would work on local instance variable of Deck
- operate on own local instance variable @cards

deck = Deck.new
deck.cards #=> [Card1, Card2, Card3]
deck.shuffle #=> [Card2, Card1, Card3]
deck.deal #=> Deck[Card1]

# deck class has a local collection of cards
# calling a method operates on local collection

FP Approach
no concept of class or instance of class, no instance variable
no this.cards, this.deck
Cards module is its own thing, no copies
create_deck returns an array of strings
shuffling, pass in array of strings, return shuffled array of strings
save function takes string and saves string with path to saved file
load takes path to saved file, reads string, outputs string