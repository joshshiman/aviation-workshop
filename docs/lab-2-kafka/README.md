# Lab 2: Kafka Consumer

**Duration:** 30-45 minutes  
**Objective:** Build a Kafka consumer to process real-time flight and weather events

---

## Overview

In this lab, you'll:
1. Create a Kafka consumer using the prebuilt helper
2. Process weather and flight events
3. Print and inspect the data structure
4. Understand the event flow

---

## Prerequisites

- ✅ Completed Lab 1 (environment setup)
- ✅ Virtual environment activated (`(venv)` in prompt)
- ✅ Kafka connection tested successfully

---

## Part 1: Understanding the Data (5 min)

### What Data Are We Consuming?

Kafka is streaming two types of real-time events:

**1. Weather Events**
```json
{
  "event_id": "weather_1747689600_4523",
  "timestamp": "2026-05-19T20:30:00.000Z",
  "city": "Toronto",
  "latitude": 43.7012,
  "longitude": -79.4321,
  "condition": "Thunderstorm",
  "severity": "High",
  "visibility_km": 2.1,
  "wind_speed_kmh": 52.3,
  "temperature_c": 16.8,
  "hazard_radius_km": 35.7
}
```

**2. Flight Events**
```json
{
  "event_id": "flight_1747689605_7821",
  "timestamp": "2026-05-19T20:30:05.000Z",
  "flight_id": "AC456",
  "airline": "AC",
  "status": "On Time",
  "departure_city": "Toronto",
  "arrival_city": "Vancouver",
  "current_latitude": 47.2341,
  "current_longitude": -98.5432,
  "altitude_ft": 35000,
  "speed_kmh": 850,
  "heading_degrees": 285,
  "passengers": 142
}
```

> 💡 **Key Fields for Later:**
> - Weather: `latitude`, `longitude`, `severity`, `hazard_radius_km`
> - Flight: `current_latitude`, `current_longitude`, `flight_id`

---

## Part 2: Create Your First Consumer with IBM Bob (15 min)

### Step 1: Open IBM Bob

Open IBM Bob (your agentic IDE) in VS Code.

### Step 2: Use Bob to Create the Consumer

Copy and paste this prompt into Bob's chat:

```bash
Create a file called consumer.py in the workshop/backend directory with the following requirements:

1. Import os, json, KafkaConsumer from kafka, and dotenv.load_dotenv
2. Load environment variables at the module level
3. Create a function process_weather_event(event) that prints:
   - Weather Event header with emoji
   - City, Condition, Severity
   - Location (latitude, longitude with 4 decimal places)
   - Visibility in km
4. Create a function process_flight_event(event) that prints:
   - Flight Event header with emoji
   - Flight ID and Status
   - Route (departure_city → arrival_city)
   - Current location (current_latitude, current_longitude with 4 decimal places)
   - Altitude in feet
5. Create a main() function that:
   - Prints a startup banner
   - Gets WEATHER_TOPIC and FLIGHT_TOPIC from environment (defaults: weather_events, flight_telemetry)
   - Creates a SINGLE KafkaConsumer for BOTH topics with these settings:
     * bootstrap_servers from KAFKA_BOOTSTRAP_SERVERS env var
     * security_protocol='SASL_SSL'
     * sasl_mechanism='PLAIN'
     * sasl_plain_username from KAFKA_SASL_USERNAME env var
     * sasl_plain_password from KAFKA_SASL_PASSWORD env var
     * value_deserializer=lambda m: json.loads(m.decode('utf-8'))
     * group_id with unique timestamp
     * auto_offset_reset='earliest'
     * enable_auto_commit=True
   - Uses the consumer as an iterator: for message in consumer:
   - Checks message.topic to determine if it's weather or flight
   - Calls the appropriate process function
   - Handles KeyboardInterrupt to close consumer cleanly
6. Add if __name__ == "__main__": main()

IMPORTANT: Use the iterator pattern (for message in consumer:) NOT poll(). This ensures messages are consumed correctly.

Use clear formatting with emojis (🌤️ for weather, ✈️ for flights) and proper spacing between events.
```

> 💡 **Tip:** Bob will generate the code for you! Review it to make sure it matches the requirements.

### Step 3: Review Bob's Generated Code

Bob should create a file similar to this structure:

```python
# Bob will generate:
# - Imports (os, json, KafkaConsumer, dotenv)
# - process_weather_event() function
# - process_flight_event() function
# - main() function with:
#   * Single consumer for both topics
#   * Iterator pattern (for message in consumer:)
#   * Topic-based routing
# - Proper error handling
```

**Expected file location:** `workshop/backend/consumer.py`

---

## Part 3: Test Your Consumer (10 min)

### Step 1: Run Your Consumer

In your terminal (with venv activated):

```bash
cd workshop/backend
python consumer.py
```

