# Ex19 Palindrome Check Using Deque
## DATE: 17-11-25
## AIM:
To design a program that checks whether a given message is a palindrome by removing all non-alphanumeric characters, converting all characters to lowercase, and using a deque data structure for comparison.

## Algorithm
1.Read the input message from the user.

2.Clean the string by removing all non-alphanumeric characters and converting it to lowercase.

3.Insert each character of the cleaned string into a deque — characters go to the rear.

4.Compare characters by repeatedly removing from the front and rear.

5.If all characters match until the deque has 0–1 elements → it is a palindrome.

## Program:
```
/*
Program to checks whether a given message is a palindrome by removing all non-alphanumeric characters.
Developed by: VIMALA SAHANA W
RegisterNumber: 212223040241  
*/
import java.util.Deque;
import java.util.LinkedList;
import java.util.Scanner;

public class PalindromeDeque {

    // Function to check palindrome using deque
    public static boolean isPalindrome(String message) {

        // Step 1: Clean message (remove non-alphanumeric characters, lowercase)
        String cleaned = message.replaceAll("[^a-zA-Z0-9]", "").toLowerCase();

        Deque<Character> deque = new LinkedList<>();

        // Step 2: Add characters to deque
        for (char ch : cleaned.toCharArray()) {
            deque.addLast(ch);
        }

        // Step 3: Compare front & rear
        while (deque.size() > 1) {
            char front = deque.removeFirst();
            char rear = deque.removeLast();

            if (front != rear) {
                return false;  // Not a palindrome
            }
        }

        return true; // Palindrome if all matched
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a message: ");
        String message = sc.nextLine();

        if (isPalindrome(message)) {
            System.out.println("The message IS a palindrome.");
        } else {
            System.out.println("The message is NOT a palindrome.");
        }

        sc.close();
    }
}

```

## Output:
<img width="497" height="161" alt="image" src="https://github.com/user-attachments/assets/320b8e6d-bdc1-41cf-8f52-60743df6f58a" />



## Result:
The program successfully removes all non-alphanumeric characters, converts the text to lowercase, and uses a deque to efficiently compare characters from both ends. Hence, it determines whether the string is a palindrome.
