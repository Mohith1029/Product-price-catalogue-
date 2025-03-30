catalogue = {}

def add_product(name, price):
    if name in catalogue:
        print(f"Product '{name}' already exists. Use update_price() to change the price.")
    else:
        catalogue[name] = price
        print(f"Product '{name}' added successfully.")

def update_price(name, price):
    if name in catalogue:
        catalogue[name] = price
        print(f"Price of '{name}' updated to {price}.")
    else:
        print(f"Product '{name}' not found. Use add_product() to add it first.")

def remove_product(name):
    if name in catalogue:
        del catalogue[name]
        print(f"Product '{name}' removed successfully.")
    else:
        print(f"Product '{name}' not found.")

def search_by_price_range(min_price, max_price):
    result = {name: price for name, price in catalogue.items() if min_price <= price <= max_price}
    if result:
        print("Products in the given price range:")
        for name, price in result.items():
            print(f"{name}: {price}")
    else:
        print("No products found in the given price range.")

def display_catalogue():
    if catalogue:
        print("Product Catalogue:")
        for name, price in catalogue.items():
            print(f"{name}: {price}")
    else:
        print("The catalogue is empty.")

def main():
    while True:
        print("\nProduct Catalogue Menu:")
        print("1. Add product")
        print("2. Update price")
        print("3. Remove product")
        print("4. Search by price range")
        print("5. Display catalogue")
        print("6. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            name = input("Enter product name: ")
            price = float(input("Enter product price: "))
            add_product(name, price)
        elif choice == "2":
            name = input("Enter product name: ")
            price = float(input("Enter new price: "))
            update_price(name, price)
        elif choice == "3":
            name = input("Enter product name: ")
            remove_product(name)
        elif choice == "4":
            min_price = float(input("Enter minimum price: "))
            max_price = float(input("Enter maximum price: "))
            search_by_price_range(min_price, max_price)
        elif choice == "5":
            display_catalogue()
        elif choice == "6":
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
