# Configuring User Leve Business Hours in GHL Growth Tools Custom Zapier App

This guide explains how to set up **user-based business hours** using the custom **GHL Growth Tools Zapier app**. The app allows users to define business hours for different days of the week, ensuring accurate scheduling and availability management.

---

## **How to Input User Business Hours**

You will need to input your business hours as a **JSON object** in the provided text box in our Zapier app. Below is the format you should use:

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
```

---

## **Explanation of Fields**

### **1. daysOfTheWeek**

Specify the days of the week using numbers:

- **0** = Sunday  
- **1** = Monday  
- **2** = Tuesday  
- **3** = Wednesday  
- **4** = Thursday  
- **5** = Friday  
- **6** = Saturday  

You can specify multiple days in an array. For example:
- `[1, 2, 3, 4, 5]` represents Monday through Friday.
- `[0, 6]` represents Sunday and Saturday.

---

### **2. hours**

Define the opening and closing hours for each set of days.

Each `hours` object contains:
- **`openHour`**: The hour when the business opens (in 24-hour format, e.g., 8 for 8 AM, 15 for 3 PM).  
- **`closeHour`**: The hour when the business closes (in 24-hour format, e.g., 17 for 5 PM, 23 for 11 PM).  
- **`openMinute`**: The minute when the business opens. Must be between **0** and **59**.  
- **`closeMinute`**: The minute when the business closes. Must be between **0** and **59**.

---

### **3. 24-Hour Time Format**

Use **24-hour time** (also known as "military time") to specify the hours.

- Examples:  
  - `8` = 8 AM  
  - `15` = 3 PM  
  - `23` = 11 PM  

---

## **Validation Rules**

1. **Days of the Week**:  
   Must be an array containing numbers between **0** and **6** only.
   
2. **Hours**:
   - `openHour` and `closeHour` must be between **0** and **23**.
   - `openMinute` and `closeMinute` must be between **0** and **59**.
   
3. **JSON Structure**:  
   Ensure the input is valid JSON. You can use [JSONLint](https://jsonlint.com/) to validate your JSON before inputting it into the app.

---

## **Example Use Cases**

### **Case 1: Business Open Monday to Friday, 8 AM to 5 PM**

```json
[
  {
    "hours": [
      {
        "openHour": 8,
        "closeHour": 17,
        "openMinute": 0,
        "closeMinute": 0
      }
    ],
    "daysOfTheWeek": [1]
  },
  {
    "hours": [
      {
        "openHour": 8,
        "closeHour": 17,
        "openMinute": 0,
        "closeMinute": 0
      }
    ],
    "daysOfTheWeek": [2]
  },
  {
    "hours": [
      {
        "openHour": 8,
        "closeHour": 17,
        "openMinute": 0,
        "closeMinute": 0
      }
    ],
    "daysOfTheWeek": [3]
  },
  {
    "hours": [
      {
        "openHour": 8,
        "closeHour": 17,
        "openMinute": 0,
        "closeMinute": 0
      }
    ],
    "daysOfTheWeek": [4]
  },
  {
    "hours": [
      {
        "openHour": 8,
        "closeHour": 17,
        "openMinute": 0,
        "closeMinute": 0
      }
    ],
    "daysOfTheWeek": [5]
  }
]

```

### **Case 2: Business Open on Weekends Only from 10 am to 2 pm**

```json
[
  {
    "daysOfTheWeek": [3],
    "hours": [
      {
        "openHour": 10,
        "closeHour": 14,
        "openMinute": 0,
        "closeMinute": 0
      }
    ]
  }
]
```

---

## **Support**

If you encounter any issues or have questions about configuring business hours, please contact our support team @ support@ghlgrowthtools.com.




