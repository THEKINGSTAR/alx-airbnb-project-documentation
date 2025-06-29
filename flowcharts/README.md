# Flowchart – User Registration Process

## 🧭 Description

This flowchart outlines the backend workflow for the user registration process in the Airbnb Clone project. It helps visualize the decision-making logic, data handling, and control flow during signup.

## 🔁 Flow Steps

1. User submits a registration form (email, password, role).
2. Input is validated.
3. System checks if email already exists.
   - If yes → return error.
   - If no → hash password, save user, generate JWT.
4. Token is returned on success.

## 📤 Exported Files

- `user-registration.drawio` – Editable diagram (Draw.io format)
- `user-registration.png` – Exported image file
