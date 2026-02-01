# Coffee-Machine-Project-Using-PYTHON

# Coffee Machine Simulator – Python Project

## Project Overview
The Coffee Machine Simulator is a command-line Python application that mimics the working of a real-world coffee vending machine. The program allows users to select a beverage, verifies ingredient availability, processes coin-based payments, calculates change, prepares the drink, and maintains a record of remaining resources and total profit.

This project demonstrates strong foundational Python skills, logical thinking, and the ability to translate a real-life business process into a functional software solution.

## Problem Statement
Design a system that:
- Offers multiple coffee options
- Manages limited machine resources
- Accepts payments using coins
- Validates transactions
- Produces accurate reports for resources and revenue

## Solution Approach
The application uses:
- Dictionaries to store menu items and machine resources
- Modular functions to handle specific tasks
- Conditional logic to validate user inputs and payments
- A continuous loop to simulate an always-on coffee machine

The system ensures data consistency by updating resources only after successful transactions.

## Features
- Supports multiple drink options (espresso, latte, cappuccino)
- Validates availability of required ingredients
- Accepts coin input and calculates total payment
- Returns change when excess payment is provided
- Maintains total profit earned
- Displays real-time resource and revenue reports
- Allows safe shutdown of the machine

## Technologies Used
- Python 3
- Core Python concepts:
  - Dictionaries
  - Functions
  - While loops
  - Conditional statements
  - Global variables
  - Input/output handling

## Application Workflow
1. User selects a beverage or command
2. System checks ingredient availability
3. User inserts coins
4. Payment is validated against drink cost
5. Resources are deducted
6. Drink is served
7. Profit and resources are updated
8. Machine waits for the next input

## Commands Supported
- espresso – Orders espresso
- latte – Orders latte
- cappuccino – Orders cappuccino
- report – Displays remaining resources and profit
- off – Turns off the coffee machine

## How to Run the Project

### Prerequisites
- Python 3 installed on the system

### Steps

cd coffee-machine-python
Run the application:

python main.py
Code Structure
MENU dictionary defines available drinks, ingredients, and prices

resources dictionary tracks machine inventory

is_resource_sufficient() validates ingredient availability

process_coins() calculates total payment

is_transaction_successful() validates payment and updates profit

make_coffee() deducts resources and completes the order

Main loop controls user interaction and machine state

# Key Learnings
-Implementation of business logic using Python

-Modular and reusable function design

-Handling state and data integrity

-Simulating real-world systems using command-line programs

-Writing clean, readable, and maintainable code


# This project showcases:

-Strong understanding of Python fundamentals

-Ability to structure code logically

-Practical application of problem-solving skills

-Experience in building interactive applications

Author
Manish Kumar
Aspiring Data Analyst with strong Python fundamentals


Python Project

```python
MENU = {
    "espresso": {
        "ingredients": {
            "water": 50,
            "coffee": 18,
        },
        "cost": 1.5,
    },
    "latte": {
        "ingredients": {
            "water": 200,
            "milk": 150,
            "coffee": 24,
        },
        "cost": 2.5,
    },
    "cappuccino": {
        "ingredients": {
            "water": 250,
            "milk": 100,
            "coffee": 24,
        },
        "cost": 3.0,
    }
}

profit = 0
resources = {
    "water": 300,
    "milk": 200,
    "coffee": 100,
}


def is_resource_sufficient(order_ingredients):
    """Returns True when order can be made, False if ingredients are insufficient."""
    for item in order_ingredients:
        if order_ingredients[item] > resources[item]:
            print(f"Sorry there is not enough {item}.")
            return False
    return True


def process_coins():
    """Returns the total calculated from coins inserted."""
    print("Please insert coins.")
    total = int(input("how many quarters?: ")) * 0.25
    total += int(input("how many dimes?: ")) * 0.1
    total += int(input("how many nickles?: ")) * 0.05
    total += int(input("how many pennies?: ")) * 0.01
    return total


def is_transaction_successful(money_received, drink_cost):
    """Return True when the payment is accepted, or False if money is insufficient."""
    if money_received >= drink_cost:
        change = round(money_received - drink_cost, 2)
        print(f"Here is ${change} in change.")
        global profit
        profit += drink_cost
        return True
    else:
        print("Sorry that's not enough money. Money refunded.")
        return False


def make_coffee(drink_name, order_ingredients):
    """Deduct the required ingredients from the resources."""
    for item in order_ingredients:
        resources[item] -= order_ingredients[item]
    print(f"Here is your {drink_name} ☕️. Enjoy!")


is_on = True

while is_on:
    choice = input("What would you like? (espresso/latte/cappuccino): ")
    if choice == "off":
        is_on = False
    elif choice == "report":
        print(f"Water: {resources['water']}ml")
        print(f"Milk: {resources['milk']}ml")
        print(f"Coffee: {resources['coffee']}g")
        print(f"Money: ${profit}")
    else:
        drink = MENU[choice]
        if is_resource_sufficient(drink["ingredients"]):
            payment = process_coins()
            if is_transaction_successful(payment, drink["cost"]):
                make_coffee(choice, drink["ingredients"])

```

**Author** 
Manish Kumar-Data Analyst with strong Python fundamentals
















