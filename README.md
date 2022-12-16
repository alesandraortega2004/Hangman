import java.util.ArrayList;
import java.util.regex.Pattern;
import java.util.Random;
import java.util.Scanner;

public class Hangman {

    public static String [] words = {"Rashaun", "Alesandra", "Team X"};
    public static Random random = new Random();
    public static Scanner scanner = new Scanner(System.in);
    public static ArrayList <String> array = new ArrayList<>();

    public static void printboard (ArrayList<String>array, int life) {
        for (String x : array) {
            System.out.println(x);


        }
        System.out.println(life + "life left");

    }
        public static boolean CheckTrueFalse (ArrayList <String>array,String TrueWord, int life) {
            //true or false //check board

            String CheckTrueFalse = " ";

            for (String x = array){
                CheckTrueFalse += x;
            }
            if (CheckTrueFalse.equals(TrueWord)) {
                System.out.println("You Answered Correctly");
                return false;
            }
            //when you are out of lives
            else if (life == 0) {
                System.out.println("You Died");
                System.out.println("Game Over");
                System.out.println("You Died  .   . ");
                System.out.println("(_____)");
                return false;
            }
            return true;
        }
    public static void main(String[] args) {
        while (true) {
            String TrueWord = "";
            array.clear();

            int life = 6;
            
          
            // How to EXIT and START new game
            

            System.out.println("Welcome to Hangman By Rashaun and Alesandra");
            System.out.println();

            System.out.println("new game press: n");
            System.out.println("exit game press: e");
            String menu = scanner.nextLine();

            if (menu.equals("e")) {
                System.out.println("Exiting Game");

                break;
            } else if (menu.equals("n")) {
              
            
                

                int index = random.nextInt(words.length);
                TrueWord += words[index];

                for (int i = 0; i < TrueWord.length(); i++) {
                    array.add("");
                }
                
                printboard(array, life);

                while (CheckTrueFalse(array, TrueWord, life)){
                    System.out.println("Enter a letter from A-Z");
                    System.out.println("Starting Game"); 
                    continue;
                    
                String answer = scanner.nextLine();
                
                if (Pattern.matches("A-Z", answer)){
                    System.out.println("NULL");
                

              
                }

                    char letter = answer.charAt(0);

                    if (array.contains(answer)) {
                        System.out.println("NULL");
                    } else {
                        for (int i = 0; i < TrueWord.length(); i++) {
                            if (TrueWord.charAt(i) == letter) {
                                array.remove(i);
                                array.add(i, answer);

                            }
                        }
                        if (array.contains(answer)) {
                            life -= 1;
                        }
                    }

                    printboard(array, life);

                }
            }
