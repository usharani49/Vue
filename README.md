## 1. What is a Vue component?

A component is a reusable part of your application's user interface.

For example, Let's take an Employee Management System, will have:

Employee Management System

Dashboard

Total employees         Active          Inactive

# 120                   # 105              # 15



Employee List

| ID  | Name  | Department |
| --- | ----- | ---------- |
| 101 | Rahul | IT         |
| 102 | Priya | HR         |
| 103 | Arjun | Finance    |

Illustrative dashboard layout.

We can divide this screen into reusable components:

- `Dashboard.vue`
- `EmployeeStats.vue`
- `EmployeeTable.vue`
- `EmployeeRow.vue`

Why?

Suppose we need to change the employee table design. We can work on `EmployeeTable.vue` without rewriting the entire application.

This is how professional Vue applications are organized.

## 2. What does a Vue component look like?

Open your `App.vue` file.

A Vue component usually contains three sections:

```
<template>
  <h1>Hello Vue!</h1>
</template>

<script setup>
const message = "Welcome to Vue";
</script>

<style scoped>
h1 {
  color: blue;
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

## 3. Example: Display employee information

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

You use interpolation whenever you want to display JavaScript data in your Vue template.

## 4. Next concept: Display multiple employees

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

## 5. Interview programming practice

JavaScript coding interview

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
