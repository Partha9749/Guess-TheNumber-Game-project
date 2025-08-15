import java.util.Random;
import java.util.Scanner;

public class GuessTheNumberGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int totalScore = 0;
        int maxRounds = 3;
        int maxAttempts = 5;

        System.out.println("🎮 Welcome to the 'Guess the Number' Game!");
        System.out.println("You have " + maxRounds + " rounds to play. Good luck!\n");

        for (int round = 1; round <= maxRounds; round++) {
            int numberToGuess = random.nextInt(100) + 1;  // Random number between 1 to 100
            int attemptsLeft = maxAttempts;
            boolean guessedCorrectly = false;

            System.out.println("Round " + round + " of " + maxRounds);
            System.out.println("Guess a number between 1 and 100. You have " + maxAttempts + " attempts.");

            while (attemptsLeft > 0) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();
                attemptsLeft--;

                if (userGuess == numberToGuess) {
                    int scoreThisRound = attemptsLeft + 1; // More attempts left = higher score
                    totalScore += scoreThisRound;
                    System.out.println("Correct! You guessed the number!");
                    System.out.println("You scored " + scoreThisRound + " points this round.\n");
                    guessedCorrectly = true;
                    break;
                } else if (userGuess < numberToGuess) {
                    System.out.println("Too low! Attempts left: " + attemptsLeft);
                } else {
                    System.out.println("Too high! Attempts left: " + attemptsLeft);
                }
            }

            if (!guessedCorrectly) {
                System.out.println("You've used all attempts. The number was: " + numberToGuess + "\n");
            }
        }

        System.out.println("Game Over! Your total score is: " + totalScore);
        System.out.println("Hope you are enjoy this game. Thanks for playing!");
        scanner.close();
    }
}
