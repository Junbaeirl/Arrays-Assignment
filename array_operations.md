Name: Ian Vang
Course: CISC 192 - C++ Programming
Date: 11/2/2025
Assignment: Non-Duplicated Integer Array Operations
```
#include <iostream>
#include <array>

int main() {
    // Our constant integer which is used to determine how many integers we will ask from the user for sorting.
    // This "N" can be set to any number to allow for a higher or lower quantity of integers to be sorted.
    const int N = 5;
    // This creates our array with "N" as our size that will hold integers.
    std::array<int, N> numbers{};
    int input;
    // Asks for a input of "N" which is 5, unique integers.
    std::cout << "Enter " << N << " unique integers:\n";

    for (int i = 0; i < N; ++i) {
        bool duplicate;
        do {
            duplicate = false;
            std::cout << "Number " << i + 1 << ": ";
            std::cin >> input;
            // Reads input form the user after prompting for "N" unique integers.
            // Also returns a fail if the user inputs anything different from a unique integer.

            // Double checks for duplicates and returns a prompt when a duplicate integer is found.
            for (int j = 0; j < i; ++j) {
                if (numbers[j] == input) {
                    std::cout << "No duplicate numbers! Please enter a different number.\n";
                    duplicate = true;
                    break;
                }
            }
        } while (duplicate);
        // Stores the input after confirming there are no duplicates.
        numbers[i] = input;
    }
// Proceed to ask the user how they would like to categorize their integers, Using a numerical value for options 1-3.
    char choice;
    std::cout << "\nChoose an operation:\n";
    std::cout << "(1) Sort ascending\n";
    std::cout << "(2) Sort descending\n";
    std::cout << "(3) Find maximum number\n";
    std::cout << "Enter choice: ";
    // this string reads for input of 1,2 or 3 for the above options
    std::cin >> choice;
// Switch statements are used to determine how the array will be organized and displayed to the user.
    switch (choice) {
        case '1': {
            // Sort ascending
            for (int i = 0; i < N - 1; ++i) {
                for (int j = 0; j < N - i - 1; ++j) {
                    if (numbers[j] > numbers[j + 1]) {
                        int temp = numbers[j];
                        numbers[j] = numbers[j + 1];
                        numbers[j + 1] = temp;
                    }
                }
            }

            std::cout << "Array sorted in ascending order: ";
            for (int n : numbers) std::cout << n << " ";
            std::cout << "\n";
            break;
        }

        case '2': {
            // Sort descending
            for (int i = 0; i < N - 1; ++i) {
                for (int j = 0; j < N - i - 1; ++j) {
                    if (numbers[j] < numbers[j + 1]) {
                        int temp = numbers[j];
                        numbers[j] = numbers[j + 1];
                        numbers[j + 1] = temp;
                    }
                }
            }

            std::cout << "Array sorted in descending order: ";
            for (int n : numbers) std::cout << n << " ";
            std::cout << "\n";
            break;
        }

        case '3': {
            // Determines the maximum number of the integers inputted.
            int max = numbers[0];
            for (int i = 1; i < N; ++i) { // This checks the array for any other bigger numbers and adds it to "max" until all integers have been checked.
                if (numbers[i] > max)
                    max = numbers[i];
            }
            // "max" will containt the largest "N" integer and display it as the maximum.
            std::cout << "Maximum number: " << max << "\n";
            break;
        }

            // Displays an error if the user inputs anything other than the allowed options.
        default:
            std::cout << "Invalid choice.\n";
            break;
    }
// Return 0 if successful.
    return 0;
}
```