# Reading and Extracting Data from Complex JSON Files in Python.
Certainly! Here's a beginner-friendly guide on reading and extracting data from a JSON file with various types of keys and values. This guide will help you understand how to work with nested data and different data types within JSON.
## 1. Introduction
JSON (JavaScript Object Notation) is a widely-used format for data interchange. It is easy to read and write, making it popular for data exchange between systems. Python’s json module allows you to work with JSON data effortlessly.
## 2. Sample JSON File
We'll use the following complex JSON file named complex_data.json:
```
{
  "company": {
    "name": "Tech Solutions",
    "location": "New York",
    "departments": [
      {
        "name": "HR",
        "employees": [
          {
            "id": 1,
            "name": "John Doe",
            "position": "HR Manager",
            "salary": 50000
          },
          {
            "id": 2,
            "name": "Jane Doe",
            "position": "HR Assistant",
            "salary": 40000
          }
        ]
      },
      {
        "name": "Finance",
        "employees": [
          {
            "id": 3,
            "name": "Alice Smith",
            "position": "Finance Manager",
            "salary": 70000
          },
          {
            "id": 4,
            "name": "Bob Johnson",
            "position": "Accountant",
            "salary": 55000
          }
        ]
      }
    ],
    "projects": [
      {
        "id": "P001",
        "name": "Project Alpha",
        "budget": 100000,
        "deadline": "2024-12-31"
      },
      {
        "id": "P002",
        "name": "Project Beta",
        "budget": 150000,
        "deadline": "2025-06-30"
      }
    ]
  }
}
```
## 3. Reading JSON Data
### 3.1. Import the JSON Module
First, you need to import the json module:
```
import json
```

### 3.2. Open and Read the JSON File
Use the following code to read the JSON file:
```
with open('complex_data.json', 'r') as file:
    data = json.load(file)
```
This code snippet opens complex_data.json in read mode and loads its content into the data variable as a Python dictionary.

## 4. Extracting Data
### 4.1. Accessing Top-Level Elements
To access the top-level elements of the JSON file:
```
company_name = data['company']['name']
location = data['company']['location']
print(f"Company: {company_name}")
print(f"Location: {location}")
```
Here, ```data['company']``` accesses the value associated with the "company" key, which is a dictionary. From there, ```['name']``` and ```['location']``` access specific fields.

### 4.2. Accessing Nested Lists and Dictionaries
To extract and print department information and employees:
```
departments = data['company']['departments']
for department in departments:
    print(f"Department: {department['name']}")
    for employee in department['employees']:
        print(f"ID: {employee['id']}, Name: {employee['name']}, Position: {employee['position']}, Salary: {employee['salary']}")
```
•	```data['company']['departments']``` accesses the list of departments.
•	Each department is a dictionary containing its own list of employees.
•	The nested loops extract and print employee details.

### 4.3. Accessing Projects Data
To access and print project information:
```
projects = data['company']['projects']
for project in projects:
    print(f"Project ID: {project['id']}, Name: {project['name']}, Budget: {project['budget']}, Deadline: {project['deadline']}")
```

•	```data['company']['projects']``` accesses the list of projects.
•	Each project is a dictionary with various fields such as id, name, budget, and deadline.

## 5. Writing JSON Data
If you need to modify and write data back to a JSON file, follow these steps:
### 5.1. Convert Python Object to JSON String
```
json_string = json.dumps(data, indent=4)
```

The indent parameter formats the JSON string to be more readable.

### 5.2. Write JSON Data to File
```
with open('updated_complex_data.json', 'w') as file:
    file.write(json_string)
```

This writes the updated JSON string to a new file.

## 6. Full Example Code
Here’s a complete Python script that reads, processes, and writes JSON data:
```
import json

# Read JSON data from file
with open('complex_data.json', 'r') as file:
    data = json.load(file)

# Extract and print company details
company_name = data['company']['name']
location = data['company']['location']
print(f"Company: {company_name}")
print(f"Location: {location}")

# Extract and print departments and employees
departments = data['company']['departments']
for department in departments:
    print(f"Department: {department['name']}")
    for employee in department['employees']:
        print(f"    ID: {employee['id']}, Name: {employee['name']}, Position: {employee['position']}, Salary: {employee['salary']}")

# Extract and print projects
projects = data['company']['projects']
for project in projects:
    print(f"Project ID: {project['id']}, Name: {project['name']}, Budget: {project['budget']}, Deadline: {project['deadline']}")

# Write JSON data to a new file
json_string = json.dumps(data, indent=4)
with open('updated_complex_data.json', 'w') as file:
    file.write(json_string)
```

## 7. Conclusion
Understanding and working with complex JSON structures involves navigating nested dictionaries and lists. By practicing these techniques, you’ll become proficient in handling various types of data in JSON format.




