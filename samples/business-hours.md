# **Configuring User Level Business Hours using our GHL Growth Tools Custom Zapier App**

This guide explains how to set up **user-based business hours** using the **create/update user modules** with our custom **[GHL Growth Tools](https://ghlgrowthtools.com)** Zapier app. The app allows users to define business hours for different days of the week, ensuring accurate scheduling and availability management.

---

## **How to Input User Business Hours**

You will need to input your business hours as a **JSON object** in the provided text box in our Zapier app. Below is the format you should use:

![Business Hours Example](https://storage.googleapis.com/msgsndr/cnrSdNBeVI9NoNfiuGsB/media/6791bdd76a58c423bd13d109.png)

### **JSON Format Example**

```json
[
  {
    "days_of_the_week": [1],
    "hours": [
      {
        "open_hour": 8,
        "close_hour": 17,
        "open_minute": 0,
        "close_minute": 0
      }
    ]
  },
  {
    "days_of_the_week": [6],
    "hours": [
      {
        "open_hour": 10,
        "close_hour": 15,
        "open_minute": 0,
        "close_minute": 0
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

---

### **2. hours**

Define the opening and closing hours for each set of days.

Each `hours` object contains:
- **`open_hour`**: The hour when the business opens (in 24-hour format, e.g., 8 for 8 AM, 15 for 3 PM).  
- **`close_hour`**: The hour when the business closes (in 24-hour format, e.g., 17 for 5 PM, 23 for 11 PM).  
- **`open_minute`**: The minute when the business opens. Must be between **0** and **59**.  
- **`close_minute`**: The minute when the business closes. Must be between **0** and **59**.

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
   Must be an array containing a single number between **0** and **6** only.
   
2. **Hours**:
   - `open_hour` and `closeHour` must be between **0** and **23**.
   - `open_minute` and `closeMinute` must be between **0** and **59**.
   
3. **JSON Structure**  
   Ensure the input is valid JSON by wrapping your code inside an object with a key like `businessHours`. You can use [JSONLint](https://jsonlint.com/) to validate your JSON before inputting it into the app.

   **Note:** When pasting your code in Zapier, do **not** include the entire object. Only include the array of days and hours, as shown in the examples above.

   **Example of a wrapped object for validation purposes in [JSONLint](https://jsonlint.com/):**  
   ```json
   {
     "businessHours": [
       {
         "days_of_week": [1],
         "hours": [
           {
             "open_hour": 8,
             "close_hour": 17,
             "open_minute": 0,
             "close_minute": 0
           }
         ]
       }
     ]
   }
   ```

   **Example of what to paste in Zapier:**  
   ```json
   [
     {
       "days_of_week": [1],
       "hours": [
         {
           "open_hour": 8,
           "close_hour": 17,
           "open_minute": 0,
           "close_minute": 0
         }
       ]
     }
   ]
   ```



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

### **Case 2: Business Open on Weekends Only from 10 AM to 2 PM**

```json
[
  {
    "hours": [
      {
        "openHour": 10,
        "closeHour": 14,
        "openMinute": 0,
        "closeMinute": 0
      }
    ],
    "daysOfTheWeek": [6]
  },
  {
    "hours": [
      {
        "openHour": 10,
        "closeHour": 14,
        "openMinute": 0,
        "closeMinute": 0
      }
    ],
    "daysOfTheWeek": [0]
  }
]
```

### **Case 3: Business Has Split Hours on Monday and Tuesday**

In this case, the user operates with a **break in between shifts** (e.g., available in the morning, unavailable for lunch, then available again in the afternoon). The `hours` object allows for multiple time periods in a single day.

```json
[
  {
    "hours": [
      {
        "openHour": 8,
        "closeHour": 12,
        "openMinute": 0,
        "closeMinute": 0
      },
      {
        "openHour": 14,
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
        "closeHour": 12,
        "openMinute": 0,
        "closeMinute": 0
      },
      {
        "openHour": 14,
        "closeHour": 17,
        "openMinute": 0,
        "closeMinute": 0
      }
    ],
    "daysOfTheWeek": [2]
  }
]
```

---

## **Support**

If you encounter any issues or have questions about configuring business hours, please contact our support team at **[support@ghlgrowthtools.com](mailto:support@ghlgrowthtools.com)**.




