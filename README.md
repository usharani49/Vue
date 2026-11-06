##  What is a Vue component?

A component is a reusable part of our application's user interface.

For example, Let's take an example of Employee Management System ,will have:

Employee Management System

Dashboard

# 120

Total employees

# 105

Active

# 15

Inactive

Employee List

| ID  | Name  | Department |
| --- | ----- | ---------- |
| 101 | Rahul | IT         |
| 102 | Priya | HR         |
| 103 | Arjun | Finance    |


We can divide this screen into reusable components:

- `Dashboard.vue`
- `EmployeeStats.vue`
- `EmployeeTable.vue`
- `EmployeeRow.vue`

Why?

Suppose we need to change the employee table design. We can work on `EmployeeTable.vue` without rewriting the entire application.

This is how professional Vue applications are organized.

##  What does a Vue component look like?
Create App.vue file.

A Vue component usually contains three sections:

```
<template>
  <h1>Hello World</h1>
  <h2>{{ msg }}</h2>
</template>

<script setup>
 const msg="Welcome to vue"
</script>

<style scoped>
 h1 {
  color: blue;
 }
 h2{
  color: green;
 }
</style>
```

Let's understand them.

| Section          | Purpose                    |
| ---------------- | -------------------------- |
| `<template>`     | What appears on the screen |
| `<script setup>` | JavaScript logic           |
| `<style scoped>` | CSS for this component     |

`scoped` means the styles apply to this component rather than accidentally affecting other components.

Here, {{ msg }} connects the JavaScript variable to the HTML output. This is called interpolation.

##  Example: Display employee information

Replace the contents of `App.vue` temporarily with this:

```
<template>
  <div>
    <h1>Employee Management System</h1>

    <h2>{{ employeeName }}</h2>
    <p>Department: {{ department }}</p>
    <p>Salary: ₹{{ salary }}</p>
  </div>
</template>

<script setup>
const employeeName = "Rahul";
const department = "Frontend";
const salary = 35000;
</script>

<style scoped>
h1 {
  color: blue;
}

div {
  padding: 20px;
}
</style>
```

What is happening?

- `employeeName` stores Rahul.
- `department` stores Frontend.
- `salary` stores 35000.
- `{{ employeeName }}` displays the JavaScript value inside the template.

This is called interpolation.

We use interpolation whenever we want to display JavaScript data in our Vue template.

## Where does JavaScript logic get used in real projects?
For example, suppose our Employee Management System has 100 employees.

JavaScript handles:
- Employee data.
- Calculating total employees.
- Filtering employees by department.
- Searching employees.
- Processing API responses.
  
Vue displays the results on the screen.

##  Display multiple employees

Real applications have multiple employees. We don't create separate HTML elements manually for every employee.

We use arrays and Vue's `v-for`.

Example:

```
<template>
  <div>
    <h1>Employee List</h1>

    <div v-for="employee in employees" :key="employee.id">
      <h3>{{ employee.name }}</h3>
      <p>{{ employee.department }}</p>
    </div>
  </div>
</template>

<script setup>
const employees = [
  {
    id: 1,
    name: "Rahul",
    department: "IT"
  },
  {
    id: 2,
    name: "Priya",
    department: "HR"
  },
  {
    id: 3,
    name: "Arjun",
    department: "Finance"
  }
];
</script>
```

Important concepts:

- `employees` is an array.
- Each employee is an object.
- `v-for` repeats the HTML for every employee.
- `employee` represents the current employee.
- `:key="employee.id"` gives Vue a unique identifier for each row.

This pattern appears frequently in company projects.

##  Interview programming practice

Imagine an interviewer gives you this employee data:

```
const employees = [
  { name: "Rahul", department: "IT" },
  { name: "Priya", department: "HR" },
  { name: "Arjun", department: "IT" },
  { name: "Sneha", department: "Finance" }
];
```

Question: Return only employees who belong to the IT department.

Example solution:

```
const itEmployees = employees.filter(
  employee => employee.department === "IT"
);

console.log(itEmployees);
```

Output:

```
[
  { name: "Rahul", department: "IT" },
  { name: "Arjun", department: "IT" }
]
```

Why use `filter()`?

It checks every array element and returns a new array containing only the elements that satisfy the condition.


## Your  tasks

# Task 1: Employee information

Create an employee object with:

- Name
- Employee ID
- Department
- Salary

Display all four values in `App.vue`.

# Task 2: Employee list

Create an array containing five employees.

Display all five using `v-for`.

# Task 3: Department filtering

Display only employees belonging to the IT department using JavaScript `filter()`.

# Task 4: Explain the concepts

Tell me in your own words:

1. What is a Vue component?
2. What is the purpose of `<template>`?
3. What is interpolation?
4. Why do we use `v-for`?
5. Why do we use `:key`?
6. What does `filter()` do?


## Your tasks Answers

# Task 1: Display employee information

Replace your `App.vue` contents with:

