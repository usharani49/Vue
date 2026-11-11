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

Task 1: Employee information

Create an employee object with:

- Name
- Employee ID
- Department
- Salary

Display all four values in `App.vue`.

Task 2: Employee list

Create an array containing five employees.

Display all five using `v-for`.

Task 3: Department filtering

Display only employees belonging to the IT department using JavaScript `filter()`.

Task 4: Explain the concepts

Tell me in your own words:

1. What is a Vue component?
2. What is the purpose of `<template>`?
3. What is interpolation?
4. Why do we use `v-for`?
5. Why do we use `:key`?
6. What does `filter()` do?


## Your tasks Answers

Task 1: Display employee information

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

Task 2: Display five employees

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

Task 3: Filter IT department employees

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

Task 4: Interview answers

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

console.log(highSalaryEmployees)
```

## Question 2: Find an employee with ID 103.

```
const employee = employees.find(
  employee => employee.id === 103
);

console.log(employee)
```

Difference:

- `filter()` returns an array.
- `find()` returns the first matching element or `undefined`.

## Question 3: Get only employee names.

```
const employeeNames = employees.map(
  employee => employee.name
);

console.log(employeeNames)
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


# Vue 3 Reactivity and `ref()`

Goal: Understand how Vue updates the screen when data changes.

## 1. First, understand the problem

Suppose you have an employee application.

Initially, the employee count is 5.

When you add a new employee, the count should become 6 automatically.

How does Vue know that the data changed?

This is where reactivity comes in.

## 2. Normal JavaScript variable vs Vue `ref()`

First, consider normal JavaScript:

```
let count = 5;

count = 6;

console.log(count);
```

Output:

```
6
```

The variable changes successfully.

But Vue doesn't automatically track this ordinary variable and update the screen when it changes.

Now let's use Vue's `ref()`.

```
<template>
  <h1>Employee Count: {{ count }}</h1>

  <button @click="count++">
    Add Employee
  </button>
</template>

<script setup>
import { ref } from "vue";

const count = ref(5);
</script>
```

When you click the button:

- Initially, count is 5.
- First click, count becomes 6.
- Second click, count becomes 7.
- Vue automatically updates the displayed value.

Try it: Employee counter

Employee count

# 5

Remove   Add employee

This is a demonstration of the expected counter behaviour.

## 3. What exactly is `ref()`?

`ref()` is a Vue function that creates reactive data.

Syntax:

```
import { ref } from "vue";

const variableName = ref(initialValue);
```

Example:

```
const employeeName = ref("Rahul");
const salary = ref(35000);
const isActive = ref(true);
```

Important: In JavaScript, access or modify a ref's value using `.value`.

```
console.log(employeeName.value);

employeeName.value = "Priya";

salary.value = 40000;
```

But inside the Vue template, you don't need `.value`.

```
<template>
  <h2>{{ employeeName }}</h2>
  <p>{{ salary }}</p>
</template>
```

Vue automatically unwraps refs in templates.

## 4. Real company example: Employee status

Imagine your manager asks:

"Add a button to activate or deactivate an employee."

We can implement it using `ref()`.

```
<template>
  <div>
    <h2>Employee: Rahul</h2>

    <p>Status: {{ isActive ? "Active" : "Inactive" }}</p>

    <button @click="toggleStatus">
      Change Status
    </button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const isActive = ref(true);

function toggleStatus() {
  isActive.value = !isActive.value;
}
</script>
```

Understand this line:

```
isActive.value = !isActive.value;
```

- If the value is `true`, it changes to `false`.
- If the value is `false`, it changes to `true`.

This is called toggling.

## 5. Interview questions

Q1. What is reactivity in Vue?

Reactivity means Vue tracks changes in reactive data and updates the relevant parts of the user interface automatically.

Q2. What is `ref()`?

`ref()` creates a reactive reference to a value in Vue 3.

Q3. Why do we use `.value`?

We use `.value` in JavaScript to access or modify the value stored inside a ref.

Q4. Do we need `.value` inside templates?

No. Vue automatically unwraps refs in templates.

Q5. What happens when a ref value changes?

Vue tracks the change and updates the relevant UI.

## 6. JavaScript interview coding

Question: Toggle the employee status.

```
let isActive = true;

isActive = !isActive;

console.log(isActive);
```

Output:

```
false
```

Follow-up: What will happen after executing the same statement again?

Answer: It becomes `true`.

# Assignments

Task 1: Counter application

- Start with count = 0.
- Add button.
- Decrease button.
- Reset button.
- Display the current count.

Task 2: Employee salary

