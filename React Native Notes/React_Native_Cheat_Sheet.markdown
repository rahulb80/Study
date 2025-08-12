## React Native Overview
- **Summary**: React Native is a framework for building native iOS and Android apps using JavaScript and React.
- **Example**:
```javascript
import React from 'react';
import { Text, View } from 'react-native';

const App = () => (
  <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
    <Text>Hello, React Native!</Text>
  </View>
);
export default App;
```
- **Tips**:
  - Leverage React knowledge to build mobile apps with familiar syntax.
  - Use React Native for cross-platform development to save time.

## Creating React Native Projects
### Expo CLI vs React Native CLI
- **Summary**: Expo CLI simplifies setup with a managed workflow, while React Native CLI offers full control for custom native configurations.
- **Example**:
```bash
# Expo CLI
npx create-expo-app MyApp
cd MyApp
npx expo start

# React Native CLI
npx react-native init MyApp
cd MyApp
npx react-native run-android
```
- **Tips**:
  - Use Expo CLI for faster setup and built-in tools like push notifications.
  - Choose React Native CLI for advanced native module integration.
  - Expo CLI requires less native code knowledge but may limit customization.

### Creating a New React Native Project
- **Summary**: Initialize a new React Native project using either Expo CLI or React Native CLI to set up the project structure.
- **Example**:
```bash
# Using Expo CLI
npx create-expo-app FavoritePlacesApp
# Using React Native CLI
npx react-native init FavoritePlacesApp
```
- **Tips**:
  - Ensure Node.js and npm/yarn are installed before creating projects.
  - Use descriptive project names to reflect app purpose.
  - Verify CLI tools are globally installed or use `npx` to avoid installation.

### Analyzing the Created Project
- **Summary**: A new React Native project includes a predefined folder structure with key files like `App.js` and configuration files.
- **Example**:
```plaintext
FavoritePlacesApp/
├── node_modules/       # Dependencies
├── src/                # Source code (custom)
├── App.js              # Main app component
├── package.json        # Project metadata and dependencies
├── metro.config.js     # Metro bundler config
├── babel.config.js     # Babel configuration
```
- **Tips**:
  - Explore `App.js` to understand the entry point of the app.
  - Check `package.json` for installed dependencies and scripts.
  - Use `src/` folder to organize custom components and logic.

## Running the App
### Running on a Real Device
- **Summary**: Run the React Native app on a physical device via USB debugging or Wi-Fi for real-world testing.
- **Example**:
```bash
# Expo CLI: Scan QR code with Expo Go app
npx expo start

# React Native CLI: Connect device and run
npx react-native run-android
# or
npx react-native run-ios
```
- **Tips**:
  - Enable USB debugging on Android or trust the computer on iOS.
  - Use Expo Go app for quick testing with Expo CLI projects.
  - Ensure the device and development machine are on the same network for Wi-Fi debugging.

## Setting Up a Local Development Environment
- **Summary**: Configure tools like Node.js, JDK, Android Studio, and Xcode to develop and test React Native apps locally.
- **Example**:
```bash
# Install Node.js (example for macOS with Homebrew)
brew install node

# Install Java Development Kit (JDK)
brew install openjdk@17

# Install Android Studio (manually via website)
# Install Xcode (via Mac App Store)
```
- **Tips**:
  - Use a version manager like `nvm` to handle multiple Node.js versions.
  - Set up Android emulator or iOS simulator for testing without a physical device.
  - Verify environment variables (e.g., `JAVA_HOME`, `ANDROID_HOME`) are correctly set.

## Quick Reference Table
| Tool/Command | Description | Example/Usage |
|--------------|-------------|---------------|
| `npx create-expo-app` | Initializes a new Expo-managed React Native project | `npx create-expo-app MyApp` |
| `npx expo start` | Starts the Expo development server | `npx expo start` |
| `npx react-native init` | Initializes a new React Native CLI project | `npx react-native init MyApp` |
| `npx react-native run-android` | Runs the app on an Android device/emulator | `npx react-native run-android` |
| `npx react-native run-ios` | Runs the app on an iOS device/simulator | `npx react-native run-ios` |
| `brew install node` | Installs Node.js on macOS | `brew install node` |
| `brew install openjdk@17` | Installs JDK for Android development | `brew install openjdk@17` |