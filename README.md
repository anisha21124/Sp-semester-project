This Is my semister project on C code done by using codeblock.idm. 
This project consits of a code written by myself (Fariha Jahan Anisha) on Parking management system. Here is the code that I used for making this project:



#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <string.h>

#define MAX_HISTORY_SIZE 100

// Structure to represent vehicle entry
struct Entry {
    int vehicleType;
    time_t entryTime;
};

struct Entry history[MAX_HISTORY_SIZE];
int historyCount = 0;


int not = 0, noc = 0, nor = 0, nob = 0, amount = 0, count = 0;


void Truck();
void Car();
void Rikshaw();
void Bike();
void status();
void displayHistory();
void clearData();
int menu();

int main() {
    while (1) {
        switch (menu()) {
            case 1:
                Truck();
                break;
            case 2:
                Car();
                break;
            case 3:
                Rikshaw();
                break;
            case 4:
                Bike();
                break;
            case 5:
                status();
                break;
            case 6:
                displayHistory();
                break;
            case 7:
                clearData();
                break;
            case 8:
                exit(0);
            default:
                printf("\nEnter correct option\n");
        }
    }
    return 0;
}

// Function to record truck entry
void Truck() {
    printf("\nTruck Entry Successfully\n");
    history[historyCount].vehicleType = 1;
    time(&history[historyCount].entryTime);
    historyCount++;

    // Update counts and amount
    not++;
    amount += 200;
    count++;
}

// Function to record car entry
void Car() {
    printf("\nCar Entry Successfully\n");
    history[historyCount].vehicleType = 2;
    time(&history[historyCount].entryTime);
    historyCount++;

    // Update counts and amount
    noc++;
    amount += 100;
    count++;
}

// Function to record rikshaw entry
void Rikshaw() {
    printf("\nRikshaw Entry Successfully\n");
    history[historyCount].vehicleType = 3;
    time(&history[historyCount].entryTime);
    historyCount++;

    // Update counts and amount
    nor++;
    amount += 70;
    count++;
}

// Function to record bike entry
void Bike() {
    printf("\nBike Entry Successfully\n");
    history[historyCount].vehicleType = 4;
    time(&history[historyCount].entryTime);
    historyCount++;

    // Update counts and amount
    nob++;
    amount += 50;
    count++;
}

// Function to display current status
void status() {
    printf("\n--- Parking Status ---\n");
    printf("Number of Truck: %d\n", not);
    printf("Number of Car: %d\n", noc);
    printf("Number of Rikshaw: %d\n", nor);
    printf("Number of Bike: %d\n", nob);
    printf("Total Vehicles: %d\n", count);
    printf("Total Amount: %d\n", amount);
}

// Function to display vehicle entry history
void displayHistory() {
    printf("\n--- Vehicle Entry History ---\n");
    for (int i = 0; i < historyCount; i++) {
        printf("Vehicle Type: ");
        switch (history[i].vehicleType) {
            case 1:
                printf("Truck");
                break;
            case 2:
                printf("Car");
                break;
            case 3:
                printf("Rikshaw");
                break;
            case 4:
                printf("Bike");
                break;
            default:
                printf("Unknown");
        }
        printf("\tEntry Time: %s", ctime(&history[i].entryTime));
    }
}

// Function to clear all data
void clearData() {
    not = 0;
    noc = 0;
    nor = 0;
    nob = 0;
    amount = 0;
    count = 0;
    historyCount = 0;
    printf("\nData Cleared Successfully\n");
}

// Function to display menu and get user input
int menu() {
    int choice;
    printf("\n1. Enter Truck\n");
    printf("2. Enter Car\n");
    printf("3. Enter Rikshaw\n");
    printf("4. Enter Bike\n");
    printf("5. Check Status\n");
    printf("6. Display History\n");
    printf("7. Clear Data\n");
    printf("8. Exit\n");
    printf("Enter your choice: ");
    scanf("%d", &choice);
    return choice;
}