- Create a reactive salary using `ref()`.
- Initial salary: ₹30,000.
- Add ₹5,000 button.
- Deduct ₹2,000 button.
- Display the updated salary.

Task 3: Employee status

- Create an employee named Rahul.
- Initial status: Active.
- Add a button to toggle between Active and Inactive.

Task 4: Interview questions

1. What is reactivity?
2. Difference between normal variable and `ref()`?
3. Why do we use `.value`?
4. Why does Vue update the screen automatically?
5. What does `!isActive.value` mean?

# Try it & Assignments Answers

# Try it: Employee counter

This is the Vue 3 implementation using `ref()`.

Replace your `App.vue` with:

```
<template>
  <div>
    <h1>Employee Counter</h1>

    <h2>Employee Count: {{ count }}</h2>

    <button @click="addEmployee">Add Employee</button>

    <button @click="removeEmployee">Remove Employee</button>

    <button @click="resetCount">Reset</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const count = ref(5);

function addEmployee() {
  count.value++;
}

function removeEmployee() {
  if (count.value > 0) {
    count.value--;
  }
}

function resetCount() {
  count.value = 5;
}
</script>
```

Explanation:

- `ref(5)` initializes the counter to 5.
- `count.value++` increases the count.
- `count.value--` decreases the count.
- `count.value = 5` resets it.
- Vue automatically updates the displayed count.


## Task 1. Counter application

Requirements:

- Start at 0.
- Add, decrease and reset buttons.

```
<template>
  <div>
    <h1>Counter Application</h1>

    <h2>Count: {{ count }}</h2>

    <button @click="increaseCount">Increase</button>

    <button @click="decreaseCount">Decrease</button>

    <button @click="resetCount">Reset</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const count = ref(0);

function increaseCount() {
  count.value++;
}

function decreaseCount() {
  count.value--;
}

function resetCount() {
  count.value = 0;
}
</script>
```

Important:

The `@click` directive listens for a button click.

For example:

```
<button @click="increaseCount">Increase</button>
```

When the user clicks the button, Vue executes `increaseCount()`.

## Task 2. Employee salary application

Requirements:

- Initial salary: ₹30,000.
- Increase by ₹5,000.
- Decrease by ₹2,000.

```
<template>
  <div>
    <h1>Employee Salary Management</h1>

    <h2>Employee: Rahul</h2>

    <h2>Salary: ₹{{ salary }}</h2>

    <button @click="increaseSalary">
      Increase Salary
    </button>

    <button @click="decreaseSalary">
      Deduct Salary
    </button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const salary = ref(30000);

function increaseSalary() {
  salary.value += 5000;
}

function decreaseSalary() {
  if (salary.value >= 2000) {
    salary.value -= 2000;
  }
}
</script>
```

Example:

| Action   | Salary  |
| -------- | ------- |
| Initial  | ₹30,000 |
| Increase | ₹35,000 |
| Increase | ₹40,000 |
| Deduct   | ₹38,000 |
| Deduct   | ₹36,000 |

Why did we use this condition?

```
if (salary.value >= 2000)
```

It prevents the salary from becoming negative.

## Task 3. Employee status application

Requirements:

- Employee: Rahul.
- Initial status: Active.
- Toggle between Active and Inactive.

```
<template>
  <div>
    <h1>Employee Status Management</h1>

    <h2>Employee: Rahul</h2>

    <h3>
      Status: {{ isActive ? "Active" : "Inactive" }}
    </h3>

    <button @click="toggleStatus">
      Change Status
    </button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const isActive = ref(true);

function toggleStatus() {
  isActive.value = !isActive.value;
}
</script>
```

Understand this carefully:

```
isActive.value = !isActive.value;
```

| Existing value | New value |
| -------------- | --------- |
| true           | false     |
| false          | true      |

The `!` operator reverses a Boolean value.

## Task 4. Interview answers

1\. What is reactivity?

Reactivity means Vue tracks changes in data and automatically updates the relevant user interface.

2\. Difference between normal variable and `ref()`?

A normal JavaScript variable is not automatically tracked by Vue. A `ref()` creates reactive data that Vue tracks.

3\. Why do we use `.value`?

We use `.value` in JavaScript to read or update the value inside a ref.

4\. Why does Vue update the screen automatically?

Vue tracks reactive dependencies. When a tracked value changes, Vue schedules the necessary UI update.

5\. What does `!isActive.value` mean?

It reverses the Boolean value. True becomes false, and false becomes true.

# Additional interview coding practice

These questions help you understand the concepts beyond the basic examples.

## Question 1: What is the output?

