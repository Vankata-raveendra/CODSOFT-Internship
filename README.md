// TASK-1   NUMBER GAME
1.Generate a random number within a specified range, such as 1 to 100.

import java.util.Random;
import java.util.Scanner;

public class Main1 {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);


        System.out.print("Enter the minimum value: ");
        int min = scanner.nextInt();

        System.out.print("Enter the maximum value: ");
        int max = scanner.nextInt();

        int randomNumber = generateRandomNumber(min, max);

        System.out.println("Random number between " + min + " and " + max + ": " + randomNumber);

        scanner.close();
    }

    public static int generateRandomNumber(int min, int max) {
        Random random = new Random();
        return random.nextInt((max - min) + 1) + min;
    }
}


//2. Prompt the user to enter their guess for the generated number.


import java.util.Random;
import java.util.Scanner;

public class Main2 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the minimum value: ");
        int min = readInteger(scanner);

        System.out.print("Enter the maximum value: ");
        int max = readInteger(scanner);

        Random random = new Random();
        int randomNumber = random.nextInt((max - min) + 1) + min;

        System.out.println("Guess a number between " + min + " and " + max + ":");

        int guess;
        do {
            System.out.print("Your guess: ");
            guess = readInteger(scanner);

            if (guess < randomNumber) {
                System.out.println("Too low! Try again.");
            } else if (guess > randomNumber) {
                System.out.println("Too high! Try again.");
            }
        } while (guess != randomNumber);

        System.out.println("Congratulations! You guessed the correct number: " + randomNumber);

        scanner.close();
    }

    public static int readInteger(Scanner scanner) {
        while (!scanner.hasNextInt()) {
            System.out.println("Invalid input. Please enter an integer.");
            scanner.next(); // consume the non-integer input
        }
        return scanner.nextInt();
    }
}

//3. Compare the user's guess with the generated number and provide feedback on whether the guess
      is correct, too high, or too low.

import java.util.Random;
import java.util.Scanner;

public class Main3 {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter the minimum value: ");
        int min = scanner.nextInt();
        
        System.out.print("Enter the maximum value: ");
        int max = scanner.nextInt();
        
        if (min > max) {
            System.out.println("Invalid range. The minimum value must be less than or equal to the maximum value.");
            return;
        }
        
        Random random = new Random();
        
        int randomNumber = random.nextInt((max - min) + 1) + min;
        
        int guess;
        
        while (true) {
            System.out.print("Guess the number between " + min + " and " + max + ": ");
            guess = scanner.nextInt();
            
            if (guess < randomNumber) {
                System.out.println("Too low! Try again.");
            } else if (guess > randomNumber) {
                System.out.println("Too high! Try again.");
            } else {
                System.out.println("Congratulations! You guessed the correct number: " + randomNumber);
                break;
            }
        }
        
        scanner.close();
    }
}


//4. Repeat steps 2 and 3 until the user guesses the correct number.


import java.util.Random;
import java.util.Scanner;

public class Main4 {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter the minimum value: ");
        int min = scanner.nextInt();
        
        System.out.print("Enter the maximum value: ");
        int max = scanner.nextInt();
        
        if (min > max) {
            System.out.println("Invalid range. The minimum value must be less than or equal to the maximum value.");
            scanner.close();
            return;
        }
        
        while (true) {

            Random random = new Random();
            
            int randomNumber = random.nextInt((max - min) + 1) + min;
            
            int guess;
            
            while (true) {
                System.out.print("Guess the number between " + min + " and " + max + ": ");
                guess = scanner.nextInt();
                
                if (guess < randomNumber) {
                    System.out.println("Too low! Try again.");
                } else if (guess > randomNumber) {
                    System.out.println("Too high! Try again.");
                } else {
                    System.out.println("Congratulations! You guessed the correct number: " + randomNumber);
                    break;
                }
            }
            
            System.out.print("Do you want to play again? (yes/no): ");
            scanner.nextLine(); // consume the newline character
            String response = scanner.nextLine();
            
            if (!response.equalsIgnoreCase("yes")) {
                break;
            }
        }
        
        scanner.close();
    }
}


//5. Limit the number of attempts the user has to guess the number.


import java.util.Random;
import java.util.Scanner;

public class Main5 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter the minimum value: ");
        int min = scanner.nextInt();
        
        System.out.print("Enter the maximum value: ");
        int max = scanner.nextInt();
        
        if (min > max) {
            System.out.println("Invalid range. The minimum value must be less than or equal to the maximum value.");
            return;
        }
        
        Random random = new Random();
        
        int randomNumber = random.nextInt((max - min) + 1) + min;
        
        int guess;
        
        int maxAttempts = 5;
        int attempts = 0;
        
        while (attempts < maxAttempts) {
            System.out.print("Guess the number between " + min + " and " + max + ": ");
            guess = scanner.nextInt();
            attempts++;
            
            if (guess < randomNumber) {
                System.out.println("Too low! Try again.");
            } else if (guess > randomNumber) {
                System.out.println("Too high! Try again.");
            } else {
                System.out.println("Congratulations! You guessed the correct number: " + randomNumber);
                return; 
            }
        }
        
        System.out.println("Sorry, you've exceeded the maximum number of attempts. The correct number was: " + randomNumber);
        
        scanner.close();
    }
}


//6. Add the option for multiple rounds, allowing the user to play again.


import java.util.Random;
import java.util.Scanner;

public class Main6 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        boolean playAgain;
        
        do {
            playGame(scanner);
            
            System.out.print("Do you want to play again? (yes/no): ");
            String playAgainInput = scanner.next();
            
            playAgain = playAgainInput.equalsIgnoreCase("yes");
        } while (playAgain);
        
        scanner.close();
    }
    
    public static void playGame(Scanner scanner) {
        System.out.println("Let's play a game!");
        
        int min, max;
        
        System.out.print("Enter the minimum value: ");
        min = scanner.nextInt();
        
        System.out.print("Enter the maximum value: ");
        max = scanner.nextInt();
        
        if (min > max) {
            System.out.println("Invalid range. The minimum value must be less than or equal to the maximum value.");
            return;
        }
        
        Random random = new Random();
        
        int randomNumber = random.nextInt((max - min) + 1) + min;
        
        int maxAttempts = 5;
        int attempts = 0;
        
        while (attempts < maxAttempts) {

            System.out.print("Guess the number between " + min + " and " + max + ": ");
            int guess = scanner.nextInt();
            attempts++;
            
            if (guess < randomNumber) {
                System.out.println("Too low! Try again.");
            } else if (guess > randomNumber) {
                System.out.println("Too high! Try again.");
            } else {
                System.out.println("Congratulations! You guessed the correct number: " + randomNumber);
                return; 
            }
        }
        

        System.out.println("Sorry, you've exceeded the maximum number of attempts. The correct number was: " + randomNumber);
    }
}


