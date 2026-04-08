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

def first_choice():
    while True:
        slow_print("Day 1: A customer walks in. What do you do?")
        slow_print("A. Greet them warmly")
        slow_print("B. Ignore them")
        choice = input("Choice (A/B): ").upper()

        if choice == "A":
            slow_print("Customer smiles and sits down. Good start!\n")
            return "good"
        elif choice == "B":
            slow_print("Customer leaves. Not a good impression...\n")
            return "bad"
        else:
            print("Invalid input. Try again.\n")

def second_choice(path):
    while True:
        slow_print("You need to prepare a drink.")
        slow_print("A. Make a fancy latte")
        slow_print("B. Serve instant coffee")
        choice = input("Choice (A/B): ").upper()

        if choice == "A":
            slow_print("The drink looks amazing!\n")
            return path + "_good"
        elif choice == "B":
            slow_print("It tastes cheap...\n")
            return path + "_bad"
        else:
            print("Invalid input. Try again.\n")

def third_choice(path):
    while True:
        slow_print("More customers are coming!")
        slow_print("A. Work hard and serve all")
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

def ending(result):
    slow_print("\n--- RESULT ---")

    if result.count("good") >= 2:
        slow_print("🌟 GOOD ENDING: Trish Cafe becomes popular!")
    elif result.count("bad") >= 2:
        slow_print("💔 BAD ENDING: The cafe shuts down...")
    else:
        slow_print("😐 NORMAL ENDING: The cafe survives, but barely.")

def play_game():
    title_screen()
    intro()

    result = first_choice()
    result = second_choice(result)
    result = third_choice(result)

    ending(result)

def main():
    while True:
        play_game()
        again = input("\nPlay again? (yes/no): ").lower()
        if again != "yes":
            print("Thanks for playing Trish Cafe! ☕")
            break

main()