from random import shuffle

# The first is a list of all possible card ranks: 2-10, Jack, King, Queen, Ace
# The second is a list of all posible card suits: Hearts, Diamonds, Clubs, Spades
ranks = ["2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K", "A"]
suits = ["H", "D", "C", "S"]

# This class represents an individual playing card
class Card():#DONE
    def __init__(self, suit, rank):
        self.suit = suit
        self.rank = rank

    # This function creates a string out of a Card for easy printing.
    def __str__(self):
        return "[" + self.suit + ", " + self.rank + "]"

# This class represents a deck of playing cards
class Deck(): #DONE
    def __init__(self):#That is, for each suit there should be a Card of each rank added to the cards list in the Deck class.
        cards = []
        for x in range(len(suits)):#x represents the current suit
            for a in range(len(ranks)):#a represents the current rank
                cards.append(Card(suits[x],ranks[a]))
        self.cards = cards
        
    # This function will shuffle the deck, randomizing the order of the cards
    # inside the deck.
    # It takes an integer argument, which determine how many times the deck is
    # shuffled.
    def shuffle_deck(self, n = 5):
        for i in range(n):
            shuffle(self.cards)

    # This function will deal a card from the deck. The card should be removed
    # from the deck and added to the player's hand.
    def deal_card(self, player):
        player.hand.append(self.cards.pop(len(self.cards)-1))

    # This function constructs a string out of a Deck for easy printing.
    def __str__(self):
        res = "[" + str(self.cards[0])
        for i in range(1, len(self.cards)):
            res += ", " + str(self.cards[i])
        res += "]"
        return res

# This class represents a player in a game of Blackjack
class Player():#DONE
    def __init__(self, name):#When you construct a Player object, you should set the Player's name to the string passed in as an argument, the hand attribute should be set to an empty list, and the status attribute should be set to True.
        self.name = name
        self.hand = []
        self.status = True

    def value(self):
        total = 0
        for x in self.hand:#x is a Card object
            if(x.rank=="Q" or x.rank=="J" or x.rank=="K"):
                total+=10
            elif (x.rank=="A" and total>10):
                total+=1
            elif (x.rank=="A"):
                total+=11
            elif (x.rank=="2"):
                total+=2
            elif(x.rank=="3"):
                total+=3
            elif(x.rank=="4"):
                total+=4
            elif(x.rank=="5"):
                total+=5
            elif(x.rank=="6"):
                total+=6
            elif(x.rank=="7"):
                total+=7
            elif(x.rank=="8"):
                total+=8
            elif(x.rank=="9"):
                total+=9
            elif(x.rank=="10"):
                total+=10
        return total


    def choose_play(self):
        if(self.value()<17):
            return "Hit"
        else:
            self.status = False
            return "Stay"

    # This function creates a string representing a player for easy printing.
    def __str__(self):
        res = "Player: " + self.name + "\n"
        res += "\tHand: " + str(self.hand[0])
        for i in range(1, len(self.hand)):
            res += ", " + str(self.hand[i])
        res += "\n"
        res += "\tValue: " + str(self.value())
        return res

# This class represents a game of Blackjack
class Blackjack():
    def __init__(self, players):
        self.players = players
        self.deck = Deck()
        self.deck.shuffle_deck(5)
        for x in players:
            self.deck.deal_card(x)
            self.deck.deal_card(x)

    def play_game(self):
        weplaying = True
        while(weplaying):
            fcount=0
            for x in self.players:#This loop is checking to see what the status is for all the players.
                if(x.status==False):
                    fcount+=1
                if(len(self.players)==fcount):
                    weplaying = False
            if(weplaying==False):
                break#Will stop the game if all the players have status of false
            #Now game simulation activities below
            for cplayer in self.players:
                if(cplayer.choose_play()=="Stay"):
                    continue
                elif(cplayer.choose_play()=="Hit"):
                    self.deck.deal_card(cplayer)
                    if(cplayer.value()>21):
                        print(cplayer.name + " has busted.")
                        cplayer.status = False
        #Now will determine who the winner is, or tie, or all busts
        scores = []
        for person in self.players:#adding values to the score list. Will not include if any player has score over 21
            if(person.value()<=21):
                scores.append(person.value())
        if(len(scores)==0):
            print ("There is no winner. All players busted.")
            return
        cwin = 0 # index of the current maximum player
        #for person in range(len(scores)):#person is index of scores
            #if (person==0):#
                #continue
            #elif (scores[person]>scores[cwin]):
            #    cwin = person
            #elif (scores[person]==scores[cwin]):#Current Issue is that can have two people with same score, but less than the maximum person which occurs later
                #if(max(scores)==scores[person]):
                    #print ("No winner. There has been a tie")
                #return
        biggest = max(scores)
        bcount = 0
        for playa in scores:#checking to see if there has been a tie for winning.
            if(biggest==playa):
                bcount+=1
            if(bcount>1):
                print("No winner. There has been a tie.")
                return

        for x in self.players:
            #print(cwin)
            #if(scores[cwin]==x.value()):
                #print ("The winner is " + x.name + ". Congratulations!")
            if(x.value()==biggest):
                print ("The winner is " + x.name +". Congratulations!")


    # This function creates a string representing the state of a Blackjack game
    # for easy printing.
    def __str__(self):
        res = "Current Deck:\n\t" + str(self.deck)
        res = "\n"
        for p in self.players:
            res += str(p)
            res += "\n"
        return res

if __name__ == "__main__":
    # Uncomment each section of test code as you finish implementing each class
    # for this problem. Uncomment means remove the '#' at the front of the line
    # of code.
    
    # Test Code for your Card class
    #c1 = Card("H", "10")
    #c2 = Card("C", "A")
    #c3 = Card("D", "7")

    #print(c1)
    #print(c2)
    #print(c3)

    print()

    # Test Code for your Deck class
    #d1 = Deck()
    #d1.shuffle_deck(10)
    #print(d1)

    print()

    # Test Code for your Player class
    #p1 = Player("Alice")
    #p2 = Player("Bob")
    #d1.deal_card(p1)
    #d1.deal_card(p2)
    #print(p1.value())
    #print(p2.value())
    #d1.deal_card(p1)
    #d1.deal_card(p2)
    #print(p1.value())
    #print(p2.value())
    #d1.deal_card(p1)
    #d1.deal_card(p2)
    #print(p1.value())
    #print(p2.value())
    #print(p1)
    #print(p2)
    #print(p1.choose_play())
    #print(p2.choose_play())

    print()

    # Test Code for your Blackjack class
    players = [Player("Summer"), Player("Rick"), Player("Morty"), Player("Jerry")]
    game = Blackjack(players)
    print(game)
    game.play_game()
    print(game)
