import random
import time
import matplotlib.pyplot as plt

# Function to simulate soil moisture levels
def monitor_soil_moisture():
    soil_data = []
    time_intervals = []
    
    print("Starting Smart Watering System...\n")
    for i in range(20):  # Simulate 20 readings
        soil_moisture = random.randint(0, 100)  # Random moisture percentage
        soil_data.append(soil_moisture)
        time_intervals.append(i + 1)
        
        # Display moisture status
        print(f"Time: {i + 1}, Soil Moisture: {soil_moisture}%")
        if soil_moisture < 40:
            print("Status: Dry - Watering On\n")
        elif soil_moisture > 70:
            print("Status: Wet - Watering Off\n")
        else:
            print("Status: Optimal - No Action Needed\n")
        
        time.sleep(0.5)  # Simulate delay between readings
    
    # Visualize soil moisture data
    visualize_soil_moisture(time_intervals, soil_data)

# Function to visualize soil moisture data
def visualize_soil_moisture(time_intervals, soil_data):
    plt.figure(figsize=(10, 5))
    plt.plot(time_intervals, soil_data, marker='o', linestyle='-', color='b')
    plt.title("Soil Moisture Levels Over Time")
    plt.xlabel("Time Intervals")
    plt.ylabel("Soil Moisture (%)")
    plt.axhline(y=40, color='r', linestyle='--', label="Dry Threshold")
    plt.axhline(y=70, color='g', linestyle='--', label="Wet Threshold")
    plt.legend()
    plt.grid()
    plt.show()

# Main execution
if __name__ == "__main__":
    monitor_soil_moisture()
