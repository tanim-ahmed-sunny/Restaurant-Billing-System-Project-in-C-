#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#define INVOICE "bill.txt"

struct items{
    char item[20];
    float price;
    int qty;
};

struct orders{
    char customer[50];
    char date[50];
    int numOfItems;
    struct items itm[50];
};

void generateBillHeader(char name[50], char date[30]) {

     printf("\n\n");
        printf("\t    RTR. Restaurant");
        printf("\n\t   -----------------");
        printf("\nDate:%s",date);
        printf("\nInvoice To: %s",name);
        printf("\n");
        printf("---------------------------------------\n");
        printf("Items\t\t");
        printf("Qty\t\t");
        printf("Total\t\t");
        printf("\n---------------------------------------");
        printf("\n\n");


    FILE *file = fopen(INVOICE, "a");
    if (!file) {
        printf("Error opening invoice file.\n");
        return;
    }

    fprintf(file, "\n\n");
    fprintf(file, "\t    RTR. Restaurant");
    fprintf(file, "\n\t   -----------------");
    fprintf(file, "\nDate:%s", date);
    fprintf(file, "\nInvoice To: %s", name);
    fprintf(file, "\n");
    fprintf(file, "---------------------------------------\n");
    fprintf(file, "Items\t\t");
    fprintf(file, "Qty\t\t");
    fprintf(file, "Total\t\t");
    fprintf(file, "\n---------------------------------------");
    fprintf(file, "\n\n");

    fclose(file);
}



void generateBillBody(char item[30], int qty, float price) {

        printf("%s\t\t",item);
        printf("%d\t\t",qty);
        printf("%.2f\t\t",qty * price);
        printf("\n");

    FILE *file = fopen(INVOICE, "a");
    if (!file) {
        printf("Error opening invoice file.\n");
        return;
    }

    fprintf(file, "%s\t\t", item);
    fprintf(file, "%d\t\t", qty);
    fprintf(file, "%.2f\t\t", qty * price);
    fprintf(file, "\n");

    fclose(file);
}



