import pandas as pd
from datetime import datetime
import random

# Simulate sensor data
def generate_sensor_data(num_entries=10):
    data = {
        "Timestamp": [datetime.now().strftime("%Y-%m-%d %H:%M:%S") for _ in range(num_entries)],
        "Camera_Input": [random.choice(['clear', 'obstacle', 'turn']) for _ in range(num_entries)],
        "LiDAR_Distance_m": [round(random.uniform(0.5, 10.0), 2) for _ in range(num_entries)],
        "Ultrasonic_cm": [round(random.uniform(10, 100), 1) for _ in range(num_entries)],
    }
    return pd.DataFrame(data)

# Simulate robotic task execution log
def generate_robotic_log(num_tasks=5):
    tasks = {
        "Timestamp": [datetime.now().strftime("%Y-%m-%d %H:%M:%S") for _ in range(num_tasks)],
        "Task": [random.choice(['pick', 'place', 'idle']) for _ in range(num_tasks)],
        "Status": [random.choice(['completed', 'pending', 'error']) for _ in range(num_tasks)],
    }
    return pd.DataFrame(tasks)

# Simulate secure communication log
def generate_comm_log(num_entries=10):
    logs = {
        "Timestamp": [datetime.now().strftime("%Y-%m-%d %H:%M:%S") for _ in range(num_entries)],
        "Data_Type": [random.choice(['sensor', 'command', 'status']) for _ in range(num_entries)],
        "Encrypted": [random.choice([True, False]) for _ in range(num_entries)],
        "Protocol": [random.choice(['MQTT', 'HTTP', 'TLS']) for _ in range(num_entries)]
    }
    return pd.DataFrame(logs)

# Simulate test feedback log
def generate_test_log(num_cases=5):
    feedback = {
        "Timestamp": [datetime.now().strftime("%Y-%m-%d %H:%M:%S") for _ in range(num_cases)],
        "Test_Case": [f"Case_{i+1}" for i in range(num_cases)],
        "Result": [random.choice(['pass', 'fail']) for _ in range(num_cases)],
        "Observer_Notes": [random.choice(['ok', 'needs calibration', 'slow response']) for _ in range(num_cases)],
    }
    return pd.DataFrame(feedback)

# Generate all logs
sensor_df = generate_sensor_data()
robot_df = generate_robotic_log()
comm_df = generate_comm_log()
test_df = generate_test_log()

# Display sample outputs
print("=== Sensor Data ===")
print(sensor_df.head(), "\n")

print("=== Robotic Task Log ===")
print(robot_df.head(), "\n")

print("=== Communication Log ===")
print(comm_df.head(), "\n")

print("=== Test Feedback Log ===")
print(test_df.head(), "\n")

# Optionally save to CSV
sensor_df.to_csv("sensor_data.csv", index=False)
robot_df.to_csv("robotic_tasks.csv", index=False)
comm_df.to_csv("communication_log.csv", index=False)
test_df.to_csv("test_feedback.csv", index=False)

print("All logs have been saved to CSV files.")
