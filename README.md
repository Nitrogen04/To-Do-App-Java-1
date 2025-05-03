import java.util.ArrayList;
import java.util.Scanner;

public class ToDoApp {
    static ArrayList<String> toDoList = new ArrayList<>();
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int choice;

        do {
            System.out.println("To-Do List Application");
            System.out.println("1. Add Task");
            System.out.println("2. View Tasks");
            System.out.println("3. Remove Task");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter task: ");
                    String task = scanner.nextLine();
                    addTask(task);
                    break;
                case 2:
                    viewTasks();
                    break;
                case 3:
                    System.out.print("Enter task number to remove: ");
                    int taskNumber = scanner.nextInt();
                    removeTask(taskNumber);
                    break;
                case 4:
                    System.out.println("Exiting application...");
                    break;
                default:
                    System.out.println("Invalid choice, try again.");
            }
        } while (choice != 4);
        
        scanner.close();
    }

    private static void addTask(String task) {
        toDoList.add(task);
        System.out.println("Task added!");
    }

    private static void viewTasks() {
        if (toDoList.isEmpty()) {
            System.out.println("No tasks available.");
        } else {
            System.out.println("To-Do List:");
            for (int i = 0; i < toDoList.size(); i++) {
                System.out.println((i + 1) + ". " + toDoList.get(i));
            }
        }
    }

    private static void removeTask(int taskNumber) {
        if (taskNumber > 0 && taskNumber <= toDoList.size()) {
            toDoList.remove(taskNumber - 1);
            System.out.println("Task removed!");
        } else {
            System.out.println("Invalid task number.");
        }
    }
}
