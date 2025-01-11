# Configuring Business Hours in GHL Growth Tools Zapier App

This guide explains how to set up **business hours** using the custom **GHL Growth Tools Zapier app**. The app allows users to define business hours for different days of the week, ensuring accurate scheduling and availability management.

---

## **How to Input Business Hours**

You will need to input your business hours as a **JSON object** in the provided text box in the Zapier app. Below is the format you should use:

### **JSON Format Example**

```json
[
  {
    "daysOfTheWeek": [1],
    "hours": [
      {
        "openHour": 8,
        "closeHour": 17,
        "openMinute": 0,
        "closeMinute": 0
      }
    ]
  },
  {
    "daysOfTheWeek": [6],
    "hours": [
      {
        "openHour": 10,
        "closeHour": 15,
        "openMinute": 0,
        "closeMinute": 0
      }
    ]
  }
]