//7. Display the user's score, which can be based on the number of attempts taken or rounds won.


import java.util.Random;
import java.util.Scanner;

public class Main7 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        boolean playAgain;
        int totalAttempts = 0; 

        do {
            int attempts = playGame(scanner); 
            totalAttempts += attempts; 
            
            System.out.println("Your score for this round: " + attempts + " attempts.");
            System.out.println("Your total score: " + totalAttempts + " attempts.");

            System.out.print("Do you want to play again? (yes/no): ");
            String playAgainInput = scanner.next();
            
            playAgain = playAgainInput.equalsIgnoreCase("yes");
        } while (playAgain);
        

        scanner.close();
    }
    
    public static int playGame(Scanner scanner) {
        System.out.println("Let's play a game!");
        
        int min, max;
        

        System.out.print("Enter the minimum value: ");
        min = scanner.nextInt();
        
        System.out.print("Enter the maximum value: ");
        max = scanner.nextInt();
        
        if (min > max) {
            System.out.println("Invalid range. The minimum value must be less than or equal to the maximum value.");
            return 0; // Return 0 attempts if invalid range
        }
        
        Random random = new Random();
        
        int randomNumber = random.nextInt((max - min) + 1) + min;
        
        int maxAttempts = 5;
        int attempts = 0;
        

        while (attempts < maxAttempts) {

            System.out.print("Guess the number between " + min + " and " + max + ": ");
            int guess = scanner.nextInt();
            attempts++;
            
            if (guess < randomNumber) {
                System.out.println("Too low! Try again.");
            } else if (guess > randomNumber) {
                System.out.println("Too high! Try again.");
            } else {
                System.out.println("Congratulations! You guessed the correct number: " + randomNumber);
                return attempts; // End the game and return attempts
            }
        }
        
        System.out.println("Sorry, you've exceeded the maximum number of attempts. The correct number was: " + randomNumber);
        return attempts; 
    }
}




//TASK-2 WORD COUNTER
1. Implementing input validation to handle empty inputs or file errors.

import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.util.Scanner;

public class InputValidation {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String text = "";

        System.out.println("Enter the text directly or type 'file' to provide a file path:");

        if (scanner.hasNextLine()) {
            String input = scanner.nextLine();
            if (input.equalsIgnoreCase("file")) {
                System.out.println("Please enter the file path:");
                String filePath = scanner.nextLine();
                text = readFile(filePath);
            } else {
                text = input;
            }
        }

        if (text.isEmpty()) {
            System.out.println("No input provided. Exiting.");
            return;
        }

        System.out.println("Input text: " + text);
    }

    private static String readFile(String filePath) {
        StringBuilder content = new StringBuilder();
        try (BufferedReader br = new BufferedReader(new FileReader(filePath))) {
            String line;
            while ((line = br.readLine()) != null) {
                content.append(line).append(" ");
            }
        } catch (IOException e) {
            System.out.println("File reading error: " + e.getMessage());
        }
        return content.toString();
    }
}


//2.Read the input text or file and store it in a string.

import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.util.Scanner;

public class ReadInput {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String text = "";

        System.out.println("Enter the text directly or type 'file' to provide a file path:");

        String input = scanner.nextLine();
        if (input.equalsIgnoreCase("file")) {
            System.out.println("Please enter the file path:");
            String filePath = scanner.nextLine();
            text = readFile(filePath);
        } else {
            text = input;
        }

        System.out.println("Input text: " + text);
    }

    private static String readFile(String filePath) {
        StringBuilder content = new StringBuilder();
        try (BufferedReader br = new BufferedReader(new FileReader(filePath))) {
            String line;
            while ((line = br.readLine()) != null) {
                content.append(line).append(" ");
            }
        } catch (IOException e) {
            System.out.println("File reading error: " + e.getMessage());
        }
        return content.toString();
    }
}


//3. Split the string into an array of words using space or punctuation as delimiters.


import java.util.Arrays;

public class SplitWords {
    public static void main(String[] args) {
        String text = "This is a sample text. This text is for testing.";

        String[] words = text.split("\\W+");
        System.out.println("Words: " + Arrays.toString(words));
    }
}


//4. Prompt the user to enter a text or provide a file to count the words.


import java.util.Scanner;

public class UserInputs{
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter the text directly or type 'file' to provide a file path:");

        String input = scanner.nextLine();
        if (input.equalsIgnoreCase("file")) {
            System.out.println("Please enter the file path:");
            String filePath = scanner.nextLine();
            System.out.println("File path entered: " + filePath);
        } else {
            System.out.println("Text entered: " + input);
        }
    }
}


//5.Display the total count of words to the user.

import java.util.Scanner;

public class WordCounter {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Enter the text:");
        String text = scanner.nextLine();
        
        String[] words = text.split("\\W+");
        
        int wordCount = words.length;
        System.out.println("Total word count: " + wordCount);
        
        scanner.close();
    }
}


//6.Initialize a counter variable to keep track of the number of words.


public class WordCounter1 {
    public static void main(String[] args) {
        String text = "This is a sample text. This text is for testing.";
        String[] words = text.split("\\W+");

        int wordCount = 0;
        for (String word : words) {
            if (!word.isEmpty()) {
                wordCount++;
            }
        }
        System.out.println("Total word count: " + wordCount);
    }
}


//7.Adding a graphical user interface (GUI) for a more user-friendly experience.


import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.util.Arrays;
import java.util.HashMap;
import java.util.HashSet;
import java.util.Map;
import java.util.Set;

public class WordCounterGUI extends JFrame {
    private JTextArea textArea;
    private JButton countButton;
    private JLabel resultLabel;

    private static final Set<String> STOP_WORDS = new HashSet<>(Arrays.asList(
        "a", "an", "and", "the", "in", "on", "at", "to", "is", "are", "was", "were", "of"
    ));

    public WordCounterGUI() {
        setTitle("Word Counter");
        setSize(400, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        textArea = new JTextArea();
        countButton = new JButton("Count Words");
        resultLabel = new JLabel("Word count: 0");

        countButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String text = textArea.getText();
                if (text.isEmpty()) {
                    resultLabel.setText("No text entered.");
                } else {
                    String[] words = text.split("\\W+");
                    int wordCount = 0;
                    Map<String, Integer> wordFrequencies = new HashMap<>();
                    for (String word : words) {
                        if (!word.isEmpty() && !STOP_WORDS.contains(word.toLowerCase())) {
                            wordCount++;
                            wordFrequencies.put(word.toLowerCase(), wordFrequencies.getOrDefault(word.toLowerCase(), 0) + 1);
                        }
                    }
                    resultLabel.setText("Word count: " + wordCount + ", Unique words: " + wordFrequencies.size());
                }
            }
        });

        add(new JScrollPane(textArea), "Center");
        add(countButton, "South");
        add(resultLabel, "North");
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            WordCounterGUI gui = new WordCounterGUI();
            gui.setVisible(true);
        });
    }
}