```
<template>
  <div>
    <h1>Employee Management System</h1>

    <h2>Employee Details</h2>

    <p>Name: {{ employee.name }}</p>
    <p>Employee ID: {{ employee.id }}</p>
    <p>Department: {{ employee.department }}</p>
    <p>Salary: ₹{{ employee.salary }}</p>
  </div>
</template>

<script setup>
const employee = {
  name: "Rahul",
  id: 101,
  department: "IT",
  salary: 35000
};
</script>

<style scoped>
div {
  padding: 20px;
}

h1 {
  color: blue;
}
</style>
```

Expected output:

# Employee Management System

Employee Details

- Name: Rahul
- Employee ID: 101
- Department: IT
- Salary: ₹35,000

Explanation:

- `employee` is a JavaScript object.
- It contains four properties.
- `employee.name` accesses the name property.
- `{{ employee.name }}` displays its value in the browser.

# Task 2: Display five employees

```
<template>
  <div>
    <h1>Employee List</h1>

    <div
      v-for="employee in employees"
      :key="employee.id"
      class="employee-card"
    >
      <h3>{{ employee.name }}</h3>
      <p>ID: {{ employee.id }}</p>
      <p>Department: {{ employee.department }}</p>
      <p>Salary: ₹{{ employee.salary }}</p>
    </div>
  </div>
</template>

<script setup>
const employees = [
  {
    id: 101,
    name: "Rahul",
    department: "IT",
    salary: 35000
  },
  {
    id: 102,
    name: "Priya",
    department: "HR",
    salary: 40000
  },
  {
    id: 103,
    name: "Arjun",
    department: "Finance",
    salary: 45000
  },
  {
    id: 104,
    name: "Sneha",
    department: "IT",
    salary: 38000
  },
  {
    id: 105,
    name: "Kiran",
    department: "Marketing",
    salary: 30000
  }
];
</script>

<style scoped>
.employee-card {
  border: 1px solid #ccc;
  padding: 15px;
  margin-bottom: 10px;
  border-radius: 8px;
}
</style>
```

Explanation:

`v-for="employee in employees"` repeats the employee card for every item in the array.

`:key="employee.id"` gives every rendered employee a unique key. Vue uses it to track list items efficiently when the list changes.

# Task 3: Filter IT department employees

```
<template>
  <div>
    <h1>IT Department Employees</h1>

    <div
      v-for="employee in itEmployees"
      :key="employee.id"
      class="employee-card"
    >
      <h3>{{ employee.name }}</h3>
      <p>Department: {{ employee.department }}</p>
    </div>
  </div>
</template>

<script setup>
const employees = [
  { id: 101, name: "Rahul", department: "IT" },
  { id: 102, name: "Priya", department: "HR" },
  { id: 103, name: "Arjun", department: "IT" },
  { id: 104, name: "Sneha", department: "Finance" }
];

const itEmployees = employees.filter(
  employee => employee.department === "IT"
);
</script>

<style scoped>
.employee-card {
  border: 1px solid #ccc;
  padding: 10px;
  margin-bottom: 10px;
}
</style>
```

Expected output:

IT Department Employees

Rahul

IT

Arjun

IT

How `filter()` works:

1. It checks Rahul. Department is IT. Keep him.
2. It checks Priya. Department is HR. Exclude her.
3. It checks Arjun. Department is IT. Keep him.
4. It checks Sneha. Department is Finance. Exclude her.

The result is a new array containing Rahul and Arjun.

# Task 4: Interview answers

| Question                    | Answer                                                            |
| --------------------------- | ----------------------------------------------------------------- |
| 1. What is a Vue component? | A reusable piece of a Vue application's user interface.           |
| 2. Purpose of `<template>`? | Defines the HTML-like structure displayed on the screen.          |
| 3. What is interpolation?   | Displaying JavaScript values inside a template using `{{ }}`.     |
| 4. Why use `v-for`?         | To render lists by repeating elements for array items.            |
| 5. Why use `:key`?          | To give Vue a unique identity for each rendered list item.        |
| 6. What does `filter()` do? | Returns a new array containing elements that satisfy a condition. |

# Additional real-time interview coding questions

These are important variations of what we learned.

## Question 1: Find employees earning more than ₹35,000.

```
const highSalaryEmployees = employees.filter(
  employee => employee.salary > 35000
);
```

## Question 2: Find an employee with ID 103.

```
const employee = employees.find(
  employee => employee.id === 103
);
```

Difference:

- `filter()` returns an array.
- `find()` returns the first matching element or `undefined`.

## Question 3: Get only employee names.

```
const employeeNames = employees.map(
  employee => employee.name
);
```

Output:

```
["Rahul", "Priya", "Arjun", "Sneha"]
```

Difference:

- `map()` transforms every element.
- `filter()` selects matching elements.
- `find()` returns the first matching element.

These three methods are essential for frontend development and coding interviews.