```
let count = 10;

count++;
count += 5;
count--;

console.log(count);
```

Answer: `15`

Calculation: 10 → 11 → 16 → 15.

## Question 2: What is the output?

```
let isActive = true;

isActive = !isActive;
isActive = !isActive;

console.log(isActive);
```

Answer: `true`

## Question 3: Find the mistake

```
<script setup>
import { ref } from "vue";

const count = ref(0);

function increaseCount() {
  count++;
}
</script>
```

Mistake: We used `count++` instead of `count.value++`.

Correct code:

```
function increaseCount() {
  count.value++;
}
```


## The Golden Rule Checklist for <script>

• Was it born from a ref() or computed()?
  Yes? Use .value (e.g., employees.value, selectedDepartment.value).

• Was it born inside a function parenthesis ( ... ) => as a temporary placeholder?
  No? Do NOT use .value (e.g., employee, total).

Inside <<script> use .value AND inside <template> use {{}}


# Understand the code inside computed()

## First, understand the problem

Suppose your Employee Management System has four employees.

```
const employees = [
  { name: "Rahul", salary: 40000 },
  { name: "Priya", salary: 35000 },
  { name: "Arun", salary: 50000 },
  { name: "Sneha", salary: 45000 }
];
```

Your manager asks:

"Calculate the total salary of all employees."

Before writing code, think about what you need to do.

1. Take Rahul's salary, 40000.
2. Add Priya's salary, 35000.
3. Add Arun's salary, 50000.
4. Add Sneha's salary, 45000.

Result: ₹1,70,000.

This is a calculation based on existing employee data.

In Vue, we use `computed()` to create a value based on other reactive values.

## Understand the computed() structure

Look at this code:

```
const totalSalary = computed(() => {
  return 170000;
});
```

Let's break it down.

Part 1

```
const totalSalary =
```

We are creating a variable named `totalSalary`.

Part 2

```
computed(
```

We are telling Vue to create a computed property.

Part 3

```
() =>
```

This is an arrow function. It gives Vue a function containing the calculation.

Part 4

```
{
  return 170000;
}
```

This function returns the calculated value.

Final result

```
});
```

This closes the function and the `computed()` call.

For now, remember this pattern:

```
const variableName = computed(() => {
  return calculatedValue;
});
```

Don't worry about employee arrays yet. First, understand the structure.

## What does return mean?

Consider this normal JavaScript function:

```
function getSalary() {
  return 40000;
}

const salary = getSalary();

console.log(salary);
```

Output:

```
40000
```

What happened?

- `getSalary()` runs the function.
- `return 40000` sends the value back.
- The returned value gets stored in `salary`.

Without `return`:

```
function getSalary() {
  40000;
}

const salary = getSalary();

console.log(salary);
```

Output:

```
undefined
```

Why?

Because the function did not return anything.

A function without an explicit return value returns `undefined`.

This matters inside computed properties because Vue needs the function to return the value you want to calculate.

## What are curly braces `{ }` doing?

Look at:

```
const getSalary = () => {
  return 40000;
};
```

Here:

- `()` holds the function parameters.
- `=>` represents an arrow function.
- `{ }` holds the function body.
- `return` sends the result back.

Compare these two functions:

```
const getSalary = () => {
  return 40000;
};
```

And:

```
const getSalary = () => 40000;
```

Both return `40000`.

When you use curly braces in an arrow function, you need `return` to return a value.

When you omit curly braces and write an expression directly, JavaScript returns that expression automatically.

This difference is important.

## Now put computed() and return together

Let's calculate a fixed value first.

```
import { computed } from "vue";

const totalSalary = computed(() => {
  return 40000 + 35000;
});
```

The calculation is:

```
40000 + 35000 = 75000
```

So `totalSalary` contains the computed result, ₹75,000.

But we don't want to hardcode salary values. We want to calculate them from employee data.

Before doing that, let's understand the array methods.

# Understand filter(), reduce(), and length

These three are different. Don't mix them up.

## What is filter()?

Suppose you have these salaries:

```
const salaries = [40000, 35000, 50000, 45000];
```

Your requirement:

"Find salaries greater than 40000."

Think about the condition:

```
salary > 40000
```

Now use `filter()`:

```
const result = salaries.filter((salary) => {
  return salary > 40000;
});

console.log(result);
```

Output:

```
[50000, 45000]
```

What did `filter()` do?

- It checked each salary.
- It kept the values satisfying the condition.
- It returned a new array containing those values.

How filter() checks each value

## 40,000

Reject

## 35,000

Reject

## 50,000

Keep

## 45,000

Keep

New array: `[50000, 45000]`