//8. Split the string into an array of words using space or punctuation as delimiters.


import java.util.Arrays;
import java.util.HashSet;
import java.util.Scanner;
import java.util.Set;

public class WordCounterWithStopWords {
    private static final Set<String> STOP_WORDS = new HashSet<>(Arrays.asList(
        "a", "an", "and", "the", "in", "on", "at", "to", "is", "are", "was", "were", "of"
    ));

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Enter the text:");
        String text = scanner.nextLine();
        
        String[] words = text.split("\\W+");

        int wordCount = 0;
        for (String word : words) {
            if (!word.isEmpty() && !STOP_WORDS.contains(word.toLowerCase())) {
                wordCount++;
            }
        }
        System.out.println("Total word count (excluding stop words): " + wordCount);
        
        scanner.close();
    }
}


//9. Iterate through the array of words and increment the counter for each word encountered.


import java.util.Arrays;
import java.util.HashSet;
import java.util.Scanner;
import java.util.Set;

public class WordCounterWithStopWordss {
    private static final Set<String> STOP_WORDS = new HashSet<>(Arrays.asList(
        "a", "an", "and", "the", "in", "on", "at", "to", "is", "are", "was", "were", "of"
    ));

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Enter the text:");
        String text = scanner.nextLine();
        
        String[] words = text.split("\\W+");

        int wordCount = 0;
        for (String word : words) {
            if (!word.isEmpty() && !STOP_WORDS.contains(word.toLowerCase())) {
                wordCount++;
            }
        }
        System.out.println("Total word count (excluding stop words): " + wordCount);
        
        scanner.close();
    }
}


//10. Providing statistics like the number of unique words or the frequency of each word.


import java.util.Arrays;
import java.util.HashMap;
import java.util.HashSet;
import java.util.Map;
import java.util.Scanner;
import java.util.Set;

public class WordStatistics {
    private static final Set<String> STOP_WORDS = new HashSet<>(Arrays.asList(
        "a", "an", "and", "the", "in", "on", "at", "to", "is", "are", "was", "were", "of"
    ));

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Enter the text:");
        String text = scanner.nextLine();
        
        String[] words = text.split("\\W+");

        int wordCount = 0;
        Map<String, Integer> wordFrequencies = new HashMap<>();
        for (String word : words) {
            if (!word.isEmpty() && !STOP_WORDS.contains(word.toLowerCase())) {
                wordCount++;
                wordFrequencies.put(word.toLowerCase(), wordFrequencies.getOrDefault(word.toLowerCase(), 0) + 1);
            }
        }

        System.out.println("Total word count (excluding stop words): " + wordCount);
        System.out.println("Number of unique words: " + wordFrequencies.size());
        System.out.println("Word frequencies: " + wordFrequencies);
        
        scanner.close();
    }
}


//TASK-3 STUDENT MANAGEMENT SYSTEM

//1.Create a Student class to represent individual students. Include attributes such as name, roll
    number, grade, and any other relevant details.

import java.util.Scanner;

public class Student {
    private String name;
    private int rollNumber;
    private String grade;

    public Student(String name, int rollNumber, String grade) {
        this.name = name;
        this.rollNumber = rollNumber;
        this.grade = grade;
    }


    public String getName() {
        return name;
    }

    public int getRollNumber() {
        return rollNumber;
    }

    public String getGrade() {
        return grade;
    }


    public void setName(String name) {
        this.name = name;
    }

    public void setRollNumber(int rollNumber) {
        this.rollNumber = rollNumber;
    }

    public void setGrade(String grade) {
        this.grade = grade;
    }


    public void displayStudentDetails() {
        System.out.println("Name: " + name);
        System.out.println("Roll Number: " + rollNumber);
        System.out.println("Grade: " + grade);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter student details:");

        System.out.print("Name: ");
        String name = scanner.nextLine();

        System.out.print("Roll Number: ");
        int rollNumber = scanner.nextInt();

        scanner.nextLine(); // Consume newline character

        System.out.print("Grade: ");
        String grade = scanner.nextLine();


        Student student = new Student(name, rollNumber, grade);


        System.out.println("\nStudent Details:");
        student.displayStudentDetails();

        scanner.close();
    }
}


//2. Implement methods to read and write student data to a storage medium, such as a file or a
      database.


import java.io.*;
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class StudentDataHandler {
    

    public static void writeStudentsToFile(List<Student> students, String fileName) {
        try (PrintWriter writer = new PrintWriter(new FileWriter(fileName))) {
            for (Student student : students) {
                writer.println(student.getName() + "," + student.getRollNumber() + "," + student.getGrade());
            }
            System.out.println("Student data written to file successfully.");
        } catch (IOException e) {
            System.err.println("Error writing student data to file: " + e.getMessage());
        }
    }
    

    public static List<Student> readStudentsFromFile(String fileName) {
        List<Student> students = new ArrayList<>();
        try (Scanner scanner = new Scanner(new File(fileName))) {
            while (scanner.hasNextLine()) {
                String line = scanner.nextLine();
                String[] parts = line.split(",");
                if (parts.length == 3) {
                    String name = parts[0];
                    int rollNumber = Integer.parseInt(parts[1]);
                    String grade = parts[2];
                    students.add(new Student(name, rollNumber, grade));
                }
            }
            System.out.println("Student data read from file successfully.");
        } catch (FileNotFoundException e) {
            System.err.println("File not found: " + e.getMessage());
        }
        return students;
    }


    public static void main(String[] args) {
        List<Student> students = new ArrayList<>();
        students.add(new Student("John", 101, "A"));
        students.add(new Student("Alice", 102, "B"));

        // Write student data to file
        writeStudentsToFile(students, "students.txt");

        // Read student data from file
        List<Student> readStudents = readStudentsFromFile("students.txt");
        for (Student student : readStudents) {
            System.out.println(student);
        }
    }
}

class Student {
    private String name;
    private int rollNumber;
    private String grade;

    public Student(String name, int rollNumber, String grade) {
        this.name = name;
        this.rollNumber = rollNumber;
        this.grade = grade;
    }

    public String getName() {
        return name;
    }

    public int getRollNumber() {
        return rollNumber;
    }

    public String getGrade() {
        return grade;
    }

    @Override
    public String toString() {
        return "Name: " + name + ", Roll Number: " + rollNumber + ", Grade: " + grade;
    }
}


//3.Implement a StudentManagementSystem class to manage the collection of students. Include
    methods to add a student, remove a student, search for a student, and display all students.

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.*;
import java.util.HashMap;
import java.util.Map;

class Student {
    private String name;
    private int rollNumber;
    private String grade;

    public Student(String name, int rollNumber, String grade) {
        this.name = name;
        this.rollNumber = rollNumber;
        this.grade = grade;
    }

    public int getRollNumber() {
        return rollNumber;
    }

