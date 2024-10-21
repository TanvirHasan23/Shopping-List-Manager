# Shopping-List-Manager
from Practice2 import product_price
from practice1 import shopping_list

available_product = {
    'bread': 1.50,
    'milk': 2.00,
    'eggs': 3.00,
    'butter': 2.50,
    'cheese': 4.00,
    'apple': .30,
    'chicken': 5.00,
    'rice': 1.20,
    'pasta': 1.00
}
def add_items_to_list():
    shopping_list = {}
    print('Enter items for your shopping list. Type done when finished. ')

    while True:
        product = input('Enter product name: ')
        if product == 'done':
            break
        if product in shopping_list:
            print(f'{product} is already in shopping list.')
        else:
            shopping_list[product] = 0
    return shopping_list

def assign_price(shopping_list):

    for product in shopping_list:
        if product in available_product:
            shopping_list[product] = available_product[product_price]
        else:
            shopping_list[product] = float(input(f'Enter the price of {product}: '))
    return shopping_list

def display_shopping_list(shopping_list):
    print('Your shopping list: ')
    total_prices = 0
    for product, value in shopping_list:
        print(f'{product}: ${value}')
        total_prices += value
    print(f'Total Cost is: {total_prices}')


display_shopping_list(assign_price(add_items_to_list()))