The important point:

`filter()` returns an array. It does not return just one matching value.

Now apply it to employees:

```
const employees = [
  { name: "Rahul", department: "IT" },
  { name: "Priya", department: "HR" },
  { name: "Arun", department: "IT" }
];

const itEmployees = employees.filter((employee) => {
  return employee.department === "IT";
});
```

Output:

```
[
  { name: "Rahul", department: "IT" },
  { name: "Arun", department: "IT" }
]
```

Here, `employee` represents one employee at a time.

## What is reduce()?

Now consider the same salary array:

```
const salaries = [40000, 35000, 50000, 45000];
```

Your requirement:

"Calculate the total salary."

We need to add all the numbers.

We could write a loop:

```
let total = 0;

for (let salary of salaries) {
  total = total + salary;
}

console.log(total);
```

Output:

```
170000
```

`reduce()` does the same kind of calculation.

```
const total = salaries.reduce((sum, salary) => {
  return sum + salary;
}, 0);

console.log(total);
```

Output:

```
170000
```

Understand each part:

| Code           | Meaning                               |
| -------------- | ------------------------------------- |
| `reduce()`     | Combines array values into one result |
| `sum`          | Running total                         |
| `salary`       | Current array value                   |
| `sum + salary` | Adds the current salary               |
| `0`            | Starting value of the total           |

Let's follow the calculation:

How reduce() calculates the total

| Starting total    | 0        |
| ----------------- | -------- |
| 0 + 40,000        | 40,000   |
| 40,000 + 35,000   | 75,000   |
| 75,000 + 50,000   | 1,25,000 |
| 1,25,000 + 45,000 | 1,70,000 |

Final total

# ₹1,70,000

The important point:

- `filter()` returns an array.
- `reduce()` returns one final value in this example.

## What is length?

`length` tells you how many items are in an array.

```
const employees = ["Rahul", "Priya", "Arun", "Sneha"];

console.log(employees.length);
```

Output:

```
4
```

You can also use it after `filter()`:

```
const itEmployees = employeesList.filter((employee) => {
  return employee.department === "IT";
});

console.log(itEmployees.length);
```

If two employees belong to IT, the output is `2`.

This is how we counted IT employees in Day 4.

Remember:

```
employees.length
```

Counts all employees.

```
itEmployees.length
```

Counts only the employees in the filtered array.

## Compare the three methods

| Method     | What it does                 | Result    |
| ---------- | ---------------------------- | --------- |
| `filter()` | Selects matching items       | New array |
| `reduce()` | Combines items into a result | One value |
| `length`   | Counts items                 | Number    |

# Understand includes() and toLowerCase()

## What is includes()?

Suppose the employee's name is Rahul.

```
const name = "Rahul";

console.log(name.includes("Rah"));
```

Output:

```
true
```

Why?

Because `"Rah"` exists inside `"Rahul"`.

Now:

```
console.log(name.includes("Pri"));
```

Output:

```
false
```

Because `"Pri"` does not exist inside `"Rahul"`.

So `includes()` checks whether one piece of text exists inside another.

It returns either:

- `true`, if it finds a match.
- `false`, if it doesn't find a match.

## What is toLowerCase()?

Look at this:

```
const name = "RAHUL";

console.log(name.toLowerCase());
```

Output:

```
rahul
```

It converts all letters to lowercase.

Why do we need this in employee search?

Consider:

```
const name = "Rahul";

console.log(name.includes("rah"));
```

Output:

```
false
```

JavaScript's normal string comparison is case-sensitive.

`"Rah"` and `"rah"` are treated as different text.

We solve this by converting both strings to lowercase:

```
const name = "Rahul";
const searchText = "RAH";

console.log(
  name.toLowerCase().includes(searchText.toLowerCase())
);
```

Output:

```
true
```

Let's break it down:

```
name.toLowerCase()
```

Produces `"rahul"`.

```
searchText.toLowerCase()
```

Produces `"rah"`.

Then:

```
"rahul".includes("rah")
```

Produces `true`.

## Put search methods together with filter()

Here is our employee list:

```
const employees = [
  { name: "Rahul", department: "IT" },
  { name: "Priya", department: "HR" },
  { name: "Arun", department: "IT" },
  { name: "Sneha", department: "Finance" }
];
```

We want to search employees by name.

```
const searchText = "rah";

const result = employees.filter((employee) => {
  return employee.name
    .toLowerCase()
    .includes(searchText.toLowerCase());
});

console.log(result);
```

Output:

```
[
  { name: "Rahul", department: "IT" }
]
```

Understand the process:

