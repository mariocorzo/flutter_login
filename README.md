# Login App with Flutter and BLoC

This project is a simple Flutter application that implements a **login system** using the **BLoC (Business Logic Component)** pattern. It demonstrates how to structure a Flutter app with BLoC for managing the login flow and integrates an `AuthenticationRepository` to handle authentication-related operations.

---

## **Features**
- Login form built with Flutter's declarative UI.
- State management using the `flutter_bloc` package.
- Dependency injection of the `AuthenticationRepository`.
- Clean separation of concerns using the BLoC pattern.

---

## **Project Structure**
### **Key Files and Folders**
1. **`lib/login`**:
    - Contains the `LoginPage` and `LoginForm` widgets for the login UI.
    - Manages the user interaction and state changes for the login flow.

2. **`LoginBloc`**:
    - Handles the business logic for the login process.
    - Interacts with the `AuthenticationRepository`.

3. **`AuthenticationRepository`**:
    - Abstracts authentication-related operations (e.g., validating credentials).

---

## **Code Walkthrough**

### **LoginPage**
The `LoginPage` is the main widget for the login screen. It initializes the `LoginBloc` and provides it to the `LoginForm` using `BlocProvider`.

#### Key Points:
- `AuthenticationRepository` is injected via `context.read`.
- `LoginBloc` is responsible for handling the state and logic of the login flow.

```dart
class LoginPage extends StatelessWidget {
  const LoginPage({super.key});

  static Route<void> route() {
    return MaterialPageRoute<void>(builder: (_) => const LoginPage());
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Padding(
        padding: const EdgeInsets.all(12),
        child: BlocProvider(
          create: (context) => LoginBloc(
            authenticationRepository: context.read<AuthenticationRepository>(),
          ),
          child: const LoginForm(),
        ),
      ),
    );
  }
}
```

### **LoginBloc**
The `LoginBloc` (not shown in the snippet but assumed to exist) is responsible for:
- Handling events like form submission.
- Emitting states such as `LoginLoading`, `LoginSuccess`, or `LoginFailure`.

### **LoginForm**
The `LoginForm` widget (not shown in the snippet) interacts with the `LoginBloc` to display the form and handle user actions like inputting credentials and submitting the form.

---

## **Dependencies**
The project uses the following key dependencies:

### **`pubspec.yaml`**
```yaml
dependencies:
  flutter:
    sdk: flutter
  flutter_bloc: ^latest_version
  authentication_repository: ^latest_version
```

---

## **How to Run**
1. **Clone the Repository:**
   ```bash
   git clone https://github.com/mariocorzo/flutter_login
   cd flutter_login
   ```

2. **Install Dependencies:**
   ```bash
   flutter pub get
   ```

3. **Run the App:**
   ```bash
   flutter run
   ```

## **Future Enhancements**
- Add support for third-party authentication (e.g., Google, Facebook).
- Implement password reset functionality.
- Enhance UI/UX with animations and responsive design.

---

This project serves as a starting point for apps requiring authentication and highlights best practices for using BLoC in Flutter. 🚀