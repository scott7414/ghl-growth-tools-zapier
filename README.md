# GHL JSON API Integrations

This repository contains **JSON configurations**, **code snippets**, and **examples** for integrating with the **Go High Level (GHL) API** using tools like **Zapier**, **Make (Integromat)**, and custom-built applications.

The goal is to provide a centralized collection of reusable configurations and ready-to-use examples for common use cases, such as handling user settings, business hours, calendars, and more.

---

## **Contents**

### **1. Zapier Integrations**
- `user-settings.js`: Code to manage user-specific settings through the GHL API.
- `business-hours.js`: Code for handling business hours in GHL via Zapier.
- `location-wise-open-hours.json`: Example JSON for defining open hours by location.

### **2. Make (Integromat) Integrations**
- `ghl-custom-fields.json`: JSON template for syncing custom fields between GHL and other services.
- `calendar-sync.json`: Example JSON for syncing calendars using the GHL API.

### **3. Documentation**
- `input-examples.md`: Examples of user input JSON for various API endpoints.
- `api-usage-guide.md`: A guide on how to interact with the GHL API, including authentication, endpoint usage, and common errors.

---

## **How to Use**

### **1. Using with Zapier**
1. Copy the relevant code snippet from the `zapier/` folder.
2. Paste it into your Zapier custom app’s code editor.
3. Follow the provided documentation to configure fields and input data.

### **2. Using with Make (Integromat)**
1. Download the JSON templates from the `make/` folder.
2. Import them into your Make scenario.
3. Modify the input fields as needed based on your specific requirements.

---

## **Example JSON Configuration**

Here’s a sample JSON for setting location-wise user business hours in Zapier using our GHL Growth Tools Custom Zapier APP:

```json
{
  "locationWiseOpenHours": {
    "wAcbT1ozUU5MKeOM1uT5": [
      {
        "hours": [
          {
            "openHour": 8,
            "closeHour": 17,
            "openMinute": 0,
            "closeMinute": 0
          }
        ],
        "daysOfTheWeek": [1, 2, 3, 4, 5]
      }
    ]
  }
}

