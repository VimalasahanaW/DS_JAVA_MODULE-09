# Ex18 Simulation of a Ticket Counter Using Queue (Linked List Implementation)
## DATE:17-11-25
## AIM:
To simulate the functioning of a ticket counter that operates on a First-In-First-Out (FIFO) basis using a queue implemented via a linked list in Java.
## Algorithm
1.Create a Node class to store customer names and the next node reference.

2.Create enqueue (add) and dequeue (serve) methods using linked list operations.

3.Read user choices (1: Add customer, 2: Serve customer, 3: Exit).

4.For each choice:

    Enqueue → add customer to the end of the queue.

    Dequeue → remove customer from the front of the queue.

5.Continue until exit, displaying the served and waiting customers.
 

## Program:
```
/*
Program to functioning of a ticket counter that operates on a First-In-First-Out (FIFO)
Developed by: VIMALA SAHANA W
RegisterNumber: 212223040241 
*/
import java.util.Scanner;

public class TicketCounter {

    // Node class
    static class Node {
        String data;
        Node next;

        Node(String data) {
            this.data = data;
            this.next = null;
        }
    }

    // Queue implemented using linked list
    static class Queue {
        private Node front, rear;

        public void enqueue(String data) {
            Node newNode = new Node(data);
            if (rear == null) {
                front = rear = newNode;
                return;
            }
            rear.next = newNode;
            rear = newNode;
        }

        public String dequeue() {
            if (front == null) return null;
            String value = front.data;
            front = front.next;
            if (front == null) rear = null;
            return value;
        }

        public boolean isEmpty() {
            return front == null;
        }

        public String toString() {
            StringBuilder sb = new StringBuilder();
            Node temp = front;
            while (temp != null) {
                sb.append(temp.data);
                if (temp.next != null) sb.append(" -> ");
                temp = temp.next;
            }
            return sb.toString();
        }
    }

    // Main method
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Queue queue = new Queue();

        int choice = 0;  // FIX: initialize choice

        do {
            System.out.println("\n--- Ticket Counter Menu ---");
            System.out.println("1. Add Customer");
            System.out.println("2. Serve Customer");
            System.out.println("3. Show Queue");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");

            if (!sc.hasNextInt()) {
                System.out.println("Invalid input! Enter a number.");
                sc.next();
                continue;
            }

            choice = sc.nextInt();
            sc.nextLine(); // consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter customer name: ");
                    String name = sc.nextLine();
                    queue.enqueue(name);
                    System.out.println(name + " added to the queue.");
                    break;

                case 2:
                    if (queue.isEmpty()) {
                        System.out.println("No customers to serve.");
                    } else {
                        System.out.println("Served: " + queue.dequeue());
                    }
                    break;

                case 3:
                    if (queue.isEmpty()) {
                        System.out.println("Queue is empty.");
                    } else {
                        System.out.println("Waiting: " + queue.toString());
                    }
                    break;

                case 4:
                    System.out.println("Exiting Ticket Counter...");
                    break;

                default:
                    System.out.println("Invalid choice, try again.");
            }

        } while (choice != 4);

        sc.close();
    }
}

```

## Output:

<img width="623" height="508" alt="image" src="https://github.com/user-attachments/assets/11914999-806d-40e0-a1f6-dc1a1202292d" />


## Result:
Thus, the program successfully simulates a ticket counter queue where customers are served in FIFO order using a linked list-based queue implementation.
