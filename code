# american_football_cosc1336
# Command line football game created back in July 2019 as a project for my first programming class

#**********************************************************************
# Program: American Football
# Description: 
# 	This program is a videogame of American football for two players.
#       Each player enters a team name then a coin toss is initiated to
#       decide which player gets the ball first. Each player gets two
#       offensive turns in each quarter w/ options to throw or pass the ball.
#       Player can kick on fourth down or make another play.
#       If player gains 100 yards to score a touchdown, they can choose
#       to kick or try a two-point conversion before the ball turns over to
#       the other team.
#
# Author: Allison Crenshaw
# Date: 07/10/19
# Revised: 
# 	07/29/19
#       07/30/19
#       07/31/19
#
# list libraries used
import random
#
# Declare global constants (name in ALL_CAPS)
#    no global constants for this program





#**********************************************************************
# 
#**********************************************************************
# Function main()
# Description:
#       As long as the player wants to play, the program will:
#       1)Ask players for two team names
#       2)Call the coinToss() function to decide who gets ball first
#       3)Display which team gets ball first
#       4)Call the Game() function w/ team names as parameters
#       5)Display the winner
#       6)Ask if user wants to play again
# Calls:
#       coinToss()  1x
#	Game()      1x
#
# Parameters:
#       player1     string
#       player2     string
# Returns:
#	none

def main():

    # Declare and INITIALZE Local Variables (NOT parameters)
    again = ''

    # game welcome screen
    print("Welcome to the Big Game!")

    # start while loop
    again = 'y'

    # start while
    while again == 'y':

        # input for team names
        print("Please enter two team names.\n")
        entry1 = input("Enter your first team name: ")
        entry2 = input("Enter your second team name: ")

        # display team names
        print("\nAlright, we have the", entry1, "versus the", entry2, "! It's gonna be a good game!")
        input("Press enter to continue.")
        print("\nNow, let's see who will go first...")

        # call coinToss()
        print("Heads,", entry1, "will get the ball first.")
        print("Tails,", entry2, "will get the ball first.")
        input("\nPress enter to toss the coin.")
        print("\n***initiating coin toss***\n")
        heads_or_tails = coinToss()

        # start if
        if heads_or_tails == 1:
            print("Heads!", entry1, "will go first.")
            player1 = entry1
            player2 = entry2
        elif heads_or_tails == 2:
            print("Tails!", entry2, "will go first.")
            player1 = entry2
            player2 = entry1
        # end if
        
        # call Game() and print winner
        winner = Game(player1, player2)
        print("\nAnd the winner is...", winner,"!")
        print("Would you like to play again?")
        again = input("Enter y for yes or enter any other character to quit: ")

        # start if
        if again == 'y':
            pass
        else:
            print("Thanks for playing!")
            quit()
        # end if
        
    #end while

# End Function main()

#**********************************************************************
# 
#**********************************************************************
# Function coinToss()
# Description:
#	Chooses a random number between 1 and 2 and returns the value.
#       1 will mean heads in the main() program, 2 will mean tails.
# Calls:
#	none
# Parameters:
#       none
# Returns:
#	result

def coinToss():

    # Declare and INITIALZE Local Variables (NOT parameters)
    result = ''

    # calculate random number
    result = random.randint(1,2)

    # Return the return variable, if any
    return result

# End Function coinToss()

#**********************************************************************
# 
#**********************************************************************
# Function Game()
# Description:
#	Plays a game with 4 quarters:
#       1)Calls the Quarter() function 4 times
#       2)Keeps total scores by adding in scores from each Quarter()
#       3)After 4 quarters, compares scores and returns a winner
#       
# Calls:
#	Quarter()   4x
# Parameters:
#       player1     string
#       player2     string
# Returns:
#	none

def Game(player1, player2):

    # Declare and INITIALZE Local Variables (NOT parameters)
    quarter = 0
    total_score1 = 0
    total_score2 = 0
    quarter_scores = [] #index 0 for player1, index 1 for player2
    winner = ''
    
    # start for loop
    for quarters in range (4):
        #call Quarter() function 4x
        quarter = quarter + 1
        print("\nStarting Quarter", quarter,", let's play some football!\n")
        quarter_scores = Quarter(player1, player2)
        print("Wow, what a quarter!")

        #add quarter scores to total scores
        total_score1 = total_score1 + quarter_scores[0]
        total_score2 = total_score2 + quarter_scores[1]
        print("\nScoreboard:")
        print(player1, ":", total_score1)
        print(player2, ":", total_score2)

        # player can initiate next quarter
        print("\nOh, looks like the next quarter is about to start up.")
        input("Press enter to continue.")
        
    # end for loop
        
    # start if
    if (total_score1 > total_score2):
        winner = player1
    elif (total_score2 > total_score1):
        winner = player2
    else:
        winner = "It's a tie"
    #end if

    # Return the return variable, if any
    return winner
        
