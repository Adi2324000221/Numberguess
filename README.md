import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int rounds = 1;
        int totalScore = 0;
        boolean playAgain = true;

        System.out.println("Welcome to the Number Guessing Game!");

        while (playAgain) {
            System.out.println("\nRound " + rounds + ":");
            int number = random.nextInt(100) + 1; // Random number between 1 and 100
            int attempts = 0;
            int maxAttempts = 10;
            boolean guessedCorrectly = false;

            while (attempts < maxAttempts) {
                System.out.print("Attempt " + (attempts + 1) + "/" + maxAttempts + ": Enter your guess (1-100): ");
                int guess = scanner.nextInt();
                attempts++;

                if (guess < number) {
                    System.out.println("Too low!");
                } else if (guess > number) {
                    System.out.println("Too high!");
                } else {
                    System.out.println("Congratulations! You guessed the correct number in " + attempts + " attempts.");
                    totalScore += maxAttempts - attempts + 1;
                    guessedCorrectly = true;
                    break;
                }
            }

            if (!guessedCorrectly) {
                System.out.println("Sorry, you've used all " + maxAttempts + " attempts. The correct number was " + number + ".");
            }

            System.out.print("Do you want to play another round? (yes/no): ");
            String response = scanner.next().toLowerCase();

            if (!response.equals("yes")) {
                playAgain = false;
            } else {
                rounds++;
            }
        }

        System.out.println("\nGame Over! You played " + rounds + " round(s) with a total score of " + totalScore + ".");
        scanner.close();
    }
}