    @Override
    public String toString() {
        return "Name: " + name + ", Roll Number: " + rollNumber + ", Grade: " + grade;
    }
}

class StudentManagementSystem {
    private Map<Integer, Student> studentMap;
    private static final String FILE_NAME = "students.txt";

    public StudentManagementSystem() {
        studentMap = new HashMap<>();
        loadStudentsFromFile();
    }

    public void addStudent(String name, int rollNumber, String grade) {
        Student student = new Student(name, rollNumber, grade);
        studentMap.put(rollNumber, student);
        saveStudentsToFile();
    }

    public boolean removeStudent(int rollNumber) {
        if (studentMap.containsKey(rollNumber)) {
            studentMap.remove(rollNumber);
            saveStudentsToFile();
            return true;
        } else {
            return false;
        }
    }

    public String searchStudent(int rollNumber) {
        Student student = studentMap.get(rollNumber);
        return (student != null) ? student.toString() : null;
    }

    public String displayAllStudents() {
        StringBuilder allStudents = new StringBuilder();
        for (Student student : studentMap.values()) {
            allStudents.append(student).append("\n");
        }
        return allStudents.toString().trim();
    }

    private void saveStudentsToFile() {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(FILE_NAME))) {
            for (Student student : studentMap.values()) {
                writer.write(student.toString());
                writer.newLine();
            }
        } catch (IOException e) {
            System.out.println("Error saving students to file: " + e.getMessage());
        }
    }

    private void loadStudentsFromFile() {
        try (BufferedReader reader = new BufferedReader(new FileReader(FILE_NAME))) {
            String line;
            while ((line = reader.readLine()) != null) {
                String[] parts = line.split(", ");
                if (parts.length == 3) {
                    String name = parts[0].split(": ")[1];
                    int rollNumber = Integer.parseInt(parts[1].split(": ")[1]);
                    String grade = parts[2].split(": ")[1];
                    studentMap.put(rollNumber, new Student(name, rollNumber, grade));
                }
            }
        } catch (FileNotFoundException e) {
            System.out.println("No existing student data found. Starting fresh.");
        } catch (IOException e) {
            System.out.println("Error loading students from file: " + e.getMessage());
        }
    }
}

public class StudentManagementSystemUI1{
    private StudentManagementSystem system;

    public StudentManagementSystemUI() {
        system = new StudentManagementSystem();
        createAndShowGUI();
    }

    private void createAndShowGUI() {
        JFrame frame = new JFrame("Student Management System");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(500, 400);

        JPanel panel = new JPanel();
        panel.setLayout(new GridLayout(6, 2));

        JLabel nameLabel = new JLabel("Name:");
        JTextField nameField = new JTextField();

        JLabel rollLabel = new JLabel("Roll Number:");
        JTextField rollField = new JTextField();

        JLabel gradeLabel = new JLabel("Grade:");
        JTextField gradeField = new JTextField();

        JButton addButton = new JButton("Add Student");
        JButton removeButton = new JButton("Remove Student");
        JButton searchButton = new JButton("Search Student");
        JButton displayButton = new JButton("Display All Students");

        JTextArea resultArea = new JTextArea();
        resultArea.setEditable(false);

        addButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String name = nameField.getText();
                String rollText = rollField.getText();
                String grade = gradeField.getText();

                if (name.isEmpty() || rollText.isEmpty() || grade.isEmpty()) {
                    resultArea.setText("Please fill all fields.");
                    return;
                }

                try {
                    int rollNumber = Integer.parseInt(rollText);
                    system.addStudent(name, rollNumber, grade);
                    resultArea.setText("Student added successfully.");
                } catch (NumberFormatException ex) {
                    resultArea.setText("Invalid roll number.");
                }
            }
        });

        removeButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String rollText = rollField.getText();

                if (rollText.isEmpty()) {
                    resultArea.setText("Please enter the roll number.");
                    return;
                }

                try {
                    int rollNumber = Integer.parseInt(rollText);
                    boolean removed = system.removeStudent(rollNumber);
                    resultArea.setText(removed ? "Student removed successfully." : "Student not found.");
                } catch (NumberFormatException ex) {
                    resultArea.setText("Invalid roll number.");
                }
            }
        });

        searchButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String rollText = rollField.getText();

                if (rollText.isEmpty()) {
                    resultArea.setText("Please enter the roll number.");
                    return;
                }

                try {
                    int rollNumber = Integer.parseInt(rollText);
                    String result = system.searchStudent(rollNumber);
                    resultArea.setText(result != null ? result : "Student not found.");
                } catch (NumberFormatException ex) {
                    resultArea.setText("Invalid roll number.");
                }
            }
        });

        displayButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String allStudents = system.displayAllStudents();
                resultArea.setText(!allStudents.isEmpty() ? allStudents : "No students found.");
            }
        });

        panel.add(nameLabel);
        panel.add(nameField);
        panel.add(rollLabel);
        panel.add(rollField);
        panel.add(gradeLabel);
        panel.add(gradeField);
        panel.add(addButton);
        panel.add(removeButton);
        panel.add(searchButton);
        panel.add(displayButton);

        frame.add(panel, BorderLayout.NORTH);
        frame.add(new JScrollPane(resultArea), BorderLayout.CENTER);

        frame.setVisible(true);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                new StudentManagementSystemUI();
            }
        });
    }
}


//4. Allow users to interact with the Student Management System by providing options such as
     adding a new student, editing an existing student's information, searching for a student, displaying all
     students, and exiting the application.

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class StudentManagementSystem1 {
    private List<Student> students;
    private Scanner scanner;

    public StudentManagementSystem1() {
        students = new ArrayList<>();
        scanner = new Scanner(System.in);
    }

    public void displayMenu() {
        while (true) {
            System.out.println("\nStudent Management System Menu:");
            System.out.println("1. Add Student");
            System.out.println("2. Edit Student");
            System.out.println("3. Search Student");
            System.out.println("4. Display All Students");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");

            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline character

            switch (choice) {
                case 1:
                    addStudent();
                    break;
                case 2:
                    editStudent();
                    break;
                case 3:
                    searchStudent();
                    break;
                case 4:
                    displayAllStudents();
                    break;
                case 5:
                    System.out.println("Exiting program.");
                    return;
                default:
                    System.out.println("Invalid choice. Please enter a number between 1 and 5.");
            }
        }
    }

    private void addStudent() {
        System.out.println("\nEnter student details:");
        System.out.print("Name: ");
        String name = scanner.nextLine();
        System.out.print("Roll Number: ");
        int rollNumber = scanner.nextInt();
        scanner.nextLine(); // Consume newline character
        System.out.print("Grade: ");
        String grade = scanner.nextLine();

        students.add(new Student(name, rollNumber, grade));
        System.out.println("Student added successfully.");
    }

    private void editStudent() {
        System.out.print("Enter roll number of student to edit: ");
        int rollNumber = scanner.nextInt();
        scanner.nextLine(); // Consume newline character

        boolean found = false;
        for (Student student : students) {
            if (student.getRollNumber() == rollNumber) {
                System.out.println("Enter new details for student:");
                System.out.print("Name: ");
                student.setName(scanner.nextLine());
                System.out.print("Grade: ");
                student.setGrade(scanner.nextLine());
                found = true;
                System.out.println("Student information updated successfully.");
                break;
            }
        }
        if (!found) {
            System.out.println("Student not found.");
        }
    }

    private void searchStudent() {
        System.out.print("Enter roll number of student to search: ");
        int rollNumber = scanner.nextInt();
        scanner.nextLine(); 

        boolean found = false;
        for (Student student : students) {
            if (student.getRollNumber() == rollNumber) {
                System.out.println("Student found:");
                System.out.println(student);
                found = true;
                break;
            }
        }
        if (!found) {
            System.out.println("Student not found.");
        }
    }

    private void displayAllStudents() {
        if (students.isEmpty()) {
            System.out.println("No students found.");
        } else {
            System.out.println("All Students:");
            for (Student student : students) {
                System.out.println(student);
            }
        }
    }

    public static void main(String[] args) {
        StudentManagementSystem1 system = new StudentManagementSystem1();
        system.displayMenu();
    }
}

