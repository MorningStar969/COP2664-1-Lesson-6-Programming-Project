# COP2664-1-Lesson-6-Programming-Project
This is a GitHub repository link for the Programming Project of Lesson 6.

// This program is used for a customer who is ordering a meal at a food court where it shows the list of food options that are available, the price oif each food item, and the total price of the meal where they can also apply a discount if they have one.

import Foundation // This is used for the math functions
struct MenuItem { // This is used to store the menu items and their prices.
  var name: String // This is used to store the name of the menu item.
  var price: Double // This is used to store the price of the menu item.
  var category: String // This is used to store the category of the menu item.
}

var menu: [MenuItem] = [ // This is used to store the menu items and their prices.
  MenuItem(name: "Burger", price: 5.99, category: "Food"),
  MenuItem(name: "Pizza", price: 9.95, category: "Food"),
  MenuItem(name: "Soda", price: 4.99, category: "Drink"),
  MenuItem(name: "Milkshake", price: 3.99, category: "Dessert"),
  MenuItem(name: "Salad", price: 8.69, category: "Food"),
  MenuItem(name: "Turkey Sandwich", price: 6.99, category: "Food"),
  MenuItem(name: "Water", price: 1.95, category: "Drink"),
  MenuItem(name: "Cookie", price: 2.49, category: "Dessert"),
  MenuItem(name: "Smoothie", price: 2.99, category: "Drink")]
func displayMenu() { // This is used to display the menu items and their prices.
  print("Menu:") // This is used to print the menu items and their prices.
  for item in menu { // This is used to iterate over the menu items.
    print("\(item.name) - $\(item.price) - \(item.category)") // This is used to print the menu items and their prices.
  }
}
func addItemToOrder(itemName: String) { // This is used to add an item to the order.
  if let item = menu.first(where: { $0.name == itemName }) { // This is used to find the item in the menu.
    order.append(item) // This is used to add the item to the order.
    print("Item added to order.") // This is used to print a message indicating that the item was added to the order.
  } else { // This is used to handle the case where the item is not found in the menu.
    print("Item not found in the menu.") // This is used to print a message indicating that the item was not found in the menu.
  }
}
func calculateOrderTotal() { // This is used to calculate the total price of the order.
  let total = order.reduce(0.0) { $0 + $1.price } // This is used to calculate the total price of the order.
  print("Order Total: $\(total)") // This is used to print the total price of the order.
}
func applyDiscount(discountPercentage: Double) { // This is used to apply a discount to the order.
  let discount = order.reduce(0.0) { $0 + $1.price } * (discountPercentage / 100) // This is used to calculate the discount amount.
  let totalAfterDiscount = order.reduce(0.0) { $0 + $1.price } - discount // This is used to calculate the total price of the order after applying the discount.
  print("Order Total after discount: $\(totalAfterDiscount)") // This is used to print the total price of the order after applying the discount.
}
func viewItemsByCategory(category: String) { // This is used to view items by category.
  let filteredItems = menu.filter { $0.category == category } // This is used to filter the menu items by category.
  print("\(category) Items:") // This is used to print the category of the items.
  for item in filteredItems { // This is used to iterate over the filtered items.
    print("\(item.name) - $\(item.price)") // This is used to print the name and price of the items.
  }
}
var order: [MenuItem] = [] // This is used to store the items in the order.
print("Welcome to the Restaurant Ordering System!") // This is used to print a welcome message.
while true { // This is used to loop until the user chooses to exit.
  print("\nChoose an option:") // This is used to print a message indicating the available options.
  print("1. View Menu") // This is used to print an option to view the menu.
  print("2. Add Item to Order") // This is used to print an option to add an item to the order.
  print("3. View Order Total") // This is used to print an option to view the order total.
  print("4. Apply Discount") // This is used to print an option to apply a discount to the order.
  print("5. View Items by Category") // This is used to print an option to view items by category.
  print("0. Exit") // This is used to print an option to exit the program.
  if let choice = readLine(), let option = Int(choice) { // This is used to read the user's choice and convert it to an integer.
    switch option { // This is used to handle the user's choice.
      case 1: // This is used to handle the case where the user chooses to view the menu.
        displayMenu() // This is used to display the menu items and their prices.
      case 2: // This is used to handle the case where the user chooses to add an item to the order.
        print("Enter the item name:") // This is used to print a message indicating the item name.
        if let itemName = readLine() { // This is used to read the item name.
          addItemToOrder(itemName: itemName) // This is used to add the item to the order.
        }
      case 3: // This is used to handle the case where the user chooses to view the order total.
        calculateOrderTotal() // This is used to calculate the total price of the order.
      case 4: // This is used to handle the case where the user chooses to apply a discount to the order.
        print("Enter the discount percentage:") // This is used to print a message indicating the discount percentage.
        if let discountPercentage = readLine(), let percentage = Double(discountPercentage) { // This is used to read the discount percentage and convert it to a double.
          applyDiscount(discountPercentage: percentage) // This is used to apply the discount to the order.
        }
      case 5: // This is used to handle the case where the user chooses to view items by category.
        print("Enter the category name:") // This is used to print a message indicating the category name.
        if let category = readLine() { // This is used to read the category name.
          viewItemsByCategory(category: category) // This is used to view items by category.
        }
      case 0: // This is used to handle the case where the user chooses to exit the program.
        print("Exiting the program.") // This is used to print a message indicating that the program is exiting.
        break // This is used to exit the loop.
      default: // This is used to handle the case where the user enters an invalid option.
        print("Invalid choice. Please try again.") // This is used to print a message indicating that the choice is invalid.
    }
  }
}
