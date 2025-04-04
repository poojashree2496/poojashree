class Bookstore:
    def __init__(self):
        self.inventory = {}

    def add_book(self, title, author, price, stock):
        self.inventory[title] = {'author': author, 'price': price, 'stock': stock}

    def update_stock(self, title, quantity):
        if title in self.inventory:
            self.inventory[title]['stock'] += quantity
        else:
            print("Book not found in inventory.")

    def sell_book(self, title, quantity):
        if title in self.inventory:
            if self.inventory[title]['stock'] >= quantity:
                self.inventory[title]['stock'] -= quantity
                print(f"{quantity} copies of '{title}' sold.")
            else:
                print("Not enough stock available.")
        else:
            print("Book not found in inventory.")

    def display_books(self):
        print("Current Inventory:")
        for title, details in self.inventory.items():
            print(f"Title: {title}, Author: {details['author']}, Price: {details['price']}, Stock: {details['stock']}")

# Example usage:
store = Bookstore()
store.add_book("Python Programming", "John Doe", 599, 10)
store.add_book("Data Science Essentials", "Jane Smith", 799, 5)

store.display_books()

store.sell_book("Python Programming", 2)
store.update_stock("Data Science Essentials", 3)

store.display_books()
