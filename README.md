\#include <stdio.h>
#include <stdlib.h>

int password = 1234;  
int Min = 5;    
float total_amount = 0.0;  

void displayMenu();
void adminMode();

int main() {
    int choice;

    while (1) {
        displayMenu();
        printf("Enter your choice: ");
        scanf("%d", &choice);

        if (choice == 1) {
            purchaseItem();
        } else if (choice == 2) {
            adminMode();
        } else if (choice == 3) {
            exit(0);
        } else {
            printf("Invalid choice. Please try again.\n");
        }
    }

    return 0;
}

void displayMenu() {
    printf("\nVending Machine Simulator Menu:\n");
    printf("1. Purchase Item\n");
    printf("2. Admin Mode\n");
    printf("3. Exit\n");
}


void adminMode() {
    int admin_pass;
    printf("Enter the admin password: ");
    scanf("%d", &admin_pass);

    if (admin_pass != password) {
        printf("Incorrect admin password.\n");
        return;
    }

    int admin_choice;
    while (1) {
        printf("\nAdmin Mode Menu:\n");
        printf("1. Replenish Items\n");
        printf("2. Change Item Prices\n");
        printf("3. Display Total Sale\n");
        printf("4. Display Item Availability\n");
        printf("0. Exit Admin Mode\n");

        printf("Enter your choice: ");
        scanf("%d", &admin_choice);

    }
}