# End Function Game()

#**********************************************************************
# 
#**********************************************************************
# Function Quarter()
# Description:
#	This function runs one quarter of the football game:
#           1)Calls the Turn() function 2x, allowing each team 1 offensive turn
#           2)Totals up each team's score for the quarter
#           3)Returns each team's quarter score to the Game() function inside of a list
# Calls:
#	Turn()
# Parameters:
#       player1     string
#       player2     string
# Returns:
#	quarter_scores  list

def Quarter(player1, player2):

    # Declare and INITIALZE Local Variables (NOT parameters)
    player1_score = 0
    player2_score = 0
    quarter_scores = []

    # call Turn() 2x total, once for each player.
    player1_score = Turn(player1)
    player2_score = Turn(player2)

    # create a total score for the quarter & display for user
    print(player1, "scored", player1_score, "points this quarter.")
    print(player2, "scored", player2_score, "points this quarter.")
    
    # append scores to a list quarter_scores to be returned to Game()
    quarter_scores.append(player1_score)
    quarter_scores.append(player2_score)
    return quarter_scores

# End Function Quarter()

#**********************************************************************
# 
#**********************************************************************
# Function Turn()
# Description:
#	This function gives a team their turn with the ball to run offense
#           1)Keeps track of down#, yards gained since 1st down, & total yards gained on field
#           2)While down is 4 or less and no touchdown scored, team can:
#               a)Pass()
#               b)Run()
#               c)Kick()
#           3)Pass() and Run() return yards gained which can reset down to 1 OR
#             if team chooses to kick, Kick() will return points scored (if any)
#           4)Yards gained added to yards since 1st down & total yards gained on field
#           5)Steps 2-4 repeat until team scores a touchdown or does not make 1st down
#           6)If touchdown is scored, Touchdown() is called, points are returned OR
#             if down reaches 5 and no touchdown, 0 points are returned
# Calls:
#	Pass()
#	Run()
#       Kick()
#       Touchdown()
# Parameters:
#       player      string
# Returns:
#	points

def Turn(player):

    # Declare and INITIALZE Local Variables (NOT parameters)
    valid = False
    choice = 0
    down = 1
    gain = 0
    first_down = 0
    field_position = 0
    points = 0
    

    # ask team for their play and call corresponding function
    # with while loop for data validation
    print(player,", it's your ball.")
    
    # start while
    while valid == False:

        # start while
        while down < 5:
            print("")
            print("You are currently at yard", field_position, "on down #", down, ".")
            print("What play do you want to run?")
            print("1 = Pass the Ball")
            print("2 = Run the Ball")
            print("3 = Kick a Field Goal")
            print("4 = Quit")

            # start try
            try:
                choice = int(input("\nEnter your choice: "))
            except ValueError:
                print("You have entered an invalid input. Please enter a 1, 2, 3, or 4.")
            else:
                # start if
                if choice == 1:
                    valid = True
                    gain = Pass()
                    first_down += gain
                    field_position += gain

                    # start if
                    if field_position >= 100:
                        points = Touchdown(player, field_position)
                        down = 5
                    elif (field_position < 100) and (first_down < 10):
                        down += 1
                    elif (field_position < 100) and (first_down >= 10):
                        down = 1
                        first_down = 0
                    else:
                        pass
                    # end if
                        
                    
                elif choice == 2:
                    valid = True
                    gain = Run()
                    first_down += gain
                    field_position += gain

                    # start if
                    if field_position >= 100:
                        points = Touchdown(player, field_position)
                        down = 5
                    elif (field_position < 100) and (first_down < 10):
                        down += 1
                    elif (field_position < 100) and (first_down >= 10):
                        down = 1
                        first_down = 0
                    else:
                        pass
                    # end if
                        
                    
                elif choice == 3:
                    valid = True
                    points = Kick(field_position)
                    down = 5
                    
                elif choice == 4:
                    quit()
                    
                else:
                    valid = False
                    print("Error: you have entered a number other than 1, 2, 3, or 4.")
                    print("Please enter a valid option.")
                    pass
                # end if
            # end try

    # start if
    if down == 5:
        print("\nAlright, let's turn the ball over to the other team.")
    else:
        pass
    # end if

    # Return the return variable, if any
    return points

# End Function Turn()

#**********************************************************************
# 
#**********************************************************************
# Function Touchdown()
# Description:
#	The touchdown function let's the player choose to kick or
#       do a two-point conversion
#           1)Calls kick or two-point conversion
#           2)Adds extra points from kick or conversion to
#             6 points for the touchdown
#           3)Returns total points
# Calls:
#	Kick()
#	Conversion()
# Parameters:
#       player              string
#       field_position      int
# Returns:
#	points

