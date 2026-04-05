# PYTHONPROGS
Game Simulator 


import random
import time

def start_game():
    money = 50.00
    coffee_beans = 10
    day = 1
    reputation = 5
    
    print("☕ Welcome to Trisiah Cafe! ☕")
    print("Can you turn this small shop into a local legend?")
    
    while day <= 5:  # Let's play for a 5-day work week
        print(f"\n--- Day {day} ---")
        print(f"Stats: ${money:.2f} | Beans: {coffee_beans} | Rep: {reputation}/10")
        
        # 1. Management Phase
        action = input("Options: (1) Buy Beans [$5] (2) Start Shift: ")
        
        if action == "1":
            if money >= 5:
                money -= 5
                coffee_beans += 10
                print("🛒 Restocked! You now have more beans.")
            else:
                print("❌ Not enough money!")
        
        # 2. Shift Phase
        print("\nDoors are open! Customers are coming in...")
        customers = random.randint(2, 5)
        
        for i in range(customers):
            time.sleep(1)
            if coffee_beans > 0:
                print(f"  > Customer {i+1} ordered a latte!")
                # Simple success/fail logic
                success = random.choice([True, True, False])
                if success:
                    income = 6.50
                    money += income
                    coffee_beans -= 1
                    print(f"    ✅ Perfect brew! You earned ${income}")
                else:
                    reputation -= 1
                    coffee_beans -= 1
                    print("    ⚠️ You burnt the milk! Rep down.")
            else:
                print("    🚫 Out of beans! You had to turn a customer away.")
                reputation -= 1

        day += 1
        
    # Game Over
    print("\n--- Weekly Report ---")
    print(f"Final Balance: ${money:.2f}")
    print(f"Final Reputation: {reputation}")
    if reputation > 7:
        print("Trisiah Cafe is the talk of the town! You win!")
    else:
        print("A bit of a rocky start, but Trisiah Cafe is still standing.")

if __name__ == "__main__":
    start_game()

