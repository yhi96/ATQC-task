# ATQC-task
Manual test cases:

### Test Case 1:
Test Case ID: TC_INV_001
Title: Verify getting the list of devices in the inventory
Pre-conditions: API server is running. Inventory should contain devices.
Test Steps:

Send a GET request to /inventory/devices.
Expected Result:
The API returns a 200 OK status.
The response body is a JSON list containing the devices in the inventory.
The response body is not empty.

### Test Case 2:
Test Case ID: TC_INV_002
Title: Verify adding a new device to the inventory (positive scenario)
Pre-conditions: API server is running. Inventory is empty or does not contain device with ID '123456'.
Test Steps:

Send a POST request to /inventory/devices with the following JSON data:
json body:
{ 
    "id": "123456", 
    "name": "Device Test", 
    "type": "Sensor", 
    "status": "Active" 
}
Check the response for a 201 Created status.
Verify that the response body contains the device data (ID, name, type, status).
Expected Result:
The API returns a 201 Created status.
The device data is correctly returned in the response body.

### Test Case 3:
Test Case ID: TC_INV_003
Title: Verify adding a device with missing required fields (negative scenario)
Pre-conditions: API server is running.
Test Steps:

Send a POST request to /inventory/devices with the following JSON data missing the "id" field:
json body:
{ 
    "name": "Device Test", 
    "type": "Sensor", 
    "status": "Active" 
}
Check the response for a 400 Bad Request status.
Verify that the error message indicates that the "id" field is required.
Expected Result:
The API returns a 400 Bad Request status.
The error message should indicate the missing "id" field.

### Test Case 4:
Test Case ID: TC_INV_004
Title: Verify updating device information (positive scenario)
Pre-conditions: API server is running. Device with ID '123456' exists in the inventory.
Test Steps:

Send a PUT request to /inventory/devices with the following JSON data:
json body:
{ 
    "id": "123456", 
    "name": "Updated Device", 
    "type": "Sensor", 
    "status": "Inactive" 
}
Verify that the API returns a 200 OK status.
Check the response body for updated information: "name" should be "Updated Device", and "status" should be "Inactive".
Expected Result:
The API returns a 200 OK status.
The device information is correctly updated in the response body.

### Test Case 5:
Test Case ID: TC_INV_005
Title: Verify getting the device details by ID (positive scenario)
Pre-conditions: API server is running. Device with ID '123456' exists in the inventory.
Test Steps:

Send a GET request to /inventory/devices/123456.
Verify that the API returns a 200 OK status.
Check that the response body contains the details for the device with ID '123456'.
Expected Result:
The API returns a 200 OK status.
The response body contains the correct details for the device with ID '123456'.
