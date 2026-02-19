import time

def msdb_process_updated():
    print("--- MADURAI SMART DROP BOOTH (MSDB) ---")
    print("Welcome! Please Scan Mobile App OR MSDB Smart Pass.")
    
    # User choice: Mobile or Card
    user_input = input("\n[ACTION] Scan your ID (Type 'SCAN' for Mobile or 'PASS' for Smart Card): ")
    
    if user_input.upper() in ["SCAN", "PASS"]:
        if user_input.upper() == "PASS":
            print("Reading MSDB Smart Pass... Verified! ✅")
        else:
            print("Authenticating Mobile App... Verified! ✅")
            
        print("\n[SYSTEM] Opening Deposit Slot... (Motor Actuated)")
        time.sleep(1)
        print(">>> SLOT OPEN. Please drop your waste.")
        
        weight = float(input("\n[SENSOR] Enter weight (Kg): "))
        print("\n[SYSTEM] Closing Slot... Calculating Rewards...")
        
        points = weight * 10
        print(f"REWARD: {points} Points added to your account!")
        print("---------------------------------------")
    else:
        print("Invalid Entry. Please try again.")

msdb_process_updated()
