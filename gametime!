# Game-of-Pig
Can you beat the computer? 

import java.util.Scanner;
import java.util.Random;

public class Assignment1_16chra {
    public static void main(String[] args){
        System.out.println("Welcome to the game of Pig. \n" +
                "To roll again hit Y then enter for yes, or N then enter for no. \n" +
                "I'll give you first turn, rookie: \n");
        int playerScore=0; 									//Initializing the Computer and Player scores
        int computerScore=0;
        while(true) { 										//i dont think alan would approve of while true but i thought this made sense
            playerScore += turn(playerScore, "you");		//player goes first, and turn returns the score for each turn, so it increments
            if(playerScore>99) { 							//if player wins, tell them and then break
                System.out.println("you win");
                break;
            }
            System.out.printf("\nscore at the end of your turn: %d \n\n", playerScore);//print total score at the end of player turn
            computerScore += turn(computerScore, "comp"); 			//same as player turn but pass in different user.
            if (computerScore>99) {
                System.out.println("comp wins");			//break and tell user if comp won
                break;
            }
            System.out.printf("\nscore at the end of computers turn: %d \n\n", computerScore);//display final scores
        }
    }

    public static int turn(int score, String user){				//method used by both comp and player for a turn
        int turnScore=0;									// initialize turn score to 0
        boolean rollAgain=true;								// parameter for the following loop, starts as true
        while (rollAgain) {
            int rollScore = roll(turnScore, user);			//start loop with calling method roll
            turnScore +=  rollScore;						//increment local turn score
            System.out.printf(user + " scored %d this roll \n", rollScore);//display roll score
            if (rollScore+score>=100) break; 				//check if user won
            if (rollScore == 0) {							//if roll returns 0, ie rolled one 1, reset turn score and break loop, ending turn
                turnScore=0;
                break;
            }
            System.out.printf(user + " current score is %d \n", turnScore+score);
            if (turnScore+score>=100) break;				//check if user won again
            if (rollScore == 25) rollAgain=true;			//auto roll again for double ones
            else if (user == "comp") rollAgain=compRollAgain(score, turnScore);//if its the comp rolling, consult the algorithm for rollagain
            else rollAgain= rollagain();					//otherwise it is the user, so consult the user rollagain method
        }
        return turnScore; 									//do i need to explain this?no
    }

    public static int roll(int turnScore, String user) {
        int roll1 = roll();
        int roll2 = roll();									// roll 2 different dice
        System.out.printf(user + " rolled: %d and %d \n", roll1, roll2);//display rolls
        if (roll1 == 1 && roll2 == 1) {			// returns 25 for snake eyes.
            return 25;
        } else if(roll1==1 || roll2==1) { 			//returns 0 if one of the dice is one
            return 0;
        } else if(roll1==roll2) { 					//returns double the sum of your dice
            return 4*roll1;
        } else { 									//returns any other circumstance
            return roll1+roll2;
        }
    }

    public static boolean rollagain() {
        boolean realAnswer=true;
        while (realAnswer) {								//Just in case user gives wrong input.
            Scanner screen = new Scanner(System.in);	    //might be redundant.
            System.out.print("Would you like to roll again? (Y or N)\n");
            char character = screen.next().charAt(0);		//Save the user input to character.
            if (character=='y')return true;				//If Y, then roll again.
            else if (character=='n')return false;			//If N, then dont roll again.
            int rand = new Random().nextInt()%5;				//Need random number for switch case.
            switch (rand) {
                case 0: System.out.printf("Excuse me, lets try this one more time.\n");
                    break;
                case 1:	System.out.printf("SEEEERRRIOUSLY\n");
                    break;
                default: System.out.printf("One more time, I dare you. \n");
                    break;
            } // Games are supposed to be fun right? haha


        }
        return false;
    }

    public static boolean compRollAgain(int score, int turnScore) {//computer algorithm, uncommented because it is a secret
        if (turnScore+score>90) return true;	//lol
        if (turnScore>20) {
            System.out.println("comp decided to end turn");
            return false;
            }
        else return true;
    }

    public static int roll() {					//Working with a friend, we found this works perfectly fine for the random number.
        Random rand = new Random();				//Get long random number.
        int num2 = rand.nextInt();				//Cast long to int.
        return Math.abs(num2%6)+1;				//Convert random number to number between 1 and 6.
    }


}
