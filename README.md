# GuessingGame-code
it my first project in java 
import java.util.Random;
import java.util.Scanner;

public class GuessingGame {

     Loading animation
    static void loadingEffect() {
        System.out.print("\nLoading");
        for(int i = 0; i < 5; i++) {
            try {
                Thread.sleep(400);8
                System.out.print(".");
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        System.out.println("\n");
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        Random rand = new Random();

        System.out.println("🎮 Welcome to the Number Guessing Game!");
        System.out.println("Choose Difficulty Level:");
        System.out.println("1. Easy (10 attempts)");
        System.out.println("2. Medium (7 attempts)");
        System.out.println("3. Hard (5 attempts)");
        System.out.print("Enter your choice: ");

        int choice = sc.nextInt();
        int attempts = 5;

        if (choice == 1) attempts = 10;
        else if (choice == 2) attempts = 7;
        else attempts = 5;

        int secretNumber = rand.nextInt(50) + 1; // 1–50
        loadingEffect();

        System.out.println("Guess the number between 1 to 50!");

        while (attempts > 0) {

            System.out.println("\n Remaining attempts: " + attempts);
            System.out.print("Enter your guess: ");

            if (!sc.hasNextInt()) {
                System.out.println(" Invalid Input! Enter a number.\n");
                sc.next();
                continue;
            }

            int guess = sc.nextInt();

            if (guess < 1 || guess > 50) {
                System.out.println(" Enter only between 1 to 50!");
                continue;
            }

            if (guess == secretNumber) {
                System.out.println("\n YOU WIN! WELL PLAYED! ");
                System.out.println(" Correct Number: " + secretNumber);
                System.out.println(" You guessed it in style! ");
                break;
            } 
            else if (guess < secretNumber) {
                System.out.println(" Too Low! Try a bigger number!");
            } 
            else {
                System.out.println(" Too High! Try a smaller number!");
            }

            attempts--;
        }

        if (attempts == 0) {
            System.out.println("\n GAME OVER ");
            System.out.println("The correct number was: " + secretNumber);
            System.out.println("Better luck next time! ");
        }

        System.out.println("\n💖 Thanks for playing! Come back again!");
        sc.close();
    }
}

