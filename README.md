# AppDevProjectTemplate
Template for MIS385N Project
# Project Overview

This project is a web application built using Flask and MongoDB, and React. The application manages users, projects, and hardware sets, allowing users to log in, join projects, and request hardware. The backend consists of four main Python files that handle different aspects of the application's functionality.

## 1. `app.py`

This file is the main entry point of the application. It sets up the Flask web server and defines various routes for handling user requests.

- **Routes:**
  - `/login`: Handles user login.
  - `/main`: Handles requests to the main user portal.
  - `/join_project`: Allows a user to join a project.
  - `/add_user`: Adds a new user to the database.
  - `/get_user_projects_list`: Retrieves the list of projects a user is part of.
  - `/create_project`: Creates a new project.
  - `/get_project_info`: Retrieves information about a project.
  - `/get_all_hw_names`: Retrieves a list of all hardware set names.
  - `/get_hw_info`: Retrieves information about a specific hardware set.
  - `/check_out`: Handles hardware checkout for a project.
  - `/check_in`: Handles hardware check-in for a project.
  - `/create_hardware_set`: Creates a new hardware set.
  - `/api/inventory`: Checks the inventory of projects.

## 2. `hardwareDB.py`

This file contains functions for managing hardware sets in the database.

- **Functions:**
  - `createHardwareSet`: Creates a new hardware set.
  - `queryHardwareSet`: Queries a hardware set by its name.
  - `updateAvailability`: Updates the availability of a hardware set.
  - `requestSpace`: Requests a certain amount of hardware from a set.
  - `getAllHwNames`: Retrieves a list of all hardware set names.

## 3. `projectsDB.py`

This file contains functions for managing projects in the database.

- **Functions:**
  - `queryProject`: Queries a project by its ID.
  - `createProject`: Creates a new project.
  - `addUser`: Adds a user to a project.
  - `updateUsage`: Updates the usage of a hardware set in a project.
  - `checkOutHW`: Handles hardware checkout for a project.
  - `checkInHW`: Handles hardware check-in for a project.

## 4. `usersDB.py`

This file contains functions for managing users in the database.

- **Functions:**
  - `addUser`: Adds a new user to the database.
  - `__queryUser`: Helper function to query a user by username and userId.
  - `login`: Authenticates a user and handles login.
  - `joinProject`: Adds a user to a project.
  - `getUserProjectsList`: Retrieves the list of projects a user is part of.

## How the Files Interact

1. **User Management (`usersDB.py`):**
   - `addUser` function in `usersDB.py` is used to add new users to the database.
   - `login` function in `usersDB.py` is used to authenticate users when they log in through the `/login` route in `app.py`.
   - `joinProject` function in `usersDB.py` adds users to projects and interacts with `projectsDB.py` to update project information.

2. **Project Management (`projectsDB.py`):**
   - `createProject` function in `projectsDB.py` is called through the `/create_project` route in `app.py` to create new projects.
   - `addUser` function in `projectsDB.py` adds users to projects, updating the project's user list.
   - `checkOutHW` and `checkInHW` functions in `projectsDB.py` handle hardware check-out and check-in for projects, respectively, interacting with `hardwareDB.py` to update hardware availability.

3. **Hardware Management (`hardwareDB.py`):**
   - `createHardwareSet` function in `hardwareDB.py` is used to create new hardware sets through the `/create_hardware_set` route in `app.py`.
   - `requestSpace` function in `hardwareDB.py` handles requests for hardware availability when users check out or check in hardware through the `/check_out` and `/check_in` routes in `app.py`.
   - `getAllHwNames` and `queryHardwareSet` functions in `hardwareDB.py` provide hardware set information to various routes in `app.py`.

4. **Main Application (`app.py`):**
   - Defines routes that handle HTTP requests and interact with `usersDB.py`, `projectsDB.py`, and `hardwareDB.py` to perform various operations.
   - Routes call appropriate functions from the respective database modules to manage users, projects, and hardware sets.

## Client side

1. Design choices are up to you, but an example directory structure has been provided. 
