
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

int password = 1234;  
const int Min = 5;    
double total_amount = 0.0;  


float itemAPrice = 1.0;
float itemBPrice = 1.5;
float itemCPrice = 2.0;
int itemAQuantity = 10;
int itemBQuantity = 10;
int itemCQuantity = 10;


void displayMenu();
void purchaseItem();
void adminMode();
void replenishItems();
void changeItemPrices();
void displayTotalSale();
void displayItemAvailability();

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

void purchaseItem() {
	
}

void adminMode() {
    int admin_pass;
    printf("Enter the admin password: ");
    scanf("%d", &admin_pass);

    if (admin_pass != password) {
        printf("Incorrect admin password. Access denied.\n");
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

        if (admin_choice == 1) {
            replenishItems();
        } else if (admin_choice == 2) {
            changeItemPrices();
        } else if (admin_choice == 3) {
            displayTotalSale();
        } else if (admin_choice == 4) {
            displayItemAvailability();
        } else if (admin_choice == 0) {
            return;
        } else {
            printf("Invalid choice. Please try again.\n");
        }
    }
}

void replenishItems() {

}

void changeItemPrices() {
    printf("Enter the new price for item A: ");
    scanf("%lf", &itemAPrice);
    printf("Enter the new price for item B: ");
    scanf("%lf", &itemBPrice);
    printf("Enter the new price for item C: ");
    scanf("%lf", &itemCPrice);
}

void displayTotalSale() {
    printf("Total Sales Amount: $%.2lf\n", total_amount);
    total_amount = 0.0;
    printf("Total Sales Amount reset to $%.2lf\n", total_amount);
}

void displayItemAvailability() {
    printf("Item A: Quantity %d\n", itemAQuantity);
    printf("Item B: Quantity %d\n", itemBQuantity);
    printf("Item C: Quantity %d\n", itemCQuantity);
}

