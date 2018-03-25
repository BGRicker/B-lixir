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

for suit <- suits do
    suit
end

for all the elements in suits array, do this (suit). Assign each element in suits to the word |suit| Everything in do block gets returned into a new array like a map

Enum.split splits array into tuples. {first_array, second_arary}
each array has a special meaning, like cards you're dealt and cards you're not dealt.

Cards.deal(deck, 5) #=> { hand: [], deck: [] }

"pattern matching is Elixir's replacement for variable assignment"
    - { hand, rest_of_deck } = Cards.deal(deck, 5)
    - assign this tuple to the result on the right, which returns a tuple
    - color = ["red"] # matches list, entire list assigned to color
    - [ color ] = ["red"] # now color matches "red" string inside array
    - [color1, color2] = ["red", "blue"]
    - [color1, color2, color3] = ["red", "blue"] #=> no match on right hand side

we write elixir, gets transpiled into Erlang, gets compiled and executed on BEAM

:erlang.term_to_binary(deck) #=> :erlang calls erlang code

case in elixir is a mix of if statements and pattern matching

error handling with case statement:

  def load(filename) do
    {status, binary} = File.read(filename)

    case status do
      :ok -> :erlang.binary_to_term binary
      :error -> "That file doesn't exist"
    end
  end