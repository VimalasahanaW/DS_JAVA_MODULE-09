# Ex17 Reversing a String Using Stack Data Structure
## DATE: 17-11-25
## AIM:
To write a Java program that reverses an input string using a stack, without using built-in reverse functions.

## Algorithm
1.Create an empty stack to store characters.

2.Read the input string from the user.

3.Push each character of the string onto the stack.

4.Pop characters one-by-one from the stack and add them to a new string (this reverses the order).

5.Display the reversed string as output.

## Program:
```
/*
Program to reverses an input string using a stack
Developed by: VIMALA SAHANA W
RegisterNumber: 212223040241
*/
import java.util.Scanner;
import java.util.Stack;

public class ReverseStringUsingStack {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String input = sc.nextLine();

        Stack<Character> stack = new Stack<>();

        // Push all characters onto the stack
        for (char ch : input.toCharArray()) {
            stack.push(ch);
        }

        // Pop characters to reverse the string
        String reversed = "";
        while (!stack.isEmpty()) {
            reversed += stack.pop();
        }

        System.out.println("Reversed String: " + reversed);

        sc.close();
    }
}

```

## Output:

<img width="430" height="139" alt="image" src="https://github.com/user-attachments/assets/a62aafe1-87ea-4f55-a6d1-38b37f99e5f9" />


## Result:
Thus, the program successfully reverses the given string using a stack without relying on built-in reverse functions.
