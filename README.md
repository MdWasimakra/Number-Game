# Number-Game

import java.util.Scanner;
import java.util.Random;

class RangeGenerator {
    public int generate(int max, int min) {
        Random random = new Random();
        return random.nextInt(max - min + 1) + min;
    }
}

public class numbergame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        RangeGenerator rangeGenerator = new RangeGenerator();
        int totalAttempts = 0;
        int win = 0;

        while (true) {
            System.out.println("Enter the maximum number: ");
            int max = scanner.nextInt();
            System.out.println("Enter the minimum number: ");
            int min = scanner.nextInt();
            scanner.nextLine(); 

            int targetNumber = rangeGenerator.generate(max, min);
            int attempts = 0;

            while (true) {
                System.out.println("Guess a number between " + min + " and " + max + ": ");
                int guessedNumber = scanner.nextInt();
                attempts++;

                if (guessedNumber > targetNumber) {
                    System.out.println("It's Greater");

                } else if (guessedNumber < targetNumber) {
                    System.out.println("It's Lesser");

                } else {
                    System.out.println("Correct Guess");
                    win++;
                    break;
                }
            }

            totalAttempts += attempts;
            System.out.println("Attempts: " + attempts);
            System.out.println("Win: " + win);

            double winRate = (double) win / totalAttempts * 100;
            System.out.printf("Your win rate is %.2f%%\n", winRate);
            System.out.print("Do you want to play again (yes/no): ");
            String playAgain = scanner.next();

            if (!playAgain.equalsIgnoreCase("yes")) {
                scanner.close();
                System.exit(0);
            }
            scanner.nextLine(); 
        }
    }
}