1. `filter()` checks each employee.
2. `employee.name` gets the employee's name.
3. `toLowerCase()` converts the name to lowercase.
4. `includes()` checks whether the search text exists.
5. `filter()` keeps employees who match.

You now understand the main JavaScript methods used in the Day 4 search feature.

# How ref(), computed(), v-model, and template work together

This is the most important connection in Day 4.

Let's understand it through one real requirement.

Requirement:

"Add a search box. When the user types an employee name, display matching employees automatically."

There are four pieces involved.

## First, ref() stores the data

```
const searchText = ref("");
```

This creates a reactive variable.

Initially, its value is an empty string.

When the user types `rah`, its value becomes `"rah"`.

## Second, v-model connects the input to ref()

```
<input v-model="searchText" placeholder="Search employee" />
```

What does `v-model` do?

It connects the input field to `searchText`.

- When the user types, `searchText` changes.
- When `searchText` changes programmatically, the input reflects the new value.

For a text input, `v-model` handles both directions of this connection.

## Third, computed() filters the employees

```
const searchedEmployees = computed(() => {
  return employees.value.filter((employee) => {
    return employee.name
      .toLowerCase()
      .includes(searchText.value.toLowerCase());
  });
});
```

Notice two reactive values here:

- `employees.value`
- `searchText.value`

Vue tracks these dependencies.

When the search text changes, Vue knows the computed result needs to be updated.

## Fourth, the template displays the result

```
<div v-for="employee in searchedEmployees" :key="employee.id">
  {{ employee.name }}
</div>
```

`v-for` loops through the filtered employee array.

It displays each matching employee.

## Follow the complete flow

User types "rah"

Search input

v-model

Updates searchText in ref()

computed()

Filters employees using the new search text

v-for in the template

Displays the matching employee

One key distinction:

- `ref()` stores the input value.
- `v-model` connects the input and the reactive variable.
- `computed()` derives the filtered list.
- The template displays the result.

## Try the search yourself

Live employee search

4 matching employee(s)

Rahul

IT

Priya

HR

Arun

IT

Sneha

Finance

# Understand .value

You might have noticed this difference in our examples.

Normal JavaScript array:

```
const employees = [];

employees.filter(...);
```

Vue reactive array using `ref()`:

```
const employees = ref([]);

employees.value.filter(...);
```

Why `.value`?

Because `ref()` wraps your original value inside a Vue ref object.

For example:

```
const salary = ref(40000);
```

To access its value inside JavaScript:

```
console.log(salary.value);
```

Output:

```
40000
```

The same applies to arrays:

```
const employees = ref([
  { name: "Rahul", salary: 40000 }
]);
```

To access the array in JavaScript:

```
employees.value
```

To filter it:

```
employees.value.filter(...)
```

But inside the Vue template, Vue automatically unwraps refs in common template expressions.

So this works:

```
<p>{{ salary }}</p>
```

You don't need `salary.value` in the template.


## What is a computed property?

Suppose our Employee Management System has these employees:

```
const employees = ref([
  { id: 1, name: "Rahul", department: "IT", salary: 40000 },
  { id: 2, name: "Priya", department: "HR", salary: 35000 },
  { id: 3, name: "Arun", department: "IT", salary: 50000 },
  { id: 4, name: "Sneha", department: "Finance", salary: 45000 }
]);
```

Your manager asks you:

"Display the total salary of all employees."

We need to calculate:

```
40000 + 35000 + 50000 + 45000
```

Result:

```
170000
```

We might write:

```
let totalSalary = 0;

for (let employee of employees.value) {
  totalSalary += employee.salary;
}
```

This works, but there is a problem.

What happens when an employee's salary changes or a new employee joins?

We need to calculate the total again manually.

Vue provides `computed()` to solve this problem.

## Understanding computed()

A computed property automatically recalculates its result when one of its reactive dependencies changes.

Syntax:

```
import { ref, computed } from "vue";

const result = computed(() => {
  // Calculation
});
```

Let's calculate total salary.

```
const totalSalary = computed(() => {
  return employees.value.reduce((total, employee) => {
    return total + employee.salary;
  }, 0);
});
```

Let's understand this code.

| Code              | Meaning                                  |
| ----------------- | ---------------------------------------- |
| `computed()`      | Creates a computed property              |
| `employees.value` | Accesses the employee array              |
| `reduce()`        | Calculates one final value from an array |
| `total`           | Running total                            |
| `employee.salary` | Current employee's salary                |
| `0`               | Initial total                            |

Result:

```
Total Salary: ₹170000
```

If an employee's salary changes, Vue automatically recalculates the total.

