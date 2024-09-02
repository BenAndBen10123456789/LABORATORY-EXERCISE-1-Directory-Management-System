#include <iostream>
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

  switch (choice) {
        case 1:
            listAllFiles();
            break;
        case 2:
            listFilesByExtension();
            break;
        case 3:
            listFilesByPattern();
            break;
        default:
            std::cerr << "Invalid choice. Returning to main menu.\n";
    }
}

void listAllFiles() {
    std::cout << "\nFiles in the current directory:\n";
    for (const auto& entry : fs::directory_iterator(fs::current_path())) {
        std::cout << entry.path().filename().string() << std::endl;
    }
}

void listFilesByExtension() {
    std::string extension;
    std::cout << "Enter the file extension (e.g., .txt): ";
    std::cin >> extension;

  std::cout << "\nFiles with extension '" << extension << "':\n";
    for (const auto& entry : fs::directory_iterator(fs::current_path())) {
        if (entry.path().extension() == extension) {
            std::cout << entry.path().filename().string() << std::endl;
        }
    }
}

void listFilesByPattern() {
    std::string pattern;
    std::cout << "Enter the pattern (e.g., moha*.*): ";
    std::cin >> pattern;

pattern (simple approach)
    std::string regex_pattern = std::regex_replace(pattern, std::regex("\\*"), ".*");

 std::cout << "\nFiles matching pattern '" << pattern << "':\n";
    for (const auto& entry : fs::directory_iterator(fs::current_path())) {
        if (std::regex_match(entry.path().filename().string(), std::regex(regex_pattern))) {
            std::cout << entry.path().filename().string() << std::endl;
        }
    }
}

void createDirectory() {
    std::string dirName;
    std::cout << "Enter the name of the directory to create: ";
    std::cin >> dirName;

  fs::path newDir = fs::current_path() / dirName; // Create in the current directory
    if (fs::create_directory(newDir)) {
        std::cout << "Directory '" << dirName << "' created successfully.\n";
    } else {
        std::cerr << "Error: Directory '" << dirName << "' could not be created.\n";
    }
}

void changeDirectory() {
    int choice;
    displayDirectoryMenu();
    std::cin >> choice;
    handleDirectorySelection(choice);
}

void displayDirectoryMenu() {
    std::cout << "\nChange Directory Menu\n";
    std::cout << "1. Move one step back (to the parent directory)\n";
    std::cout << "2. Move to the root directory\n";
    std::cout << "3. Move to a specific directory\n";
    std::cout << "Enter your choice: ";
}

void handleDirectorySelection(int choice) {
    switch (choice) {
        case 1:
            fs::current_path(fs::current_path().parent_path());
            std::cout << "Moved to parent directory: " << fs::cur(std::regex_match(entry.path().filename().string(), std::regex(regex_pattern))) {
            std::cout << entry.path().filename().string() << std::endl;
        }
    }
}

void createDirectory() {
    std::string dirName;
    std::cout << "Enter the name of the directory to create: ";
    std::cin >> dirName;

fs::path newDir = fs::current_path() / dirName; // Create in the current directory
    if (fs::create_directory(newDir)) {
        std::cout << "Directory '" << dirName << "' created successfully.\n";
    } else {
        std::cerr << "Error: Directory '" << dirName << "' could not be created.\n";
    }
}

void changeDirectory() {
    int choice;
    displayDirectoryMenu();
    std::cin >> choice;
    handleDirectorySelection(choice);
}

void displayDirectoryMenu() {
    std::cout << "\nChange Directory Menu\n";
    std::cout << "1. Move one step back (to the parent directory)\n";
    std::cout << "2. Move to the root directory\n";
    std::cout << "3. Move to a specific directory\n";
    std::cout << "Enter your choice: ";
}

