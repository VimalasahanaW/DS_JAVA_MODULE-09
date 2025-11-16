# Ex16 Check for Balanced Parentheses Using Stack
## DATE:17-11-25
## AIM:
To write a Java program that verifies whether the parentheses (brackets) in an input string are balanced — meaning each opening bracket (, {, [ has a corresponding and correctly ordered closing bracket ), }, ].

## Algorithm
1.Initialize a stack to store opening brackets.

2.Scan each character of the input string.

3.If it is an opening bracket ( ‘(’, ‘{’, ‘[’ ), push it onto the stack.

4.If it is a closing bracket, check if the stack is empty OR the top of the stack doesn’t match → then it is unbalanced. Otherwise, pop the stack.

5.After scanning all characters, if the stack is empty → Balanced, otherwise Unbalanced. 
   

## Program:
```
/*
Program to verify whether the parentheses (brackets) in an input string are balanced
Developed by: VIMALA SAHANA W
RegisterNumber: 212223040241
*/
import java.util.Scanner;
import java.util.Stack;

public class BalancedParentheses {
    public static boolean isBalanced(String str) {
        Stack<Character> stack = new Stack<>();

        for (char ch : str.toCharArray()) {
            // Push opening brackets
            if (ch == '(' || ch == '{' || ch == '[') {
                stack.push(ch);
            }
            // Process closing brackets
            else if (ch == ')' || ch == '}' || ch == ']') {
                if (stack.isEmpty()) {
                    return false; // No match
                }
                char top = stack.pop();

                // Check for correct matching
                if ((ch == ')' && top != '(') ||
                    (ch == '}' && top != '{') ||
                    (ch == ']' && top != '[')) {
                    return false;
                }
            }
        }

        return stack.isEmpty();  // True if fully matched
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.println("Enter a string to check parentheses balance: ");
        String input = sc.nextLine();

        if (isBalanced(input)) {
            System.out.println("Balanced");
        } else {
            System.out.println("Not Balanced");
        }

        sc.close();
    }
}

```

## Output:

<img width="634" height="166" alt="image" src="https://github.com/user-attachments/assets/cb54fb11-1b58-4373-b022-09556181dedd" />


## Result:
Thus,the program correctly checks whether an input string has balanced parentheses using a stack.