You do not need to manually calculate it again.

## Your first complete Vue example

Open your project's `src/App.vue`.

Replace its contents with this:

```

<script setup>
import { ref, computed } from "vue";

const employees = ref([
  { id: 1, name: "Rahul", department: "IT", salary: 40000 },
  { id: 2, name: "Priya", department: "HR", salary: 35000 },
  { id: 3, name: "Arun", department: "IT", salary: 50000 },
  { id: 4, name: "Sneha", department: "Finance", salary: 45000 }
]);

const totalSalary = computed(() => {
  return employees.value.reduce((total, employee) => {
    return total + employee.salary;
  }, 0);
});
</script>

<template>
  <h2>Employee Management System</h2>

  <h3>Total Employees: {{ employees.length }}</h3>
  <h3>Total Salary: ₹{{ totalSalary }}</h3>

  <div v-for="employee in employees" :key="employee.id">
    <p>
      {{ employee.name }} |
      {{ employee.department }} |
      ₹{{ employee.salary }}
    </p>
  </div>
</template>

```

Expected output:

## Employee Management System

# ₹1,70,000

Total salary · 4 employees

| Employee | Department | Salary  |
| -------- | ---------- | ------- |
| Rahul    | IT         | ₹40,000 |
| Priya    | HR         | ₹35,000 |
| Arun     | IT         | ₹50,000 |
| Sneha    | Finance    | ₹45,000 |

Important: In JavaScript, use `totalSalary.value` if you need to access the computed result. In the Vue template, Vue automatically unwraps it, so `{{ totalSalary }}` works.

## Difference between ref() and computed()

This is an important interview question.

| ref()                          | computed()                  |
| ------------------------------ | --------------------------- |
| Stores a reactive value        | Calculates a reactive value |
| You assign or update its value | Vue calculates its value    |
| Used for original data         | Used for derived data       |
| Example: employee salary       | Example: total salary       |

Example:

```
const salary = ref(40000);

const annualSalary = computed(() => {
  return salary.value * 12;
});
```

Here:

- `salary` stores ₹40,000.
- `annualSalary` calculates ₹4,80,000.
- If `salary` changes to ₹50,000, `annualSalary` automatically becomes ₹6,00,000.

You should use `ref()` for data you want to store and update.

Use `computed()` for values you want to derive from other reactive data.

## Dynamic employee filtering

Now let's use computed properties in a real company requirement.

Imagine your manager gives you this ticket:

"Add a department filter to the employee dashboard. When the user selects IT, display only IT employees."

First, create a reactive filter:

```
const selectedDepartment = ref("All");
```

Then create a computed property:

```
const filteredEmployees = computed(() => {
  if (selectedDepartment.value === "All") {
    return employees.value;
  }

  return employees.value.filter((employee) => {
    return employee.department === selectedDepartment.value;
  });
});
```

What happens here?

- If the selected department is `All`, return every employee.
- If the selected department is `IT`, return only IT employees.
- If the selected department is `HR`, return only HR employees.

Now add this to your template:

```
<select v-model="selectedDepartment">
  <option value="All">All Departments</option>
  <option value="IT">IT</option>
  <option value="HR">HR</option>
  <option value="Finance">Finance</option>
</select>

<div v-for="employee in filteredEmployees" :key="employee.id">
  {{ employee.name }} - {{ employee.department }}
</div>
```

Notice something important:

`v-model` updates `selectedDepartment`.

`computed()` detects the change and recalculates `filteredEmployees`.

Vue updates the displayed list automatically.

## Complete working example

```

<script setup>
import { ref, computed } from "vue";

const employees = ref([
  { id: 1, name: "Rahul", department: "IT", salary: 40000 },
  { id: 2, name: "Priya", department: "HR", salary: 35000 },
  { id: 3, name: "Arun", department: "IT", salary: 50000 },
  { id: 4, name: "Sneha", department: "Finance", salary: 45000 }
]);

const selectedDepartment = ref("All");

const filteredEmployees = computed(() => {
  if (selectedDepartment.value === "All") {
    return employees.value;
  }

  return employees.value.filter((employee) => {
    return employee.department === selectedDepartment.value;
  });
});

const totalSalary = computed(() => {
  return employees.value.reduce((total, employee) => {
    return total + employee.salary;
  }, 0);
});
</script>

<template>
  <h2>Employee Management System</h2>

  <h3>Total Salary: ₹{{ totalSalary }}</h3>

  <label>Filter by Department:</label>

  <select v-model="selectedDepartment">
    <option value="All">All Departments</option>
    <option value="IT">IT</option>
    <option value="HR">HR</option>
    <option value="Finance">Finance</option>
  </select>

  <h3>Employee List</h3>

  <p v-if="filteredEmployees.length === 0">
    No employees found.
  </p>

  <div
    v-for="employee in filteredEmployees"
    :key="employee.id"
  >
    {{ employee.name }} |
    {{ employee.department }} |
    ₹{{ employee.salary }}
  </div>
</template>

```

