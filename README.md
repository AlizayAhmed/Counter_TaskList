# Flutter To-Do List App with Persistent Storage

A modern, clean Flutter application demonstrating state management and persistent data storage using SharedPreferences.

## 📱 Features

### Week 2 Learning Objectives Implemented:

1. **State Management Basics** ✅
   - Counter app with increment/decrement functionality
   - Real-time UI updates using `setState`
   - State preservation across app restarts

2. **Persistent Data Storage** ✅
   - Counter value saved and retrieved using SharedPreferences
   - Tasks persisted locally
   - Data survives app restarts

3. **To-Do List Functionality** ✅
   - Add new tasks
   - Mark tasks as complete/incomplete
   - Delete tasks
   - Display tasks in ListView
   - Progress tracking (completed vs total tasks)
   - Modern, light UI with Material 3 design

## 🎨 UI Features

- Clean, modern interface with Material 3 design
- Light color scheme with blue and green accents
- Progress indicator showing task completion
- Smooth animations and transitions
- Empty state with helpful guidance
- Card-based layout for better visual hierarchy

## 🚀 Getting Started

### Prerequisites

- Flutter SDK (3.0.0 or higher)
- Dart SDK (3.0.0 or higher)
- An IDE (VS Code, Android Studio, or IntelliJ IDEA)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/AlizayAhmed/Counter_TaskList
cd flutter-todo-app
```

2. Install dependencies:
```bash
flutter pub get
```

3. Run the app:
```bash
flutter run
```

## 📦 Dependencies

Add these dependencies to your `pubspec.yaml`:

```yaml
dependencies:
  flutter:
    sdk: flutter
  shared_preferences: ^2.2.2

dev_dependencies:
  flutter_test:
    sdk: flutter
  flutter_lints: ^3.0.0
```

## 🏗️ Project Structure

```
lib/
└── main.dart          # Main application file containing all logic
```

## 💡 Key Concepts Demonstrated

### 1. State Management with setState

```dart
void _incrementCounter() {
  setState(() {
    _counter++;
  });
  _saveData();
}
```

The app uses `setState` to manage UI state, triggering rebuilds when data changes.

### 2. Data Persistence with SharedPreferences

```dart
Future<void> _saveData() async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.setInt('counter', _counter);
  
  final tasksString = json.encode(_tasks.map((task) => task.toJson()).toList());
  await prefs.setString('tasks', tasksString);
}
```

SharedPreferences stores simple key-value pairs persistently on the device.

### 3. Task Model

```dart
class Task {
  String title;
  bool isCompleted;
  DateTime createdAt;
  
  // JSON serialization for storage
  Map<String, dynamic> toJson() => {...};
  factory Task.fromJson(Map<String, dynamic> json) => Task(...);
}
```

Tasks are converted to/from JSON for storage in SharedPreferences.

### 4. ListView Builder

```dart
ListView.builder(
  itemCount: _tasks.length,
  itemBuilder: (context, index) {
    final task = _tasks[index];
    return Card(...);
  },
)
```

Efficiently displays a scrollable list of tasks.

## 🎯 Learning Outcomes

After studying this project, you will understand:

- How to use `setState` for reactive UI updates
- How to implement persistent storage with SharedPreferences
- How to create and manage a list of items in Flutter
- How to build a clean, modern UI with Material 3
- How to serialize/deserialize data for storage
- How to handle user input and form validation
- How to implement CRUD operations (Create, Read, Update, Delete)

## 🔄 App Flow

1. **App Launch**: Loads saved counter and tasks from SharedPreferences
2. **Add Task**: User enters task → Task added to list → Saved to storage
3. **Toggle Task**: User checks/unchecks task → State updated → Saved
4. **Delete Task**: User deletes task → Removed from list → Storage updated
5. **Counter**: User increments/decrements → Value updated and saved

## 🛠️ Customization

You can easily customize:

- **Colors**: Change `seedColor` in `ThemeData`
- **Fonts**: Add custom fonts in `pubspec.yaml`
- **Task Properties**: Add priority, due dates, categories
- **Storage**: Migrate to SQLite or Hive for more complex data

## 📚 Additional Features to Implement

Challenge yourself by adding:
- Task editing functionality
- Categories or tags for tasks
- Due dates and reminders
- Search and filter functionality
- Task sorting options
- Dark mode support
- Animations for task completion


## 👨‍💻 Author

Created as part of Week 2: Data Management and Persistent Storage learning module.

