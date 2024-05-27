# codealpha
# CodeAlpha-
*program details :* 
 this program is a simple task manager. It allows users to add tasks, mark tasks as completed, and view all tasks they've added.

1. Including Libraries: 
   - #include <iostream>: This includes a library that allows you to do input and output (like printing to the screen).
   - #include <vector>: This includes a library that provides a dynamic array structure called a vector.
   - #include <string>: This includes a library for working with strings.

2. Task Class: 
   - Task is a blueprint for creating objects that represent tasks.
   - Each task has a description (what the task is about) and a completion status (whether the task is done or not).
   - There are functions inside the Task class to set the task as completed, check if it's completed, and get its description.

3. Main Function: 
   - This is where the program starts running.
   - It creates an empty list called taskList to store tasks.
   - It declares a variable called userChoice to store the user's input.
   - Then, it enters a loop that keeps running until the user chooses to exit.

4. User Interaction:
   - Inside the loop, the program shows a menu with four options:
     1. Add a task
     2. Mark a task as completed
     3. View tasks
     4. Exit the program
   - It asks the user to choose an option and stores their choice in the userChoice variable.

5. Handling User Choices:
   - If the user chooses to add a task (option 1), the program asks for a description and adds a new task with that description to the taskList.
   - If the user chooses to mark a task as completed (option 2), the program asks for the index of the task and marks it as completed if the index is valid.
   - If the user chooses to view tasks (option 3), the program shows all tasks in the taskList along with their descriptions and completion status.
   - If the user chooses to exit (option 4), the program ends.

6. Looping: 
   - After handling the user's choice, the program goes back to the start of the loop and repeats the process, asking the user for another choice.

7. Exiting the Program: 
   - If the user chooses to exit the program (option 4), the loop breaks, and the program ends.



#include <iostream>
#include <vector>
#include <string>

// A class representing a task with a description and a completed status
class Task
{
public:
    Task(const std::string &description) : description(description), completed(false) {}

    void markCompleted()
    {
        completed = true;
    }

    bool isCompleted() const
    {
        return completed;
    }

    const std::string &getDescription() const
    {
        return description;
    }

private:
    std::string description;
    bool completed;
};

int main()
{
    // A list of tasks
    std::vector<Task> taskList;

    // The user's choice
    int userChoice;

    // Prompt the user for input until they choose to exit
    do
    {
        std::cout << "1. Add task\n2. Mark task as completed\n3. View tasks\n4. Exit\n";
        std::cin >> userChoice;

        switch (userChoice)
        {
        case 1:
        {
            std::string description;
            std::cout << "Enter task description: ";
            std::cin.ignore();
            std::getline(std::cin, description);
            taskList.push_back(Task(description));
            break;
        }
        case 2:
        {
            int index;
            std::cout << "Enter task index: ";
            std::cin >> index;
            if (index >= 0 && index < taskList.size())
            {
                taskList[index].markCompleted();
            }
            else
            {
                std::cout << "Invalid task index.\n";
            }
            break;
        }
        case 3:
        {
            std::cout << "Current tasks:\n";
            for (const Task &task : taskList)
            {
                std::cout << std::to_string(&task - &taskList[0] + 1) << ". " << task.getDescription();
                if (task.isCompleted())
                {
                    std::cout << " (completed)\n";
                }
                else
                {
                    std::cout << "\n";
                }
            }
            break;
        }
        case 4:
            return 0;
        default:
            std::cout << "Invalid choice.\n";
        }
    } while (true);

    return 0;
}
