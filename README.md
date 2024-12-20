# IRAKOZE-TIMOTHEE-26428-SUNDAY_AFTERNOON-

import java.io.*;
import java.sql.*;

public class ExceptionHandlingDemo {
    public static void main(String[] args) {
        // Checked Exceptions
        handleIOException();
        handleFileNotFoundException();
        handleEOFException();
        handleSQLException();
        handleClassNotFoundException();

        // Unchecked Exceptions
        handleArithmeticException();
        handleNullPointerException();
        handleArrayIndexOutOfBoundsException();
        handleClassCastException();
        handleIllegalArgumentException();
        handleNumberFormatException();
    }

    // 1. IOException
    private static void handleIOException() {
        try {
            FileReader fileReader = new FileReader("non_existent_file.txt");
            fileReader.read();
        } catch (IOException e) {
            System.out.println("IOException caught: " + e.getMessage());
        }
    }

    // 2. FileNotFoundException
    private static void handleFileNotFoundException() {
        try {
            FileInputStream fileInputStream = new FileInputStream("missing_file.txt");
        } catch (FileNotFoundException e) {
            System.out.println("FileNotFoundException caught: " + e.getMessage());
        }
    }

    // 3. EOFException
    private static void handleEOFException() {
        try (DataInputStream dis = new DataInputStream(new FileInputStream("example.txt"))) {
            while (true) {
                dis.readByte(); // Throws EOFException if end of file is reached
            }
        } catch (EOFException e) {
            System.out.println("EOFException caught: End of file reached");
        } catch (IOException e) {
            System.out.println("IOException caught: " + e.getMessage());
        }
    }

    // 4. SQLException
    private static void handleSQLException() {
        try {
            Connection connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/invalidDB", "user", "password");
        } catch (SQLException e) {
            System.out.println("SQLException caught: " + e.getMessage());
        }
    }

    // 5. ClassNotFoundException
    private static void handleClassNotFoundException() {
        try {
            Class.forName("com.nonexistent.Driver");
        } catch (ClassNotFoundException e) {
            System.out.println("ClassNotFoundException caught: " + e.getMessage());
        }
    }

    // 6. ArithmeticException
    private static void handleArithmeticException() {
        try {
            int result = 10 / 0; // Division by zero
        } catch (ArithmeticException e) {
            System.out.println("ArithmeticException caught: " + e.getMessage());
        }
    }

    // 7. NullPointerException
    private static void handleNullPointerException() {
        try {
            String nullString = null;
            System.out.println(nullString.length());
        } catch (NullPointerException e) {
            System.out.println("NullPointerException caught: " + e.getMessage());
        }
    }

    // 8. ArrayIndexOutOfBoundsException
    private static void handleArrayIndexOutOfBoundsException() {
        try {
            int[] array = {1, 2, 3};
            System.out.println(array[5]); // Accessing invalid index
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("ArrayIndexOutOfBoundsException caught: " + e.getMessage());
        }
    }

    // 9. ClassCastException
    private static void handleClassCastException() {
        try {
            Object str = "Test String";
            Integer castedInt = (Integer) str; // Invalid type cast
        } catch (ClassCastException e) {
            System.out.println("ClassCastException caught: " + e.getMessage());
        }
    }

    // 10. IllegalArgumentException
    private static void handleIllegalArgumentException() {
        try {
            Thread.sleep(-100); // Negative argument not allowed
        } catch (IllegalArgumentException | InterruptedException e) {
            System.out.println("IllegalArgumentException caught: " + e.getMessage());
        }
    }

    // 11. NumberFormatException
    private static void handleNumberFormatException() {
        try {
            int number = Integer.parseInt("NotANumber"); // Invalid format
        } catch (NumberFormatException e) {
            System.out.println("NumberFormatException caught: " + e.getMessage());
        }
    }
}
