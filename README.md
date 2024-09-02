#include <string>
#include <iostream>
#include <cstdio> 
#include <cstdlib> 
#include <direct.h>
#include <windows.h>

    void displayFiles(){
        system("dir");   
        system("pause"); 
    }


void createDirectory(){
            std::cout << "\nEnter The Directory Name: ";
            std::string dirName;
            std::cin >> dirName;

        if(_mkdir(dirName.c_str()) == 0){
            std::cout << "\nDirectory " << dirName << " Successfully Created\n";
        }else {
            std::cout << "\nFailed To Created Directory " << dirName << "\n";
        }
    system("pause");
}


    void changeDirectory(){
            char currentDir[FILENAME_MAX];
                _getcwd(currentDir, sizeof(currentDir));
                std::cout << "\nCurrent Directory: " << currentDir << "\n";



    std::cout << "1. Step By Step Backward\n";
    std::cout << "2. GOTO Root Directory\n";
    std::cout << "3. Forward Directory\n";
    std::cout << "Enter The Number: ";
    int choice;
    std::cin >> choice;

        if(choice == 1) {
            _chdir("..");
        } else if (choice == 2){
            _chdir("\\");
        } else if (choice == 3) {
                std::cout << "Please enter the directory name: ";
                std::string dirName;
                std::cin >> dirName;
                _chdir(dirName.c_str());
        }
    _getcwd(currentDir, sizeof(currentDir));
                std::cout << "Current Directory: " << currentDir << '\n';
    system("pause");
}



int main(){
    int choice;

        do{
            system("cls");
                std::cout << "1. To Display List Of Files\n";
                std::cout << "2. To Create New Directory\n";
                std::cout << "3. To Change The Working Directory\n";
                std::cout << "4. Exit\n";
                std::cout << "Enter A Number: ";
                std::cin >> choice;


        switch (choice) {
            case 1:
                displayFiles();
                break;
            case 2:
                createDirectory();
                break;
            case 3:
                changeDirectory();
                break;
            case 4:
                std::cout << "Exiting...\n";
                break;
            default:
                std::cout << "Invalid Option! Please Try Again.\n";
            system("pause");
                break;
            }
        }while (choice != 4);
   
 return 0;     
}
