# Project Name: Nuxt Employees

## Overview

This project is a simple Employee Management App developed for educational purposes. It allows you to list employees by consuming data from an API using Nuxt.js 3's `useFetch` hook. Additionally, you can create a new employee through the app.

## Prerequisites

Before running this project, you need to have the following software installed on your system:

1. Node.js - [Download and Install Node.js](https://nodejs.org/en/download/)
2. Nuxt.js 3 - Make sure you have Nuxt.js 3 installed. You can follow the instructions on the [Nuxt.js 3 documentation](https://v3.nuxtjs.org/docs/getting-started/installation) for installation.
3. JSON Server - We will use JSON Server as a fake REST API to simulate server responses. You can install JSON Server globally using npm:

```bash
npm install -g json-server
```

## Installation

Follow these steps to set up the project:

1. Clone the repository:

```bash
git clone <repository_url>
cd nuxt-employees
```

2. Install the project dependencies:

```bash
npm install
```

## Running the Project

To run the project, you need to start both the JSON Server and the Nuxt.js app:

1. Start the JSON Server to serve the employee data:

```bash
json-server --watch db.json
```

2. In a separate terminal, start the Nuxt.js app:

```bash
npm run dev
```

The Nuxt.js app will be running at `http://localhost:3000`.

## How to Use

Once the project is up and running, you can access the Employee Management App in your web browser at `http://localhost:3000`.

### Listing Employees

The app will automatically fetch the list of employees from the JSON Server using the `useFetch` hook. The employee data will be displayed on the home page.

### Adding a New Employee

To create a new employee, navigate to the "Create Employee" page using the navigation bar or by clicking the appropriate link. You will see a form where you can input the employee's details, such as name, position, and department. After filling out the form, click the "Create Employee" button to add the new employee to the list.

## Note

- This project is intended for educational purposes only and uses a fake REST API powered by JSON Server to simulate backend functionality.
- In a real-world scenario, you would need a proper backend server to handle API requests and store data.

Happy learning and coding! If you have any questions or run into any issues, feel free to ask for help. Enjoy building your Employee Management App with Nuxt.js 3 and the `useFetch` hook!
