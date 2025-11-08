# Array-Lab
New Repository for Array Lab
# Non-Duplicated-Integer-Array-Operations

// Name: Alex Griggs
// Course: CISC 192 - C++ Programming
// Date: 11/02/2025
// Assignment: Non-Duplicated Integer Array Operations

```
#include <iostream>
#include <array>

using namespace std;

int main() {
    const int n = 5;
	array<int, n> numbers; //create an array of size n
    int choice;

    while (true) { // Main loop for repeated operations
        //Input numbers
        while (true) {
            cout << "\nPlease enter " << n << " integers: ";
            for (int i = 0; i < n; i++) {
                cin >> numbers[i];
            }

            // Check for duplicates
            int i, j;
            for (i = 0; i < n - 1; i++) {
                for (j = i + 1; j < n; j++) {
                    if (numbers[i] == numbers[j]) break;
                }
                if (j < n) break; // duplicate found
            }

            if (i == n - 1) break; // no duplicates found
            cout << "Duplicates detected. Please enter the array again.\n";
        }

        //Menu
        while (true) {
            cout << "\nChoose an operation:\n";
            cout << "1) Sort ascending\n";
            cout << "2) Sort descending\n";
            cout << "3) Find maximum\n";
            cout << "4) Enter new numbers\n";
            cout << "5) Exit\n";
            cin >> choice;

            if (choice == 5) {
                cout << "Exiting program.\n";
                return 0;
            }
            else if (choice == 4) {
                break; // break to outer loop to enter new numbers
            }

            switch (choice) {
            case 1:
                // Sort ascending
                for (int i = 0; i < n - 1; i++)
                    for (int j = 0; j < n - i - 1; j++)
                        if (numbers[j] > numbers[j + 1]) {
                            int temp = numbers[j];
                            numbers[j] = numbers[j + 1];
                            numbers[j + 1] = temp;
                        }
                cout << "Array sorted ascending: ";
                for (int i = 0; i < n; i++) cout << numbers[i] << " ";
                cout << endl;
                break;

            case 2:
                // Sort descending (bubble sort)
                for (int i = 0; i < n - 1; i++)
                    for (int j = 0; j < n - i - 1; j++)
                        if (numbers[j] < numbers[j + 1]) {
                            int temp = numbers[j];
                            numbers[j] = numbers[j + 1];
                            numbers[j + 1] = temp;
                        }
                cout << "Array sorted descending: ";
                for (int i = 0; i < n; i++) cout << numbers[i] << " ";
                cout << endl;
                break;

            case 3: {
                // Find maximum
                int maxVal = numbers[0];
                for (int i = 1; i < n; i++)
                    if (numbers[i] > maxVal)
                        maxVal = numbers[i];
                cout << "Maximum value: " << maxVal << endl;
                break;
            }

            default:
                cout << "Invalid choice. Try again.\n";
            }
        }
    }

    return 0;
}
```
