# Shopping-List-Manager
available_product = {
    'bread': 1.50, 'milk': 2.00, 'eggs': 3.00, 'butter': 2.50,
    'cheese': 4.00, 'apple': 0.30, 'chicken': 5.00, 'rice': 1.20, 'pasta': 1.00
}

def add_items_to_list():
    shopping_list = {}
    print('Enter items for your shopping list. Type "done" when finished.')

    while True:
        product = input('Enter product name: ').lower() 
        if product == 'done':
            break
        if product in shopping_list:
            print(f'{product} is already in shopping list.')
        else:
            shopping_list[product] = 0  
    return shopping_list 

def assign_price(shopping_list):
    for product in list(shopping_list):
        if product in available_product:
            shopping_list[product] = available_product[product]
        else:
            try:
                price = float(input(f'Enter the price of {product}: '))
                if price >= 0: 
                    shopping_list[product] = price
                else:
                    print("Price cannot be negative. Please try again.")
                    del shopping_list[product] 
            except ValueError:
                print("Invalid price entered. Please enter a number.")
                del shopping_list[product] 
    return shopping_list

def display_shopping_list(shopping_list):
    if shopping_list: 
        print("\nYour Shopping List:")
        total_price = 0
        for product, price in shopping_list.items():
            print(f"- {product.capitalize()}: ${price:.2f}")
            total_price += price
        print(f"Total Price: ${total_price:.2f}")
    else:
        print("Your shopping list is empty.")


my_list = add_items_to_list()
my_priced_list = assign_price(my_list)
display_shopping_list(my_priced_list)
