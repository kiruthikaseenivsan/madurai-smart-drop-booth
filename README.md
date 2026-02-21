import time
import random

class MSDB_SmartSystem:
    def __init__(self):
        # Database simulation
        self.user_db = {"user_01": {"name": "Macha", "points": 100}}
        self.waste_rates = {"dry": 10, "wet": 5} # Points per kg

    def authenticate_user(self):
        print("\n--- MSDB SMART BOOTH ---")
        user_id = input("Scan QR / Enter Smart Pass ID: ")
        if user_id in self.user_db:
            print(f"Welcome, {self.user_db[user_id]['name']}!")
            return user_id
        else:
            print("Access Denied! Invalid ID.")
            return None

    def process_waste(self, user_id):
        print("\nSelect Waste Type:")
        print("1. Dry Waste (Plastic, Paper, Bottles)")
        print("2. Wet Waste (Organic, Food)")
        choice = input("Enter choice (1/2): ")

        waste_type = "dry" if choice == "1" else "wet"
        print(f"\nOpening {waste_type.upper()} waste slot... Please drop your waste.")
        
        # Simulating Load Cell (Weight Sensor) reading
        time.sleep(2) 
        weight = round(random.uniform(0.5, 5.0), 2) # Simulating 0.5kg to 5kg
        print(f"Weight Detected: {weight} kg")

        # Reward Logic
        earned_points = int(weight * self.waste_rates[waste_type])
        self.user_db[user_id]['points'] += earned_points
        
        print(f"Success! You earned {earned_points} points.")
        print(f"Total Balance: {self.user_db[user_id]['points']} points.")
        print("Thank you for keeping Madurai clean!")

# --- Execution ---
msdb = MSDB_SmartSystem()
active_user = msdb.authenticate_user()

if active_user:
    msdb.process_waste(active_user)