class Student {
    private String name;
    private int rollNumber;
    private String grade;

    public Student(String name, int rollNumber, String grade) {
        this.name = name;
        this.rollNumber = rollNumber;
        this.grade = grade;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getRollNumber() {
        return rollNumber;
    }

    public String getGrade() {
        return grade;
    }

    public void setGrade(String grade) {
        this.grade = grade;
    }

    @Override
    public String toString() {
        return "Name: " + name + ", Roll Number: " + rollNumber + ", Grade: " + grade;
    }
}


//5.  Design the user interface for the Student Management System. This can be a console-based
      interface or a graphical user interface (GUI) using libraries like Swing or JavaFX

import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;


class Student {
    private String name;
    private int rollNumber;
    private String grade;

    public Student(String name, int rollNumber, String grade) {
        this.name = name;
        this.rollNumber = rollNumber;
        this.grade = grade;
    }

    public int getRollNumber() {
        return rollNumber;
    }

    @Override
    public String toString() {
        return "Name: " + name + ", Roll Number: " + rollNumber + ", Grade: " + grade;
    }
}


class StudentManagementSystem {
    private Map<Integer, Student> studentMap;

    public StudentManagementSystem() {
        studentMap = new HashMap<>();
    }

    public void addStudent(String name, int rollNumber, String grade) {
        Student student = new Student(name, rollNumber, grade);
        studentMap.put(rollNumber, student);
    }

    public boolean removeStudent(int rollNumber) {
        if (studentMap.containsKey(rollNumber)) {
            studentMap.remove(rollNumber);
            return true;
        } else {
            return false;
        }
    }

    public String searchStudent(int rollNumber) {
        Student student = studentMap.get(rollNumber);
        return (student != null) ? student.toString() : null;
    }

    public String displayAllStudents() {
        StringBuilder allStudents = new StringBuilder();
        for (Student student : studentMap.values()) {
            allStudents.append(student).append("\n");
        }
        return allStudents.toString().trim();
    }
}


public class StudentManagementSystemUI {
    private Scanner scanner;
    private StudentManagementSystem system;

    public StudentManagementSystemUI() {
        scanner = new Scanner(System.in);
        system = new StudentManagementSystem();
    }

    public void displayMenu() {
        while (true) {
            System.out.println("\nStudent Management System Menu:");
            System.out.println("1. Add Student");
            System.out.println("2. Remove Student");
            System.out.println("3. Search Student");
            System.out.println("4. Display All Students");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");

            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline character

            switch (choice) {
                case 1:
                    addStudent();
                    break;
                case 2:
                    removeStudent();
                    break;
                case 3:
                    searchStudent();
                    break;
                case 4:
                    displayAllStudents();
                    break;
                case 5:
                    System.out.println("Exiting program.");
                    scanner.close();
                    System.exit(0);
                default:
                    System.out.println("Invalid choice. Please enter a number between 1 and 5.");
            }
        }
    }

    private void addStudent() {
        System.out.println("\nEnter student details:");
        System.out.print("Name: ");
        String name = scanner.nextLine();
        System.out.print("Roll Number: ");
        int rollNumber = scanner.nextInt();
        scanner.nextLine(); // Consume newline character
        System.out.print("Grade: ");
        String grade = scanner.nextLine();

        system.addStudent(name, rollNumber, grade);
        System.out.println("Student added successfully.");
    }

    private void removeStudent() {
        System.out.print("Enter roll number of student to remove: ");
        int rollNumber = scanner.nextInt();
        scanner.nextLine(); 

        boolean removed = system.removeStudent(rollNumber);
        if (removed) {
            System.out.println("Student removed successfully.");
        } else {
            System.out.println("Student not found.");
        }
    }

    private void searchStudent() {
        System.out.print("Enter roll number of student to search: ");
        int rollNumber = scanner.nextInt();
        scanner.nextLine(); 

        String result = system.searchStudent(rollNumber);
        if (result != null) {
            System.out.println("Student found:");
            System.out.println(result);
        } else {
            System.out.println("Student not found.");
        }
    }

    private void displayAllStudents() {
        String allStudents = system.displayAllStudents();
        if (!allStudents.isEmpty()) {
            System.out.println("All Students:");
            System.out.println(allStudents);
        } else {
            System.out.println("No students found.");
        }
    }

    public static void main(String[] args) {
        StudentManagementSystemUI ui = new StudentManagementSystemUI();
        ui.displayMenu();
    }
}


//TASK-4 ATM INTERFACE
1.Design the user interface for the ATM, including options such as withdrawing, depositing, and
  checking the balance

import java.util.Scanner;

class BankAccount {
    private double balance;

    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }
}

class ATM {
    private BankAccount account;

    public ATM(BankAccount account) {
        this.account = account;
    }

    public void withdraw(double amount) {
        if (amount <= 0) {
            System.out.println("Invalid amount. Please enter a positive number.");
        } else if (amount > account.getBalance()) {
            System.out.println("Insufficient balance. Transaction failed.");
        } else {
            account.setBalance(account.getBalance() - amount);
            System.out.println("Withdrawal successful. Your new balance is: $" + account.getBalance());
        }
    }

    public void deposit(double amount) {
        if (amount <= 0) {
            System.out.println("Invalid amount. Please enter a positive number.");
        } else {
            account.setBalance(account.getBalance() + amount);
            System.out.println("Deposit successful. Your new balance is: $" + account.getBalance());
        }
    }

    public void checkBalance() {
        System.out.println("Your current balance is: $" + account.getBalance());
    }
}