void generateBillFooter(float total) {

     printf("\n");
    float dis = 0.1*total;
    float netTotal=total-dis;
    float vat=0.05*netTotal,grandTotal=netTotal + 2*vat;
    printf("---------------------------------------\n");
    printf("Sub Total\t\t\t%.2f",total);
    printf("\nDiscount @10%s\t\t\t%.2f","%",dis);
    printf("\n\t\t\t\t-------");
    printf("\nNet Total\t\t\t%.2f",netTotal);
    printf("\nVAT @5%s\t\t\t\t%.2f","%",vat);
    printf("\nSC @5%s\t\t\t\t%.2f","%",vat);
    printf("\n---------------------------------------");
    printf("\nGrand Total\t\t\t%.2f",grandTotal);
    printf("\n---------------------------------------\n");
    printf("\nTime-%s", __TIME__);

    FILE *file = fopen(INVOICE, "a");
    if (!file) {
        printf("Error opening invoice file.\n");
        return;
    }
    fprintf(file, "\n");
    fprintf(file, "---------------------------------------\n");
    fprintf(file, "Sub Total\t\t\t%.2f", total);
    fprintf(file, "\nDiscount @10%s\t\t\t%.2f", "%", dis);
    fprintf(file, "\n\t\t\t\t-------");
    fprintf(file, "\nNet Total\t\t\t%.2f", netTotal);
    fprintf(file, "\nCGST @5%s\t\t\t%.2f", "%", vat);
    fprintf(file, "\nSGST @5%s\t\t\t%.2f", "%", vat);
    fprintf(file, "\n---------------------------------------");
    fprintf(file, "\nGrand Total\t\t\t%.2f", grandTotal);
    fprintf(file, "\n---------------------------------------\n");
     fprintf(file,"\nTime-%s\n", __TIME__);

    fclose(file);
}
void displayInvoiceFile() {
    FILE *file = fopen(INVOICE, "r");
    if (!file) {
        printf("Error opening invoice file.\n");
        return;
    }

    char c;
    while ((c = fgetc(file)) != EOF) {
        putchar(c);
    }

    fclose(file);
}
int main(){

    int opt,n;
    struct orders ord;
    struct orders order;
    char saveBill = 'y',contFlag = 'y';
    char name[50];
    FILE *fp = fopen(INVOICE, "a");
    if (!fp) {
        printf("Error opening users file.\n");
        return;
    }

    while(contFlag == 'y'){
    system("cls");
    float total = 0;
    int invoiceFound = 0;
    printf("\t============RTR. RESTAURANT============");
    printf("\n\nPlease select your prefered operation");
    printf("\n\n1.Generate Invoice");
    printf("\n2.Show all Invoices");
    printf("\n3.Search Invoice");
    printf("\n4.Exit");

    printf("\n\nYour choice:\t");
    scanf("%d",&opt);
    fgetc(stdin);
    switch(opt){
        case 1:
        system("cls");
        printf("\nPlease enter the name of the customer:\t");
        fgets(ord.customer,50,stdin);
        ord.customer[strlen(ord.customer)-1] = 0;
        strcpy(ord.date,__DATE__);
        printf("\nPlease enter the number of items:\t");
        scanf("%d",&n);
        ord.numOfItems = n;
        for(int i=0;i<n;i++){
            fgetc(stdin);
            printf("\n\n");
            printf("Please enter the item %d:\t",i+1);
            fgets(ord.itm[i].item,20,stdin);
            ord.itm[i].item[strlen(ord.itm[i].item)-1]=0;
            printf("Please enter the quantity:\t");
            scanf("%d",&ord.itm[i].qty);
            printf("Please enter the unit price:\t");
            scanf("%f",&ord.itm[i].price);
            total += ord.itm[i].qty * ord.itm[i].price;
        }

        generateBillHeader(ord.customer,ord.date);
        for(int i=0;i<ord.numOfItems;i++){
            generateBillBody(ord.itm[i].item,ord.itm[i].qty,ord.itm[i].price);
        }
        generateBillFooter(total);

        printf("\nDo you want to save the invoice [y/n]:\t");
        scanf("%s",&saveBill);

        if(saveBill == 'y'){
            fp = fopen("INVOICE","a+");
            fwrite(&ord,sizeof(struct orders),1,fp);
            if(fwrite != 0)
            printf("\nSuccessfully saved");
            else
            printf("\nError saving");
            fclose(fp);
        }
        break;

        case 2:
        system("cls");
        fp = fopen(INVOICE, "r");
        printf("\n  *****Your Previous Invoices*****\n");
        displayInvoiceFile();
        fclose(fp);
        break;


        case 3:
        printf("Enter the name of the customer:\t");
        char name[50];
        fgets(name, 50, stdin);
        name[strlen(name) - 1] = '\0';
        system("cls");

        FILE *fp = fopen(INVOICE, "r");
        if (!fp) {
            printf("Error opening invoice file.\n");
            return 1;
        }
         printf("\t*****Invoice of %s*****", name);
        int invoiceFound = 0;
        struct orders ord;

       while(fread(&order,sizeof(struct orders),1,fp)){
            float tot = 0;
            if(!strcmp(order.customer,name)){
            generateBillHeader(order.customer,order.date);
            for(int i=0;i<order.numOfItems;i++){
                generateBillBody(order.itm[i].item,order.itm[i].qty,order.itm[i].price);
                tot+=order.itm[i].qty * order.itm[i].price;
            }
            generateBillFooter(tot);
            invoiceFound = 1;
            }
         if (!invoiceFound) {
            printf("Sorry, the invoice for %s does not exist\n", name);
        }
       }

        fclose(fp);
        break;

    case 4:
    printf("\n\t\t Bye Bye :)\n\n");
    exit(0);
    break;

    default:
    printf("Sorry invalid option");
    break;
    }
    printf("\nDo you want to perform another operation?[y/n]:\t");
    scanf("%s",&contFlag);
    }

    printf("\n\t\t Bye Bye :)\n\n");
    printf("\n\n");

    return 0;

}
