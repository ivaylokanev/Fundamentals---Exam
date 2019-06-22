
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;
import java.util.stream.Collectors;


public class Methods {


    public static void main( String[] args ) {
        Scanner scanner = new Scanner(System.in);


        int days = Integer.parseInt(scanner.nextLine());
        int players = Integer.parseInt(scanner.nextLine());
        double energy = Double.parseDouble(scanner.nextLine());
        double water = Double.parseDouble(scanner.nextLine()); // per day
        double food = Double.parseDouble(scanner.nextLine()); // per day


        double totalWater = days * players * water;
        double totalFood = days * players * food;

        double energyLevel = 0;

        for (int i = 1; i <= days; i++) {
            double energyLoss = Double.parseDouble(scanner.nextLine());
            energy = energy - energyLoss;

            if (energy <= 0) {
                System.out.printf("You will run out of energy. You will be left with %.2f food and %.2f water.", totalFood, totalWater);
                return;
            }

            if (i % 2 == 0) {
                energy = energy * 1.05;
                energyLevel = energy;
                totalWater -= totalWater * 0.3;
            }

            if (i % 3 == 0) {
                totalFood -= totalFood / players;
                energy = energy * 1.10;
                energyLevel = energy;
            }




        }
        if (energyLevel > 0) {
            System.out.printf("You are ready for the quest. You will be left with - %.2f energy!", energyLevel);


        }
    }
}