public class ATMApp {
    private static final Scanner scanner = new Scanner(System.in);
    private static final BankAccount account = new BankAccount(1000.0); // Initial balance
    private static final ATM atm = new ATM(account);

    public static void main(String[] args) {
        while (true) {
            System.out.println("\nATM Machine:");
            System.out.println("1. Withdraw");
            System.out.println("2. Deposit");
            System.out.println("3. Check Balance");
            System.out.println("4. Exit");
            System.out.print("Choose an option: ");

            int choice = Integer.parseInt(scanner.nextLine());

            switch (choice) {
                case 1:
                    handleWithdraw();
                    break;
                case 2:
                    handleDeposit();
                    break;
                case 3:
                    atm.checkBalance();
                    break;
                case 4:
                    System.out.println("Thank you for using the ATM. Goodbye!");
                    System.exit(0);
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }

    private static void handleWithdraw() {
        System.out.print("Enter the amount to withdraw: ");
        double amount = Double.parseDouble(scanner.nextLine());
        atm.withdraw(amount);
    }

    private static void handleDeposit() {
        System.out.print("Enter the amount to deposit: ");
        double amount = Double.parseDouble(scanner.nextLine());
        atm.deposit(amount);
    }
}


//2.Validate user input to ensure it is within acceptable limits (e.g., sufficient balance for withdrawals).

import java.util.Scanner;

class BankAccount {
    private double balance;

    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }
}

class ATM {
    private BankAccount account;

    public ATM(BankAccount account) {
        this.account = account;
    }

    public void withdraw(double amount) {
        if (amount <= 0) {
            System.out.println("Invalid amount. Please enter a positive number.");
        } else if (amount > account.getBalance()) {
            System.out.println("Insufficient balance. Transaction failed.");
        } else {
            account.setBalance(account.getBalance() - amount);
            System.out.println("Withdrawal successful. Your new balance is: $" + account.getBalance());
        }
    }

    public void deposit(double amount) {
        if (amount <= 0) {
            System.out.println("Invalid amount. Please enter a positive number.");
        } else {
            account.setBalance(account.getBalance() + amount);
            System.out.println("Deposit successful. Your new balance is: $" + account.getBalance());
        }
    }

    public void checkBalance() {
        System.out.println("Your current balance is: $" + account.getBalance());
    }
}

public class ATMApp1 {
    private static final Scanner scanner = new Scanner(System.in);
    private static final BankAccount account = new BankAccount(1000.0); // Initial balance
    private static final ATM atm = new ATM(account);

    public static void main(String[] args) {
        while (true) {
            System.out.println("\nATM Machine:");
            System.out.println("1. Withdraw");
            System.out.println("2. Deposit");
            System.out.println("3. Check Balance");
            System.out.println("4. Exit");
            System.out.print("Choose an option: ");

            int choice = Integer.parseInt(scanner.nextLine());

            switch (choice) {
                case 1:
                    handleWithdraw();
                    break;
                case 2:
                    handleDeposit();
                    break;
                case 3:
                    atm.checkBalance();
                    break;
                case 4:
                    System.out.println("Thank you for using the ATM. Goodbye!");
                    System.exit(0);
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }

    private static void handleWithdraw() {
        System.out.print("Enter the amount to withdraw: ");
        double amount = Double.parseDouble(scanner.nextLine());
        atm.withdraw(amount);
    }

    private static void handleDeposit() {
        System.out.print("Enter the amount to deposit: ");
        double amount = Double.parseDouble(scanner.nextLine());
        atm.deposit(amount);
    }
}


//3.Connect the ATM class with the user's bank account class to access and modify the account


import java.util.Scanner;

public class ATMMachine {
    private double balance;

    public ATMMachine(double initialBalance) {
        this.balance = initialBalance;
    }

    public double checkBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposit successful.");
        } else {
            System.out.println("Invalid deposit amount.");
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && balance >= amount) {
            balance -= amount;
            System.out.println("Withdrawal successful.");
        } else {
            System.out.println("Insufficient funds or invalid withdrawal amount.");
        }
    }

    public void transfer(double amount, ATMMachine receiver) {
        if (amount > 0 && balance >= amount) {
            balance -= amount;
            receiver.deposit(amount);
            System.out.println("Transfer successful.");
        } else {
            System.out.println("Insufficient funds or invalid transfer amount.");
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter initial balance: ");
        double initialBalance = scanner.nextDouble();
        ATMMachine atm = new ATMMachine(initialBalance);

        boolean exit = false;
        while (!exit) {
            System.out.println("\nATM Menu:");
            System.out.println("1. Check Balance");
            System.out.println("2. Deposit");
            System.out.println("3. Withdraw");
            System.out.println("4. Transfer");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.println("Current Balance: $" + atm.checkBalance());
                    break;
                case 2:
                    System.out.print("Enter deposit amount: $");
                    double depositAmount = scanner.nextDouble();
                    atm.deposit(depositAmount);
                    break;
                case 3:
                    System.out.print("Enter withdrawal amount: $");
                    double withdrawAmount = scanner.nextDouble();
                    atm.withdraw(withdrawAmount);
                    break;
                case 4:
                    System.out.print("Enter transfer amount: $");
                    double transferAmount = scanner.nextDouble();
                    System.out.print("Enter receiver's initial balance: $");
                    double receiverInitialBalance = scanner.nextDouble();
                    ATMMachine receiverATM = new ATMMachine(receiverInitialBalance);
                    atm.transfer(transferAmount, receiverATM);
                    break;
                case 5:
                    System.out.println("Exiting ATM. Thank you!");
                    exit = true;
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
        scanner.close();
    }
}


//4.Implement methods for each option, such as withdraw(amount), deposit(amount), and
   checkBalance().

import java.util.Scanner;

public class ATMProgram {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        BankAccount account = new BankAccount();
        ATM atm = new ATM(account);

        while (true) {
            System.out.println("\n--- ATM Menu ---");
            System.out.println("1. Deposit");
            System.out.println("2. Withdraw");
            System.out.println("3. Check Balance");
            System.out.println("4. Exit");

            System.out.print("Enter your choice (1-4): ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter amount to deposit: ");
                    double depositAmount = scanner.nextDouble();
                    atm.deposit(depositAmount);
                    break;
                case 2:
                    System.out.print("Enter amount to withdraw: ");
                    double withdrawAmount = scanner.nextDouble();
                    atm.withdraw(withdrawAmount);
                    break;
                case 3:
                    atm.checkBalance();
                    break;
                case 4:
                    System.out.println("Exiting the program. Goodbye!");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }
}

class BankAccount {
    private double balance;


    public BankAccount() {
        this.balance = 0.0;
    }


    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
    }


    public void withdraw(double amount) {
        if (amount > balance) {
            System.out.println("Insufficient funds.");
        } else {
            balance -= amount;
            System.out.println("Withdrew $" + amount);
        }
    }


    public void deposit(double amount) {
        balance += amount;
        System.out.println("Deposited $" + amount);
    }


    public void checkBalance() {
        System.out.println("Current balance: $" + balance);
    }
}

class ATM {
    private BankAccount account;