def Touchdown(player, field_position):

    # Declare and INITIALZE Local Variables (NOT parameters)
    extra_points = 0
    points = 0
    valid = False
    choice = 0

    # present options and take input for extra points
    print("")
    print("**********************************")
    print("Touchdown,", player, "! +6 points")
    print("**********************************")
    print("")
    print("Time to go for some extra points.")
    print("Do you want to try to kick a field goal")
    print("or run a two-point conversion?")
    print("1 = Kick a Field Goal")
    print("2 = Two-point Conversion")
    print("3 = Quit")

    valid = False

    # start while
    while valid == False:

        # start try
        try:
            choice = int(input("\nEnter your choice: "))
        except ValueError:
            print("You have entered an invalid input. Please enter a 1, 2, or 3.")
        else:
            # start if
            if choice == 1:
                valid = True
                extra_points = Kick(field_position)
                
            elif choice == 2:
                valid = True
                extra_points = Conversion()
                
            elif choice == 3:
                valid = True
                quit()
                
            else:
                valid = False
                print("Error: you have entered a number other than 1, 2, 3, or 4.")
                print("Please enter a valid option.")
                pass
            # end if
            
        # end try
        
    # end while

    # combine touchdown points w/ points from kick or conversion
    points = (6 + (extra_points))
                  
    # Return the return variable, if any
    return points

# End Function Touchdown()

#**********************************************************************
# 
#**********************************************************************
# Function Kick()
# Description:
#	Produces a random number between 1 and 100. If random number
#       is < the field_position, team will gain a point.
#       Else, 0 points returned.
# Calls:
#	none
# Parameters:
#       field_position
# Returns:
#	points

def Kick(field_position):

    # Declare and INITIALZE Local Variables (NOT parameters)
    points = 0
    kick = 0

    # generate random number
    kick = random.randint(0, 100)

    # start if
    if kick < field_position:
        points = 1
        print("")
        print("**********************************")
        print("What a kick! +1 point")
        print("**********************************")
        print("")
    else:
        points = 0
        print("Ah, what a shame. Always hate to see a team miss a field goal.")
    # end if
    
    # Return the return variable, if any
    return points

# End Function Kick()

#**********************************************************************
# 
#**********************************************************************
# Function Conversion()
# Description:
#	Produces a random number between 1 and 100. If random number
#       is < 50, team will gain 2 points. Else, 0 points.
# Calls:
#	none
# Parameters:
#       none
# Returns:
#	points

def Conversion():

    # Declare and INITIALZE Local Variables (NOT parameters)
    points = 0
    attempt = 0

    # generate random number
    attempt = random.randint(0, 100)

    # start if
    if attempt < 50:
        points = 2
        print("")
        print("**********************************")
        print("Successful conversion! +2 points")
        print("**********************************")
        print("")
    else:
        points = 0
        print("Well, an unsuccessful conversion attempt.")
        print("Can't blame them for taking the risk on those extra points.")
    # end if

    # Return the return variable, if any
    return points

# End Function Conversion()

#**********************************************************************
# 
#**********************************************************************
# Function Pass()
# Description:
#	Produces a random number between 1 and 100 to determine if play
#       is successful. Then produces second random number in a smaller range
#       to determine how many yards gained. Low percentage opportunity for bonus yards.
# Calls:
#	none
# Parameters:
#       none
# Returns:
#	yards

def Pass():

    # Declare and INITIALZE Local Variables (NOT parameters)
    attempt = 0
    yards = 0

    # generate random number
    attempt = random.randint(0, 100)

    # start if
    if attempt < 45:
        yards = random.randint(5, 30)
        print("A successful pass!")
    else:
        yards = 0
        print("Looks like someone's got butterfigners. An unsuccessful pass.")
    # end if

        
    # start if
    if attempt < 20:
        yards = yards + 15
        print("A huge gain for this team!")
    else:
        pass
    # end if
    

    # Return the return variable, if any
    return yards

# End Function Pass()

#**********************************************************************
# 
#**********************************************************************
# Function Run()
# Description:
#	Produces a random number between 1 and 100 to determine if play
#       is successful. Then produces second random number in a smaller range
#       to determine how many yards gained. Low percentage opportunity for bonus yards.
# Calls:
#	none
# Parameters:
#       none
# Returns:
#	yards

def Run():

    # Declare and INITIALZE Local Variables (NOT parameters)
    attempt = 0
    yards = 0

    # generate random number
    attempt = random.randint(0, 100)

    # start if
    if attempt < 65:
        yards = random.randint(5, 15)
        print("A successful rush. Good choice in plays.")
    else:
        yards = 0
        print("Oof, and the QB is sacked. Hate to see them take a hit like that.")
    # end if

    # start if
    if attempt < 10:
        yards = yards + 35
        print("Look at him go!")
    # end if

    
    # Return the return variable, if any
    return yards

# End Function Run()

# end Program

main()
