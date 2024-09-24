# Software Quality Control Engineer Homework Assignment
## Objective:
You are tasked with ensuring the quality of a robotic arm control system that performs pick-and-place operations on a conveyor belt. The system uses the following key technologies:

- REST API to interact with the robotic arm for triggering actions.
- OPC UA for communicating with the conveyor belt system.
- Real-time data streaming from sensors to monitor the operation.
- The software runs in a Linux-based environment, with logs captured via systemd and other tools.

Your task will be to create a comprehensive QC strategy, automate tests, and debug issues within the system.

## 1. Test Plan Creation for Integrated Systems
You are responsible for creating a test plan for the robotic arm software interacting with the conveyor belt system using both the REST API and OPC UA protocols. The system consists of two components that must work seamlessly together for the entire operation.

### Task:

- Define the scope of your testing based on the following operations:
  - The robotic arm picks objects from a moving conveyor belt.
  - The system must detect if the object is present, using vision sensors and position data from OPC UA.
  - The system must trigger corrective actions if no object is detected within the specified timeframe.
- Create test cases that cover the following:
  - Integration tests between the REST API controlling the robotic arm and the OPC UA controlling the conveyor.
  - Error handling tests for communication failures between the robotic arm and the conveyor system.
  - Real-time data validation to ensure sensor data is accurately processed.
- Consider edge cases where:
  - The conveyor belt speeds up unexpectedly.
  - The robotic arm misses the object due to latency in sensor feedback.
  - Communication timeout between OPC UA server and the robotic arm control system.
  - 
### Deliverable: 
A comprehensive test plan including test scenarios, test cases, expected results, and priority for each test case.

## 2. Develop Test Cases for the REST API (Detailed)
Develop detailed test cases for the following REST API endpoints, which control the robotic arm:

- Start operation (POST /robot/start): Triggers the robotic arm to start its operation.
- Get system status (GET /system/status): Returns overall system status, including the status of the robotic arm and conveyor belt (Idle, Active, Error).
- Stop operation (POST /robot/stop): Stops the robotic arm and pauses the conveyor belt.
### Task:
- Write detailed test cases that cover the following:
  - API validation: Check for correct response codes (200, 400, 500) and body content.
  - Timeout scenarios: Ensure the system handles scenarios where the API doesn't respond within expected timeframes.
  - Concurrent requests: Simulate concurrent API requests (e.g., two start requests sent back-to-back) and ensure the system handles them correctly.
  - State validation: Test transitions between states (Idle, Active, Error) and confirm the correct state is returned after each operation.
  - Error injection: Propose test cases for situations where communication between the robotic arm and conveyor fails, and the API must report it accurately.
  - 
### Deliverable: 
A test case document for the REST API including input values, preconditions, steps, expected outcomes, and validation steps.

## 3. Test Automation Plan for REST API and OPC UA Systems
You will now focus on creating an automation plan for the API and OPC UA systems, emphasizing scalability and maintainability.

### Task:
- Propose a detailed automation strategy for:
  - API Testing: Use Python-based frameworks such as Pytest or Robot Framework to automate the REST API test cases.
  - OPC UA Protocol Testing: Use tools such as Open62541 or Prosys OPC UA Client for validating the conveyor belt’s operation.
Include the following in your automation plan:
Test environment setup: Specify how the automation scripts will run in a CI/CD pipeline (e.g., using Docker for the robotic arm simulator, connecting to OPC UA server).
Dependency management: Describe how to handle dependencies like Python packages and ensure the test environment is properly isolated.
Error handling and recovery: Explain how you would automate detection of failed OPC UA commands and attempt retries.
Scalability considerations: Explain how you would expand the test suite as new features are added or when dealing with multiple robotic arms.

### Deliverable: 
A 2-3 page automation strategy proposal detailing tools, steps for automation, test framework, and CI/CD integration.

## 4. Bug Investigation and Reporting (Log Analysis)
You are provided with a log file from the robotic arm control system showing an operational error where the arm failed to pick an object from the conveyor.

### Task:
Investigate the error in the provided log file (attached separately).
Analyze the root cause of the failure using the logs, identify whether it was due to sensor miscommunication, timing issues, or API misbehavior.
Write a detailed bug report that includes:
Steps to reproduce (based on the logs and available information).
Expected behavior vs. actual behavior.
Impact of the bug on overall system performance.
Suggested fixes or areas for further investigation.
### Deliverable: 
A bug report document that outlines your investigation, findings, and potential resolutions.

## 5. Real-time Data Streaming Validation
The robotic arm receives real-time sensor data to ensure it correctly identifies the objects on the conveyor belt. You are responsible for validating that this real-time data is accurate.

### Task:
Design a test to validate the real-time data stream from the vision sensors.
Consider the following:
The robotic arm must pick up objects within a 1-second window from when the sensor detects the object.
Sensor data simulation: Propose how you would simulate sensor data and introduce noise into the system to test robustness.
Data validation: Ensure the sensor feedback is accurate and consistent across different belt speeds and lighting conditions.
### Deliverable: 
A document describing the test design and methods for simulating and validating the real-time data.

## 6. Write an Automation Script for a Test (Optional):

Choose one of the API test cases from Task 2 and write a fully functional automation script using Python with unittest, pytest, or Robot Framework.

### Deliverable: 
The test script, including instructions to run it, in a GitHub repository or as a file.

### Submission Requirements:
Format: All tasks should be submitted in PDF format, except for the optional bonus task, which can be submitted as a script file or GitHub link.
Deadline: Submit your assignment within 5 days.