## Try the department filter

Employee dashboard

Choose a department to see how computed filtering behaves.

All Departments

Employees shown

# 4

Rahul

IT · ₹40,000

Priya

HR · ₹35,000

Arun

IT · ₹50,000

Sneha

Finance · ₹45,000

## Interview questions

1. What is a computed property in Vue?

Answer: A computed property derives a value from reactive data. Vue automatically recalculates it when its dependencies change.

2. Why do we use computed()?

Answer: To calculate derived values efficiently and avoid repeating the same calculation in templates or methods.

3. What is the difference between computed() and methods?

Answer:

- Computed properties cache their results until their reactive dependencies change.
- Methods execute whenever they are called.

4. Does computed() automatically update the UI?

Answer: Yes. When a dependency changes, Vue recalculates the computed value and updates the UI where it is used.

5. Can we modify a computed property directly?

Answer: A computed property created with the getter-only syntax is read-only. Vue also supports writable computed properties with a getter and setter.

## Practice tasks

Complete these using your Employee Management System.

Task 1: Calculate the number of employees in the IT department using `computed()`.

Task 2: Calculate the average salary of all employees.

Task 3: Add a salary filter. Display only employees whose salary is greater than ₹40,000.

Task 4: Add a search box. Search employees by name. The list should update as the user types.

Task 5: Create a dashboard with:

- Total employees
- Total salary
- Average salary
- IT department employee count

## JavaScript interview practice

Understand this array method because we used it in today's lesson.

```
const salaries = [40000, 35000, 50000, 45000];

const total = salaries.reduce((sum, salary) => {
  return sum + salary;
}, 0);

console.log(total);
```

Output:

```
170000
```

Question: Why does `reduce()` return one value while `filter()` returns an array?

Answer:

- `reduce()` combines array elements into one final result.
- `filter()` returns a new array containing elements that satisfy a condition.

# Practice Task Answers

## Task 1. Count IT department employees

Requirement: Display the number of employees working in the IT department.

```
const itEmployeeCount = computed(() => {
  return employees.value.filter((employee) => {
    return employee.department === "IT";
  }).length;
});
```

Explanation:

- `filter()` selects employees whose department is IT.
- `.length` counts the selected employees.
- `computed()` recalculates the count when employee data changes.

Expected result: 2 IT employees.

## Task 2. Calculate average salary

Requirement: Calculate the average salary of all employees.

```
const averageSalary = computed(() => {
  if (employees.value.length === 0) {
    return 0;
  }

  const total = employees.value.reduce((sum, employee) => {
    return sum + employee.salary;
  }, 0);

  return total / employees.value.length;
});
```

Explanation:

- `reduce()` calculates total salary.
- `employees.value.length` gives the employee count.
- Divide total salary by employee count.
- The `if` condition prevents division by zero.

Expected calculation:

```
Total salary = 170000
Employees = 4

Average salary = 170000 / 4
               = 42500
```

## Task 3. Filter employees earning above ₹40,000

Requirement: Display only employees whose salary is greater than ₹40,000.

```
const highSalaryEmployees = computed(() => {
  return employees.value.filter((employee) => {
    return employee.salary > 40000;
  });
});
```

Expected result:

| Employee | Salary  |
| -------- | ------- |
| Arun     | ₹50,000 |
| Sneha    | ₹45,000 |

Notice that Rahul earns exactly ₹40,000. He is excluded because the condition uses `>` and not `>=`.

## Task 4. Search employees by name

Requirement: Add a search box. Update the employee list as the user types.

First, create a reactive search variable:

```
const searchText = ref("");
```

Next, create a computed property:

```
const searchedEmployees = computed(() => {
  return employees.value.filter((employee) => {
    return employee.name
      .toLowerCase()
      .includes(searchText.value.toLowerCase());
  });
});
```

Explanation:

- `toLowerCase()` makes the search case-insensitive.
- `includes()` checks whether the employee name contains the search text.
- `filter()` returns matching employees.
- `computed()` updates the result when the search text changes.

Example:

| Search input | Result             |
| ------------ | ------------------ |
| rah          | Rahul              |
| PRI          | Priya              |
| ar           | Arun               |
| xyz          | No employees found |

