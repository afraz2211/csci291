
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
	char itemNum;
	char answer;
	float coin;
	float tempItem;
	char choice;
	fflush(stdin);
	// printing items 
	printf("(A)  %.2f \n",itemAPrice);
	printf("(B)  %.2f \n", itemBPrice);
	printf("(C)  %.2f \n", itemCPrice);
	printf("choose your item:...\n");
	scanf("%c",&itemNum);
	
fflush(stdin);
	if ((itemNum >='A') &&(itemNum <'D')) {
		if(itemNum == 'A'){
			printf("You choose item A and price %f , pls confirm (y/n)\n",itemAPrice);
				scanf("%c",&answer);
			tempItem=itemAPrice;
			
		}
			if(itemNum == 'B'){
			printf("You choose item B and price %f , pls confirm (y/n)\n",itemBPrice);
				scanf("%c",&answer);
			tempItem=itemBPrice;
		}
			if(itemNum == 'C'){
			printf("You choose item C and price %f , pls confirm (y/n)\n",itemCPrice);
				scanf("%c",&answer);
			tempItem=itemCPrice;
		}
	
		if(answer=='y'){
			printf("insert the coins(1, 0.5, 0.25)\n");
			while(tempItem > 0){
				fflush(stdin);
				scanf("%f",&coin);
				if (coin  > 1.0){
					printf("Entered wrong  demonomiations ,press x to cancel else c to continue \n");
					fflush(stdin);
					scanf("%c",&choice );
					if (choice == 'x'){
						purchaseItem();
						break;
					} 
					if(choice  == 'c'){
						continue;
					}
				}else {
					tempItem = tempItem - coin ;
				}
			}
			if(tempItem == 0){
				printf("Thank you for purchasing\n");
				printf("thank you for having %c", itemNum);
				if(itemNum == 'A'){
					itemAQuantity -= 1;
					total_amount += itemAPrice;
				}
				if(itemNum == 'B'){
					itemBQuantity-= 1;
					total_amount += itemBPrice;
				}
				if(itemNum == 'C'){ 
					itemCQuantity -= 1;
					total_amount += itemCPrice;
				}
			}
		}
			
		
	}
	else{
		printf("cancelling the purchase\n");
	}
	

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
	itemAQuantity = rand()% 40 ;
	itemAQuantity = rand()% 40 ;
	itemAQuantity = rand()% 40 ;
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