void handleDirectorySelection(int choice) {
    switch (choice) {
        case 1:
            fs::current_path(fs::current_path().parent_path());
            std::cout << "Moved to parent directory: " << fs::current_path()rent_path() << "\n";
            break;
        case 2:
            fs::current_path(fs::path("/"));
            std::cout << "Moved to root directory: " << fs::current_path() << "\n";
            break;
        case 3: {
            std::string dirName;
            std::cout << "Enter the name of the directory to move to: ";
            std::cin >> dirName;
            if (fs::exists(dirName) && fs::is_directory(dirName)) {
                fs::current_path(dirName);
                std::cout << "Moved to directory: " << fs::current_path() << "\n";
            } else {
                std::cerr << "Error: Directory '" << dirName << "' does not exis#include <iostream>
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

    switch (choice) {
        case 1:
            listAllFiles();
            break;
        case 2:
            listFilesByExtension();
            break;
        case 3:
            listFilesByPattern();
            break;
        default:
            std::cerr << "Invalid choice. Returning to main menu.\n";
    }
}

void listAllFiles() {
    std::cout << "\nFiles in the current directory:\n";
    for (const auto& entry : fs::directory_iterator(fs::current_path())) {
        std::cout << entry.path().filename().string() << std::endl;
    }
}

void listFilesByExtension() {
    std::string extension;
    std::cout << "Enter the file extension (e.g., .txt): ";
    std::cin >> extension;

std::cout << "\nFiles with extension '" << extension << "':\n";
    for (const auto& entry : fs::directory_iterator(fs::current_path())) {
        if (entry.path().extension() == extension) {
            std::cout << entry.path().filename().string() << std::endl;
        }
    }
}

void listFilesByPattern() {
    std::string pattern;
    std::cout << "Enter the pattern (e.g., moha*.*): ";
    std::cin >> pattern;

 pattern (simple approach)
    std::string regex_pattern = std::regex_replace(pattern, std::regex("\\*"), ".*");

std::cout << "\nFiles matching pattern '" << pattern << "':\n";
    for (const auto& entry : fs::directory_iterator(fs::current_path())) {
        if (std::regex_match(entry.path().filename().string(), std::regex(regex_pattern))) {
            std::cout << entry.path().filename().string() << std::endl;
        }
    }
}

void createDirectory() {
    std::string dirName;
    std::cout << "Enter the name of the directory to create: ";
    std::cin >> dirName;

fs::path newDir = fs::current_path() / dirName; // Create in the current directory
    if (fs::create_directory(newDir)) {
        std::cout << "Directory '" << dirName << "' created successfully.\n";
    } else {
        std::cerr << "Error: Directory '" << dirName << "' could not be created.\n";
    }
}

void changeDirectory() {
    int choice;
    displayDirectoryMenu();
    std::cin >> choice;
    handleDirectorySelection(choice);
}

void displayDirectoryMenu() {
    std::cout << "\nChange Directory Menu\n";
    std::cout << "1. Move one step back (to the parent directory)\n";
    std::cout << "2. Move to the root directory\n";
    std::cout << "3. Move to a specific directory\n";
    std::cout << "Enter your choice: ";
}

void handleDirectorySelection(int choice) {
    switch (choice) {
        case 1:
            fs::current_path(fs::current_path().parent_path());
            std::cout << "Moved to parent directory: " << fs::cur(std::regex_match(entry.path().filename().string(), std::regex(regex_pattern))) {
            std::cout << entry.path().filename().string() << std::endl;
        }
    }
}

void createDirectory() {
    std::string dirName;
    std::cout << "Enter the name of the directory to create: ";
    std::cin >> dirName;

  fs::path newDir = fs::current_path() / dirName; // Create in the current directory
    if (fs::create_directory(newDir)) {
        std::cout << "Directory '" << dirName << "' created successfully.\n";
    } else {
        std::cerr << "Error: Directory '" << dirName << "' could not be created.\n";
    }
}

void changeDirectory() {
    int choice;
    displayDirectoryMenu();
    std::cin >> choice;
    handleDirectorySelection(choice);
}

void displayDirectoryMenu() {
    std::cout << "\nChange Directory Menu\n";
    std::cout << "1. Move one step back (to the parent directory)\n";
    std::cout << "2. Move to the root directory\n";
    std::cout << "3. Move to a specific directory\n";
    std::cout << "Enter your choice: ";
}

void handleDirectorySelection(int choice) {
    switch (choice) {
        case 1:
            fs::current_path(fs::current_path().parent_path());
            std::cout << "Moved to parent directory: " << fs::current_path()rent_path() << "\n";
            break;
        case 2:
            fs::current_path(fs::path("/"));
            std::cout << "Moved to root directory: " << fs::current_path() << "\n";
            break;
        case 3: {
            std::string dirName;
            std::cout << "Enter the name of the directory to move to: ";
            std::cin >> dirName;
            if (fs::exists(dirName) && fs::is_directory(dirName)) {
                fs::current_path(dirName);
                std::cout << "Moved to directory: " << fs::current_path() << "\n";
            } else {
                std::cerr << "Error: Directory '" << dirName << "' does not exist.\n";
            }
            break;
        }
        default:
            std::cerr << "Invalid choice. Returning to main menu.\n";
    }
}

void exitProgram() {
    std::cout << "Exiting the program. Goodbye!\n";
}
t.\n";
            }
    #include <iostream>
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

  switch (choice) {
        case 1:
            listAllFiles();
            break;
        case 2:
            listFilesByExtension();
            break;
        case 3:
            listFilesByPattern();
            break;
        default:
            std::cerr << "Invalid choice. Returning to main menu.\n";
    }
}

void listAllFiles() {
    std::cout << "\nFiles in the current directory:\n";
    for (const auto& entry : fs::directory_iterator(fs::current_path())) {
        std::cout << entry.path().filename().string() << std::endl;
    }
}

void listFilesByExtension() {
    std::string extension;
    std::cout << "Enter the file extension (e.g., .txt): ";
    std::cin >> extension;

  std::cout << "\nFiles with extension '" << extension << "':\n";
    for (const auto& entry : fs::directory_iterator(fs::current_path())) {
        if (entry.path().extension() == extension) {
            std::cout << entry.path().filename().string() << std::endl;
        }
    }
}

void listFilesByPattern() {
    std::string pattern;
    std::cout << "Enter the pattern (e.g., moha*.*): ";
    std::cin >> pattern;

pattern (simple approach)
    std::string regex_pattern = std::regex_replace(pattern, std::regex("\\*"), ".*");

 std::cout << "\nFiles matching pattern '" << pattern << "':\n";
    for (const auto& entry : fs::directory_iterator(fs::current_path())) {
        if (std::regex_match(entry.path().filename().string(), std::regex(regex_pattern))) {
            std::cout << entry.path().filename().string() << std::endl;
        }
    }
}

void createDirectory() {
    std::string dirName;
    std::cout << "Enter the name of the directory to create: ";
    std::cin >> dirName;

  fs::path newDir = fs::current_path() / dirName; // Create in the current directory
    if (fs::create_directory(newDir)) {
        std::cout << "Directory '" << dirName << "' created successfully.\n";
    } else {
        std::cerr << "Error: Directory '" << dirName << "' could not be created.\n";
    }
}

void changeDirectory() {
    int choice;
    displayDirectoryMenu();
    std::cin >> choice;
    handleDirectorySelection(choice);
}

void displayDirectoryMenu() {
    std::cout << "\nChange Directory Menu\n";
    std::cout << "1. Move one step back (to the parent directory)\n";
    std::cout << "2. Move to the root directory\n";
    std::cout << "3. Move to a specific directory\n";
    std::cout << "Enter your choice: ";
}

void handleDirectorySelection(int choice) {
    switch (choice) {
        case 1:
            fs::current_path(fs::current_path().parent_path());
            std::cout << "Moved to parent directory: " << fs::cur(std::regex_match(entry.path().filename().string(), std::regex(regex_pattern))) {
            std::cout << entry.path().filename().string() << std::endl;
        }
    }
}

void createDirectory() {
    std::string dirName;
    std::cout << "Enter the name of the directory to create: ";
    std::cin >> dirName;

fs::path newDir = fs::current_path() / dirName; // Create in the current directory
    if (fs::create_directory(newDir)) {
        std::cout << "Directory '" << dirName << "' created successfully.\n";
    } else {
        std::cerr << "Error: Directory '" << dirName << "' could not be created.\n";
    }
}

void changeDirectory() {
    int choice;
    displayDirectoryMenu();
    std::cin >> choice;
    handleDirectorySelection(choice);
}

void displayDirectoryMenu() {
    std::cout << "\nChange Directory Menu\n";
    std::cout << "1. Move one step back (to the parent directory)\n";
    std::cout << "2. Move to the root directory\n";
    std::cout << "3. Move to a specific directory\n";
    std::cout << "Enter your choice: ";
}

void handleDirectorySelection(int choice) {
    switch (choice) {
        case 1:
            fs::current_path(fs::current_path().parent_path());
            std::cout << "Moved to parent directory: " << fs::current_path()rent_path() << "\n";
            break;
        case 2:
            fs::current_path(fs::path("/"));
            std::cout << "Moved to root directory: " << fs::current_path() << "\n";
            break;
        case 3: {
            std::string dirName;
            std::cout << "Enter the name of the directory to move to: ";
            std::cin >> dirName;
            if (fs::exists(dirName) && fs::is_directory(dirName)) {
                fs::current_path(dirName);
                std::cout << "Moved to directory: " << fs::current_path() << "\n";
            } else {
                std::cerr << "Error: Directory '" << dirName << "' does not exis#include <iostream>
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

    switch (choice) {
        case 1:
            listAllFiles();
            break;
        case 2:
            listFilesByExtension();
            break;
        case 3:
            listFilesByPattern();
            break;
        default:
            std::cerr << "Invalid choice. Returning to main menu.\n";
    }
}

void listAllFiles() {
    std::cout << "\nFiles in the current directory:\n";
    for (const auto& entry : fs::directory_iterator(fs::current_path())) {
        std::cout << entry.path().filename().string() << std::endl;
    }
}

void listFilesByExtension() {
    std::string extension;
    std::cout << "Enter the file extension (e.g., .txt): ";
    std::cin >> extension;

std::cout << "\nFiles with extension '" << extension << "':\n";
    for (const auto& entry : fs::directory_iterator(fs::current_path())) {
        if (entry.path().extension() == extension) {
            std::cout << entry.path().filename().string() << std::endl;
        }
    }
}

void listFilesByPattern() {
    std::string pattern;
    std::cout << "Enter the pattern (e.g., moha*.*): ";
    std::cin >> pattern;

 pattern (simple approach)
    std::string regex_pattern = std::regex_replace(pattern, std::regex("\\*"), ".*");

std::cout << "\nFiles matching pattern '" << pattern << "':\n";
    for (const auto& entry : fs::directory_iterator(fs::current_path())) {
        if (std::regex_match(entry.path().filename().string(), std::regex(regex_pattern))) {
            std::cout << entry.path().filename().string() << std::endl;
        }
    }
}

void createDirectory() {
    std::string dirName;
    std::cout << "Enter the name of the directory to create: ";
    std::cin >> dirName;

fs::path newDir = fs::current_path() / dirName; // Create in the current directory
    if (fs::create_directory(newDir)) {
        std::cout << "Directory '" << dirName << "' created successfully.\n";
    } else {
        std::cerr << "Error: Directory '" << dirName << "' could not be created.\n";
    }
}

void changeDirectory() {
    int choice;
    displayDirectoryMenu();
    std::cin >> choice;
    handleDirectorySelection(choice);
}

void displayDirectoryMenu() {
    std::cout << "\nChange Directory Menu\n";
    std::cout << "1. Move one step back (to the parent directory)\n";
    std::cout << "2. Move to the root directory\n";
    std::cout << "3. Move to a specific directory\n";
    std::cout << "Enter your choice: ";
}

void handleDirectorySelection(int choice) {
    switch (choice) {
        case 1:
            fs::current_path(fs::current_path().parent_path());
            std::cout << "Moved to parent directory: " << fs::cur(std::regex_match(entry.path().filename().string(), std::regex(regex_pattern))) {
            std::cout << entry.path().filename().string() << std::endl;
        }
    }
}

void createDirectory() {
    std::string dirName;
    std::cout << "Enter the name of the directory to create: ";
    std::cin >> dirName;

  fs::path newDir = fs::current_path() / dirName; // Create in the current directory
    if (fs::create_directory(newDir)) {
        std::cout << "Directory '" << dirName << "' created successfully.\n";
    } else {
        std::cerr << "Error: Directory '" << dirName << "' could not be created.\n";
    }
}

void changeDirectory() {
    int choice;
    displayDirectoryMenu();
    std::cin >> choice;
    handleDirectorySelection(choice);
}

void displayDirectoryMenu() {
    std::cout << "\nChange Directory Menu\n";
    std::cout << "1. Move one step back (to the parent directory)\n";
    std::cout << "2. Move to the root directory\n";
    std::cout << "3. Move to a specific directory\n";
    std::cout << "Enter your choice: ";
}

void handleDirectorySelection(int choice) {
    switch (choice) {
        case 1:
            fs::current_path(fs::current_path().parent_path());
            std::cout << "Moved to parent directory: " << fs::current_path()rent_path() << "\n";
            break;
        case 2:
            fs::current_path(fs::path("/"));
            std::cout << "Moved to root directory: " << fs::current_path() << "\n";
            break;
        case 3: {
            std::string dirName;
            std::cout << "Enter the name of the directory to move to: ";
            std::cin >> dirName;
            if (fs::exists(dirName) && fs::is_directory(dirName)) {
                fs::current_path(dirName);
                std::cout << "Moved to directory: " << fs::current_path() << "\n";
            } else {
                std::cerr << "Error: Directory '" << dirName << "' does not exist.\n";
            }
            break;
        }
        default:
            std::cerr << "Invalid choice. Returning to main menu.\n";
    }
}

void exitProgram() {
    std::cout << "Exiting the program. Goodbye!\n";
}
t.\n";
            }
            break;
        }
        default:
            std::cerr << "Invalid choice. Returning to main menu.\n";
    }
}

void exitProgram() {
    std::cout << "Exiting the program. Goodbye!\n";
}
        break;
        }
        default:
            std::cerr << "Invalid choice. Returning to main menu.\n";
    }
}

void exitProgram() {
    std::cout << "Exiting the program. Goodbye!\n";
}
