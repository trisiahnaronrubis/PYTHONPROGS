import time

def slow_print(text):
    for char in text:
        print(char, end='', flush=True)
        time.sleep(0.03)
    print()

def title_screen():
    print("\n========================")
    print("     TRISH CAFE ☕")
    print("========================\n")

def intro():
    slow_print("Welcome to Trish Cafe!")
    slow_print("You're the new owner of a small but cozy cafe.")
    slow_print("Your choices will decide if your cafe succeeds... or fails.\n")

def show_menu():
    print("\n--- MENU ---")
    menu = {
        "A": ("Latte", 120),
        "B": ("Cappuccino", 100),
        "C": ("Iced Coffee", 90)
    }

    for key in menu:
        print(f"{key}. {menu[key][0]} - ₱{menu[key][1]}")

    return menu

def order_drink():
    menu = show_menu()

    while True:
        choice = input("Choose a drink (A/B/C): ").upper()

        if choice in menu:
            drink, price = menu[choice]
            slow_print(f"You served {drink} - ₱{price}\n")
            return price
        else:
            print("Invalid choice. Try again.\n")

def first_choice():
    while True:
        slow_print("Day 1: A customer walks in. What do you do?")
        slow_print("A. Greet them warmly")
        slow_print("B. Ignore them")
        choice = input("Choice (A/B): ").upper()

        if choice == "A":
            slow_print("Customer smiles and orders something!\n")
            return "good"
        elif choice == "B":
            slow_print("Customer leaves. Bad start...\n")
            return "bad"
        else:
            print("Invalid input. Try again.\n")

def second_choice(path):
    while True:
        slow_print("You need to prepare the drink.")
        slow_print("A. Make it carefully")
        slow_print("B. Rush the preparation")
        choice = input("Choice (A/B): ").upper()

        if choice == "A":
            slow_print("The drink looks perfect!\n")
            return path + "_good"
        elif choice == "B":
            slow_print("The drink is messy...\n")
            return path + "_bad"
        else:
            print("Invalid input. Try again.\n")

def third_choice(path):
    while True:
        slow_print("More customers arrive!")
        slow_print("A. Serve all customers")
        slow_print("B. Close early")
        choice = input("Choice (A/B): ").upper()

        if choice == "A":
            slow_print("You handled the rush well!\n")
            return path + "_good"
        elif choice == "B":
            slow_print("Customers are disappointed...\n")
            return path + "_bad"
        else:
            print("Invalid input. Try again.\n")

def ending(result, total):
    slow_print("\n--- RESULT ---")

    if result.count("good") >= 2:
        slow_print("🌟 GOOD ENDING: Trish Cafe becomes popular!")
    elif result.count("bad") >= 2:
        slow_print("💔 BAD ENDING: The cafe shuts down...")
    else:
        slow_print("😐 NORMAL ENDING: The cafe survives, but barely.")

    slow_print(f"Total earnings today: ₱{total}")

def play_game():
    title_screen()
    intro()

    result = first_choice()

    total = 0
    total += order_drink()

    result = second_choice(result)
    result = third_choice(result)

    ending(result, total)

def main():
    while True:
        play_game()
        again = input("\nPlay again? (yes/no): ").lower()
        if again != "yes":
            print("Thanks for playing Trish Cafe! ☕")
            break

main()