### Step 3: Observe the Output

You should see events streaming in:

```
🚀 Starting Aviation Warning System Consumer...
============================================================
📡 Connecting to Kafka topics:
   - weather_events
   - flight_telemetry
✅ Connected! Listening for events...
============================================================

✈️  Flight Event:
   Flight: AC456
   Status: On Time
   Route: Toronto → Vancouver
   Location: (47.2341, -98.5432)
   Altitude: 35000ft

🌤️  Weather Event:
   City: Toronto
   Condition: Thunderstorm
   Severity: High
   Location: (43.7012, -79.4321)
   Visibility: 2.1km

✈️  Flight Event:
   Flight: WS789
   Status: Delayed
   Route: Montreal → Calgary
   Location: (45.8923, -95.1234)
   Altitude: 38000ft
```

### Step 4: Stop the Consumer

Press `Ctrl+C` to stop:

```
⏹️  Stopping consumer...
✅ Consumer closed cleanly
```

---

## Part 4: Understanding the Code (5 min)

### Key Concepts

**1. Single Consumer for Multiple Topics**
```python
consumer = KafkaConsumer(
    weather_topic,
    flight_topic,
    bootstrap_servers=...,
    # ... other config
)
```
- One consumer can subscribe to multiple topics
- More efficient than separate consumers
- Handles all Kafka connection details

**2. The Iterator Pattern**
```python
for message in consumer:
    if message.topic == weather_topic:
        process_weather_event(message.value)
    elif message.topic == flight_topic:
        process_flight_event(message.value)
```
- `for message in consumer:` blocks until messages arrive
- Automatically handles partition assignment
- Much simpler than manual `poll()` loops
- `message.topic` tells you which topic the message came from
- `message.value` contains the actual event data (already deserialized to dict)

**3. Auto Offset Reset**
```python
auto_offset_reset='earliest'
```
- Starts reading from the beginning of the topic
- Ensures you don't miss any messages
- Perfect for development and testing

**4. Graceful Shutdown**
```python
except KeyboardInterrupt:
    consumer.close()
```
- Catches `Ctrl+C` signal
- Closes consumer cleanly
- Prevents connection leaks

---

## Challenge: Add Event Counting (Optional, 5 min)

Want to track how many events you've processed? Ask Bob to add counters:

```bash
Modify consumer.py to add event counting:

1. Add weather_count and flight_count variables initialized to 0 in main()
2. Increment weather_count each time a weather event is processed
3. Increment flight_count each time a flight event is processed
4. In the KeyboardInterrupt handler, print final statistics showing:
   - Total weather events processed
   - Total flight events processed
   - Grand total of all events
5. Use emoji 📊 for the stats header
```

Bob will update your code to include the counters!

---

## Troubleshooting

### Issue: No events appearing

**Checklist:**
- [ ] Are you in the correct directory (`workshop/backend`)?
- [ ] Is your virtual environment activated?
- [ ] Are your Kafka credentials correct in `.env`?
- [ ] Is the Kafka data stream active? (ask instructor)

**Solution:**
```bash
# Test Kafka connection
python kafka_utils.py

# If connection works but no data, wait a moment for events to arrive
```

### Issue: "ModuleNotFoundError: No module named 'kafka_utils'"

**Solution:**
```bash
# Make sure you're in the backend directory
cd workshop/backend

# Run from there
python consumer.py
```

### Issue: Consumer connects but no data

**Possible causes:**
- Data stream not yet started
- Topics are empty
- Consumer group offset issue

**Solution:**
```bash
# Wait 10-15 seconds for events to arrive
# Or ask instructor to verify data stream is active
```

---

## Verification Checklist

Before moving to Lab 3, ensure you:

- [ ] Created `consumer.py` file
- [ ] Successfully connected to both Kafka topics
- [ ] Saw weather events printing
- [ ] Saw flight events printing
- [ ] Understand the polling loop pattern
- [ ] Can stop consumer cleanly with Ctrl+C

---

## What You Learned

✅ **Kafka Consumer Patterns**
- Creating consumers with configuration
- Polling for messages
- Processing events in real-time

✅ **Event Processing**
- Handling different event types
- Extracting relevant data
- Printing structured output

✅ **Code Organization**
- Separating concerns (process functions)
- Using helper modules (kafka_utils)
- Clean shutdown handling

---

## Next Steps

🎉 **Great job!** You're now consuming real-time aviation data.

In **Lab 3**, you'll build AI agents using watsonx Orchestrate to:
- Analyze weather severity
- Assess flight risks
- Generate intelligent alerts

---

## Quick Reference

**Run Consumer:**
```bash
cd workshop/backend
python consumer.py
```

**Stop Consumer:**
```
Ctrl+C
```

**Check Connection:**
```bash
python kafka_utils.py
```

---

**Lab 2 Complete!** ✈️🌤️