## Task 5. Create an employee dashboard

Requirement: Display four dashboard values:

1. Total employees.
2. Total salary.
3. Average salary.
4. IT department employee count.

Here is the complete implementation.

## Complete App.vue

```

<script setup>
import { ref, computed } from "vue";

// Employee data
const employees = ref([
  { id: 1, name: "Rahul", department: "IT", salary: 40000 },
  { id: 2, name: "Priya", department: "HR", salary: 35000 },
  { id: 3, name: "Arun", department: "IT", salary: 50000 },
  { id: 4, name: "Sneha", department: "Finance", salary: 45000 }
]);

// Search input
const searchText = ref("");

// Task 1: IT employee count
const itEmployeeCount = computed(() => {
  return employees.value.filter((employee) => {
    return employee.department === "IT";
  }).length;
});

// Task 2: Total salary
const totalSalary = computed(() => {
  return employees.value.reduce((sum, employee) => {
    return sum + employee.salary;
  }, 0);
});

// Task 2: Average salary
const averageSalary = computed(() => {
  if (employees.value.length === 0) {
    return 0;
  }

  return totalSalary.value / employees.value.length;
});

// Task 3: Employees earning above 40000
const highSalaryEmployees = computed(() => {
  return employees.value.filter((employee) => {
    return employee.salary > 40000;
  });
});

// Task 4: Search employees by name
const searchedEmployees = computed(() => {
  return employees.value.filter((employee) => {
    return employee.name
      .toLowerCase()
      .includes(searchText.value.toLowerCase());
  });
});
</script>

<template>
  <div class="container">
    <h1>Employee Management System</h1>

    <!-- Dashboard -->
    <div class="dashboard">
      <div class="card">
        <h3>Total Employees</h3>
        <h2>{{ employees.length }}</h2>
      </div>

      <div class="card">
        <h3>Total Salary</h3>
        <h2>₹{{ totalSalary.toLocaleString("en-IN") }}</h2>
      </div>

      <div class="card">
        <h3>Average Salary</h3>
        <h2>₹{{ averageSalary.toLocaleString("en-IN") }}</h2>
      </div>

      <div class="card">
        <h3>IT Employees</h3>
        <h2>{{ itEmployeeCount }}</h2>
      </div>
    </div>

    <!-- Search -->
    <h2>Search Employees</h2>

    <input
      type="text"
      v-model="searchText"
      placeholder="Search by employee name"
    />

    <p v-if="searchedEmployees.length === 0">
      No employees found.
    </p>

    <table v-else>
      <thead>
        <tr>
          <th>Name</th>
          <th>Department</th>
          <th>Salary</th>
        </tr>
      </thead>

      <tbody>
        <tr
          v-for="employee in searchedEmployees"
          :key="employee.id"
        >
          <td>{{ employee.name }}</td>
          <td>{{ employee.department }}</td>
          <td>₹{{ employee.salary.toLocaleString("en-IN") }}</td>
        </tr>
      </tbody>
    </table>

    <!-- High Salary Employees -->
    <h2>Employees Earning Above ₹40,000</h2>

    <p v-if="highSalaryEmployees.length === 0">
      No employees found.
    </p>

    <ul v-else>
      <li
        v-for="employee in highSalaryEmployees"
        :key="employee.id"
      >
        {{ employee.name }} - ₹{{ employee.salary }}
      </li>
    </ul>
  </div>
</template>

<style scoped>
.container {
  padding: 20px;
  font-family: Arial, sans-serif;
}

.dashboard {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 15px;
  margin-bottom: 25px;
}

.card {
  padding: 15px;
  background: #f0f0f0;
  border-radius: 8px;
}

input {
  padding: 10px;
  width: 100%;
  max-width: 350px;
  margin-bottom: 15px;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  border: 1px solid #ccc;
  padding: 10px;
  text-align: left;
}

@media (max-width: 500px) {
  .dashboard {
    grid-template-columns: 1fr;
  }
}
</style>

```

## Expected dashboard output

## Employee Management System

Total Employees

# 4

Total Salary

# ₹1,70,000

Average Salary

# ₹42,500

IT Employees

# 2

## Important interview concepts

| Concept         | Remember this                                   |
| --------------- | ----------------------------------------------- |
| `computed()`    | Calculates values from reactive data            |
| `filter()`      | Returns matching array elements                 |
| `reduce()`      | Combines array elements into one result         |
| `includes()`    | Checks whether a string contains another string |
| `toLowerCase()` | Converts text to lowercase                      |
| `v-model`       | Creates two-way binding between input and state |
| `.length`       | Returns the number of array elements            |
