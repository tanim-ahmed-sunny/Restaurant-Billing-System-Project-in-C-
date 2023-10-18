# Restaurant-Billing-System-Project-in-C-



This C program implements a Restaurant Billing System, allowing users to generate, display, and search invoices for customer orders. It utilises a file-based approach to store invoices. Below are the key functionalities:

Structures:

items: Represents individual menu items with attributes like name, price, and quantity.
orders: Holds information about a customer's order, including their name, date, number of items, and an array of items.

Functions:

generateBillHeader:

 Prints and writes the header of the invoice, including the restaurant name, date, and recipient's name.
generateBillBody: Prints and writes information about the items ordered, including their names, quantities, and total prices.
generateBillFooter: Prints and writes the footer of the invoice, showing the sub-total, discount, net total, taxes, and total.
displayInvoiceFile: Reads and displays the contents of the invoice file.

Main Functionality:

The main function provides a menu-driven interface for users.
Options include generating an invoice, displaying all invoices, searching for a specific invoice, and exiting the program.
Users can enter customer information, and order items, and the program calculates the total.

File Handling:

The program uses file operations to append invoice details to a file named "bill.txt".
It can also read and display existing invoices from the same file.

Error Handling:

The program includes basic error handling, such as checking if files can be opened successfully.
Looping and Control Flow:

The program uses loops to allow users to perform multiple operations without exiting the program.

Usage:

This program provides a simple command-line interface for managing restaurant invoices.
Users can interactively input customer details, order items, and save invoices.
It allows viewing saved invoices, and searching for invoices based on customer names.

Note:

It is recommended to compile and run this program in a C environment to observe its functionalities.
This program provides a basic framework for a restaurant billing system. Depending on the specific requirements and complexity of the system, additional features and error handling may need to be implemented.
