#include <iostream>
#include <filesystem>
#include <vector>
#include <regex>
#in#include <iostream>
#include <filesystem>
#include <vector>
#include <regex>
#include <string>

namespace fs = std::filesystem;

void displayMainMenu();
void handleMainMenuSelection(int choice);
void listFilesMenu();
void listAllFiles();
void listFilesByExtension();
void listFilesByPattern();
void createDirectory();
void changeDirectory();
void displayDirectoryMenu();
void handleDirectorySelection(int choice);
void exitProgram();

int main() {
    int choice;
    do {
        displayMainMenu();
        std::cin >> choice;
        handleMainMenuSelection(choice);
    } while (choice != 4); // 4 is the exit option
    return 0;
}

void displayMainMenu() {
    std::cout << "\nDirectory Management System\n";
    std::cout << "1. List files in the current directory\n";
    std::cout << "2. Create a new directory\n";
    std::cout << "3. Change the working directory\n";
    std::cout << "4. Exit the program\n";
    std::cout << "Enter your choice: ";
}

void handleMainMenuSelection(int choice) {
    switch (choice) {
        case 1:
            listFilesMenu();
            break;
        case 2:
            createDirectory();
            break;
        case 3:
            changeDirectory();
            break;
        case 4:
            exitProgram();
            break;
        default:
            std::cerr << "Invalid choice. Please try again.\n";
    }
}

void listFilesMenu() {
    int choice;
    std::cout << "\nList Files Menu\n";
    std::cout << "1. List all files in the current directory\n";
    std::cout << "2. List files based on a specific extension\n";
    std::cout << "3. List files based on a pattern\n";
    std::cout << "Enter your choice: ";
    std::cin >> choice;

        