    public ATM(BankAccount account) {
        this.account = account;
    }


    public void deposit(double amount) {
        account.deposit(amount);
    }


    public void withdraw(double amount) {
        account.withdraw(amount);
    }


    public void checkBalance() {
        account.checkBalance();
    }
}


//5.Display appropriate messages to the user based on their chosen options and the success or failure
      of their transactions.


import java.util.Scanner;


class BankAccount {
    private double balance;


    public BankAccount() {
        this.balance = 0.0;
    }


    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
    }


    public void withdraw(double amount) {
        if (amount > balance) {
            System.out.println("Insufficient funds. Withdrawal failed.");
        } else if (amount <= 0) {
            System.out.println("Invalid amount. Withdrawal amount must be greater than zero.");
        } else {
            balance -= amount;
            System.out.println("Withdrew $" + amount);
        }
    }


    public void deposit(double amount) {
        if (amount <= 0) {
            System.out.println("Invalid amount. Deposit amount must be greater than zero.");
        } else {
            balance += amount;
            System.out.println("Deposited $" + amount);
        }
    }


    public void checkBalance() {
        System.out.println("Current balance: $" + balance);
    }
}


class ATM {
    private BankAccount account;


    public ATM(BankAccount account) {
        this.account = account;
    }


    public void deposit(double amount) {
        account.deposit(amount);
    }


    public void withdraw(double amount) {
        account.withdraw(amount);
    }


    public void checkBalance() {
        account.checkBalance();
    }
}


public class ATMProgram1 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        BankAccount account = new BankAccount();
        ATM atm = new ATM(account);

        while (true) {
            System.out.println("\n--- Bank Account Menu ---");
            System.out.println("1. Deposit");
            System.out.println("2. Withdraw");
            System.out.println("3. Check Balance");
            System.out.println("4. Exit");

            System.out.print("Enter your choice (1-4): ");
            int choice = getValidChoice(scanner);

            switch (choice) {
                case 1:
                    System.out.print("Enter amount to deposit: ");
                    double depositAmount = getValidAmount(scanner);
                    if (depositAmount > 0) {
                        atm.deposit(depositAmount);
                    }
                    break;
                case 2:
                    System.out.print("Enter amount to withdraw: ");
                    double withdrawAmount = getValidAmount(scanner);
                    if (withdrawAmount > 0) {
                        atm.withdraw(withdrawAmount);
                    }
                    break;
                case 3:
                    atm.checkBalance();
                    break;
                case 4:
                    System.out.println("Exiting the program. Goodbye!");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }


    private static int getValidChoice(Scanner scanner) {
        int choice;
        while (true) {
            if (scanner.hasNextInt()) {
                choice = scanner.nextInt();
                if (choice >= 1 && choice <= 4) {
                    break;
                } else {
                    System.out.print("Invalid choice. Please enter a number between 1 and 4: ");
                }
            } else {
                System.out.print("Invalid input. Please enter a number between 1 and 4: ");
                scanner.next(); // clear the invalid input
            }
        }
        return choice;
    }


    private static double getValidAmount(Scanner scanner) {
        double amount;
        while (true) {
            if (scanner.hasNextDouble()) {
                amount = scanner.nextDouble();
                if (amount > 0) {
                    break;
                } else {
                    System.out.print("Invalid amount. Please enter a positive number: ");
                }
            } else {
                System.out.print("Invalid input. Please enter a valid amount: ");
                scanner.next(); // clear the invalid input
            }
        }
        return amount;
    }
}


//6. Validate user input to ensure it is within acceptable limits (e.g., sufficient balance for withdrawals).


import java.util.Scanner;

public class BankAccountProgram {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        BankAccount account = new BankAccount();

        while (true) {
            System.out.println("\n--- Bank Account Menu ---");
            System.out.println("1. Deposit");
            System.out.println("2. Withdraw");
            System.out.println("3. Check Balance");
            System.out.println("4. Exit");

            System.out.print("Enter your choice (1-4): ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter amount to deposit: ");
                    double depositAmount = scanner.nextDouble();
                    account.deposit(depositAmount);
                    break;
                case 2:
                    System.out.print("Enter amount to withdraw: ");
                    double withdrawAmount = scanner.nextDouble();
                    account.withdraw(withdrawAmount);
                    break;
                case 3:
                    account.checkBalance();
                    break;
                case 4:
                    System.out.println("Exiting the program. Goodbye!");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }
}

class BankAccount {
    private double balance;


    public BankAccount() {
        this.balance = 0.0;
    }


    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
    }


    public void withdraw(double amount) {
        if (amount > balance) {
            System.out.println("Insufficient funds.");
        } else {
            balance -= amount;
            System.out.println("Withdrew $" + amount);
        }
    }


    public void deposit(double amount) {
        balance += amount;
        System.out.println("Deposited $" + amount);
    }


    public void checkBalance() {
        System.out.println("Current balance: $" + balance);
    }
}


//7.Create a class to represent the ATM machine.


import java.util.Scanner;

class ATM {
    private double balance;

    public ATM(double initialBalance) {
        this.balance = initialBalance;
    }

    public void deposit(double amount) {
        balance += amount;
        System.out.println("Deposit successful. Current balance: " + balance);
    }

    public void withdraw(double amount) {
        if (amount > balance) {
            System.out.println("Insufficient funds. Withdrawal failed.");
        } else {
            balance -= amount;
            System.out.println("Withdrawal successful. Current balance: " + balance);
        }
    }

    public double getBalance() {
        return balance;
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter initial balance: ");
        double initialBalance = scanner.nextDouble();

        ATM atm = new ATM(initialBalance);

        boolean exit = false;
        while (!exit) {
            System.out.println("\nATM Menu:");
            System.out.println("1. Deposit");
            System.out.println("2. Withdraw");
            System.out.println("3. Check Balance");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            
            // Handle non-integer input
            if (scanner.hasNextInt()) {
                int choice = scanner.nextInt();

                switch (choice) {
                    case 1:
                        System.out.print("Enter deposit amount: ");
                        double depositAmount = scanner.nextDouble();
                        atm.deposit(depositAmount);
                        break;
                    case 2:
                        System.out.print("Enter withdrawal amount: ");
                        double withdrawAmount = scanner.nextDouble();
                        atm.withdraw(withdrawAmount);
                        break;
                    case 3:
                        System.out.println("Current Balance: " + atm.getBalance());
                        break;
                    case 4:
                        System.out.println("Exiting ATM. Goodbye!");
                        exit = true;
                        break;
                    default:
                        System.out.println("Invalid choice. Please enter a number between 1 and 4.");
                }
            } else {
                System.out.println("Invalid input. Please enter a number.");
                scanner.next(); // Consume invalid input
            }
        }
        
        scanner.close(); // Close the scanner
    }
}


//TASK-5 ADDRESS BOOK SYSTEM

//1. Design the user interface for the Address Book System. This can be a console-based interface or a
graphical user interface (GUI) using libraries like Swing or JavaFX.

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.ArrayList;

class Contact {
    private String name;
    private String phoneNumber;
    private String emailAddress;

    public Contact(String name, String phoneNumber, String emailAddress) {
        this.name = name;
        this.phoneNumber = phoneNumber;
        this.emailAddress = emailAddress;
    }

    public String getName() {
        return name;
    }

    public String getPhoneNumber() {
        return phoneNumber;
    }

    public String getEmailAddress() {
        return emailAddress;
    }

    @Override
    public String toString() {
        return "Name: " + name + ", Phone Number: " + phoneNumber + ", Email Address: " + emailAddress;
    }
}

class AddressBook {
    private ArrayList<Contact> contacts;

    public AddressBook() {
        this.contacts = new ArrayList<>();
    }

    public void addContact(Contact contact) {
        contacts.add(contact);
    }

    public void removeContact(String name) {
        for (int i = 0; i < contacts.size(); i++) {
            if (contacts.get(i).getName().equalsIgnoreCase(name)) {
                contacts.remove(i);
                return;
            }
        }
    }

    public String searchContact(String name) {
        for (Contact contact : contacts) {
            if (contact.getName().equalsIgnoreCase(name)) {
                return contact.toString();
            }
        }
        return "Contact not found.";
    }

    public String displayAllContacts() {
        StringBuilder sb = new StringBuilder();
        for (Contact contact : contacts) {
            sb.append(contact.toString()).append("\n");
        }
        return sb.toString();
    }
}

public class AddressBookGUI extends JFrame {
    private AddressBook addressBook;

    private JTextField nameField;
    private JTextField phoneNumberField;
    private JTextField emailField;
    private JTextArea displayArea;

    public AddressBookGUI() {
        addressBook = new AddressBook();

        setTitle("Address Book System");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(400, 300);
        setLayout(new BorderLayout());

        JPanel inputPanel = new JPanel(new GridLayout(4, 2));
        inputPanel.add(new JLabel("Name:"));
        nameField = new JTextField();
        inputPanel.add(nameField);
        inputPanel.add(new JLabel("Phone Number:"));
        phoneNumberField = new JTextField();
        inputPanel.add(phoneNumberField);
        inputPanel.add(new JLabel("Email Address:"));
        emailField = new JTextField();
        inputPanel.add(emailField);

        JButton addButton = new JButton("Add Contact");
        addButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                String name = nameField.getText();
                String phoneNumber = phoneNumberField.getText();
                String emailAddress = emailField.getText();
                addressBook.addContact(new Contact(name, phoneNumber, emailAddress));
                nameField.setText("");
                phoneNumberField.setText("");
                emailField.setText("");
            }
        });
        inputPanel.add(addButton);

        JButton displayButton = new JButton("Display All Contacts");
        displayButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                displayArea.setText(addressBook.displayAllContacts());
            }
        });
        inputPanel.add(displayButton);

        add(inputPanel, BorderLayout.NORTH);

        displayArea = new JTextArea();
        add(new JScrollPane(displayArea), BorderLayout.CENTER);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                new AddressBookGUI().setVisible(true);
            }
        });
    }
}


//2.Create a Contact class to represent individual contacts. Include attributes such as name, phone
     number, email address, and any other relevant details

import java.util.ArrayList;
import java.util.Scanner;

class Contact {
    private String name;
    private String phoneNumber;
    private String emailAddress;

    public Contact(String name, String phoneNumber, String emailAddress) {
        this.name = name;
        this.phoneNumber = phoneNumber;
        this.emailAddress = emailAddress;
    }

    public String getName() {
        return name;
    }

    public String getPhoneNumber() {
        return phoneNumber;
    }

    public String getEmailAddress() {
        return emailAddress;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setPhoneNumber(String phoneNumber) {
        this.phoneNumber = phoneNumber;
    }

    public void setEmailAddress(String emailAddress) {
        this.emailAddress = emailAddress;
    }

    @Override
    public String toString() {
        return "Name: " + name + ", Phone Number: " + phoneNumber + ", Email Address: " + emailAddress;
    }
}

class AddressBook {
    private ArrayList<Contact> contacts;

    public AddressBook() {
        this.contacts = new ArrayList<>();
    }

    public void addContact(Contact contact) {
        contacts.add(contact);
        System.out.println("Contact added successfully.");
    }

    public void removeContact(String name) {
        for (int i = 0; i < contacts.size(); i++) {
            if (contacts.get(i).getName().equalsIgnoreCase(name)) {
                contacts.remove(i);
                System.out.println("Contact removed successfully.");
                return;
            }
        }
        System.out.println("Contact not found.");
    }

    public void searchContact(String name) {
        for (Contact contact : contacts) {
            if (contact.getName().equalsIgnoreCase(name)) {
                System.out.println("Contact found:");
                System.out.println(contact);
                return;
            }
        }
        System.out.println("Contact not found.");
    }

    public void displayAllContacts() {
        if (contacts.isEmpty()) {
            System.out.println("No contacts in the address book.");
        } else {
            System.out.println("All Contacts:");
            for (Contact contact : contacts) {
                System.out.println(contact);
            }
        }
    }
}

public class AddressBookManager {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        AddressBook addressBook = new AddressBook();

        while (true) {
            System.out.println("\n--- Address Book Menu ---");
            System.out.println("1. Add Contact");
            System.out.println("2. Remove Contact");
            System.out.println("3. Search Contact");
            System.out.println("4. Display All Contacts");
            System.out.println("5. Exit");

            System.out.print("Enter your choice (1-5): ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline character

            switch (choice) {
                case 1:
                    System.out.print("Enter name: ");
                    String name = scanner.nextLine();
                    System.out.print("Enter phone number: ");
                    String phoneNumber = scanner.nextLine();
                    System.out.print("Enter email address: ");
                    String emailAddress = scanner.nextLine();
                    Contact newContact = new Contact(name, phoneNumber, emailAddress);
                    addressBook.addContact(newContact);
                    break;
                case 2:
                    System.out.print("Enter name of contact to remove: ");
                    String nameToRemove = scanner.nextLine();
                    addressBook.removeContact(nameToRemove);
                    break;
                case 3:
                    System.out.print("Enter name of contact to search: ");
                    String nameToSearch = scanner.nextLine();
                    addressBook.searchContact(nameToSearch);
                    break;
                case 4:
                    addressBook.displayAllContacts();
                    break;
                case 5:
                    System.out.println("Exiting the program. Goodbye!");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }
}
