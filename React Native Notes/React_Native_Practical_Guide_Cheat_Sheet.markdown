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

## Core Components
### Working With Core Components
- **Summary**: Core components like View, Text, and Button are built-in React Native elements for building UI structures.
- **Example**:
```jsx
import { View, Text, Button } from 'react-native';

const App = () => (
  <View>
    <Text>Hello World</Text>
    <Button title="Click Me" onPress={() => console.log('Pressed')} />
  </View>
);
```
- **Tips**:
  - Use View as a container similar to div in web.
  - Text is required for any text content; strings can't be rendered directly.
  - Import components explicitly to avoid bundle size issues.

## Styling
### Styling React Native Apps
- **Summary**: Styles in React Native use JavaScript objects with camelCase properties, applied via the style prop.
- **Example**:
```jsx
import { View, Text, StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  container: { flex: 1, backgroundColor: '#fff', alignItems: 'center' },
});

const App = () => (
  <View style={styles.container}>
    <Text style={{ color: 'blue', fontSize: 20 }}>Styled Text</Text>
  </View>
);
```
- **Tips**:
  - Use StyleSheet.create for performance optimization.
  - Styles don't cascade like CSS; each component's style is isolated.
  - Combine styles with array: style={[style1, style2]}.

### iOS & Android Styling Differences
- **Summary**: Platform-specific styles handle differences like shadows or fonts between iOS and Android.
- **Example**:
```jsx
import { Platform, StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  box: {
    ...Platform.select({
      ios: { shadowColor: '#000', shadowOffset: { width: 0, height: 2 } },
      android: { elevation: 5 },
    }),
  },
});
```
- **Tips**:
  - Use Platform.OS to detect the platform and apply conditional styles.
  - Test on both platforms to ensure consistent UI.
  - Avoid overusing platform-specific code; aim for cross-platform consistency.

### Working with Images & Changing Colors
- **Summary**: Image component displays local or remote images, with color changes via style props.
- **Example**:
```jsx
import { Image, View } from 'react-native';

const App = () => (
  <View style={{ backgroundColor: 'lightblue' }}>
    <Image source={require('./assets/image.png')} style={{ width: 100, height: 100, tintColor: 'red' }} />
    <Image source={{ uri: 'https://example.com/image.jpg' }} style={{ width: 200, height: 200 }} />
  </View>
);
```
- **Tips**:
  - Use require for local images; uri for remote.
  - TintColor overlays color on images.
  - Optimize image sizes to avoid performance issues.

## Layouts and Flexbox
### React Native & Flexbox
- **Summary**: Flexbox is the default layout model in React Native for arranging components flexibly.
- **Example**:
```jsx
<View style={{ flex: 1, flexDirection: 'row', justifyContent: 'space-between' }}>
  <View style={{ flex: 1, backgroundColor: 'red' }} />
  <View style={{ flex: 2, backgroundColor: 'blue' }} />
</View>
```
- **Tips**:
  - FlexDirection defaults to 'column' unlike web's 'row'.
  - Use flex values to proportionally size children.
  - Combine with alignItems for cross-axis alignment.

### Using Flexbox To Create Layouts
- **Summary**: Flexbox properties like justifyContent and alignItems create responsive layouts.
- **Example**:
```jsx
<View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
  <Text>Centered Content</Text>
</View>
```
- **Tips**:
  - JustifyContent aligns along the main axis; alignItems along the cross axis.
  - Test on different screen sizes for responsiveness.
  - Avoid fixed widths/heights; prefer flex for adaptability.

### Flexbox - A Deep Dive
- **Summary**: Advanced Flexbox includes flexWrap, flexGrow, and alignSelf for complex layouts.
- **Example**:
```jsx
<View style={{ flexDirection: 'row', flexWrap: 'wrap' }}>
  <View style={{ flexGrow: 1, alignSelf: 'flex-start' }} />
</View>
```
- **Tips**:
  - FlexWrap: 'wrap' handles overflow by moving to new lines.
  - FlexGrow expands items to fill space; flexShrink contracts them.
  - AlignSelf overrides parent's alignItems for individual children.

### Improving The Layout
- **Summary**: Refine layouts by adjusting margins, paddings, and flex properties for better UX.
- **Example**:
```jsx
<View style={{ margin: 20, padding: 10, flex: 1 }}>
  {/* Content */}
</View>
```
- **Tips**:
  - Use consistent spacing (e.g., multiples of 8) for design harmony.
  - Debug layouts with background colors to visualize boxes.
  - Consider safe areas for notched devices.

## Handling Events
### Handling Events
- **Summary**: Events like onPress are handled via props on components to respond to user interactions.
- **Example**:
```jsx
<Button title="Press Me" onPress={() => alert('Button pressed!')} />
```
- **Tips**:
  - Use arrow functions for inline handlers to avoid binding issues.
  - Prevent default behaviors if needed, though rare in RN.
  - Debounce frequent events like onChangeText for performance.

### Handling Taps with the Pressable Component
- **Summary**: Pressable provides customizable tap feedback with states like pressed.
- **Example**:
```jsx
import { Pressable, Text } from 'react-native';

<Pressable onPress={() => console.log('Tapped')} style={({ pressed }) => pressed && { opacity: 0.5 }}>
  <Text>Tap Me</Text>
</Pressable>
```
- **Tips**:
  - Style function receives { pressed } for dynamic styles.
  - Supports onLongPress for additional interactions.
  - Preferred over Touchable components for modern RN.

### Adding an Android Ripple Effect & an iOS Alternative
- **Summary**: Android ripple uses android_ripple prop; iOS uses TouchableOpacity for fade effect.
- **Example**:
```jsx
<Pressable
  android_ripple={{ color: 'lightgray' }}
  style={({ pressed }) => pressed && Platform.OS === 'ios' && { opacity: 0.8 }}
>
  <Text>Interactive</Text>
</Pressable>
```
- **Tips**:
  - Ripple is Android-only; use conditional opacity for iOS.
  - Customize ripple radius and color for better UX.
  - Test on emulators for platform-specific feedback.

## Lists
### Managing A List Of Course Goals (in our Demo App)
- **Summary**: Manage dynamic lists using state arrays and mapping to components.
- **Example**:
```jsx
import { useState } from 'react';
import { View, Text } from 'react-native';

const [goals, setGoals] = useState([]);
return (
  <View>
    {goals.map((goal, index) => <Text key={index}>{goal}</Text>)}
  </View>
);
```
- **Tips**:
  - Always provide unique keys for list items.
  - Use setState with spread operator to add items: setGoals([...goals, newGoal]).
  - Filter arrays for deletions: setGoals(goals.filter((g) => g.id !== id)).

### Making Content Scrollable with ScrollView
- **Summary**: ScrollView enables vertical/horizontal scrolling for overflowing content.
- **Example**:
```jsx
import { ScrollView, Text } from 'react-native';

<ScrollView>
  {Array.from({ length: 50 }).map((_, i) => <Text key={i}>Item {i}</Text>)}
</ScrollView>
```
- **Tips**:
  - Set contentContainerStyle for inner content styling.
  - Avoid nesting ScrollViews; use one per direction.
  - For large lists, prefer FlatList for performance.

### Optimizing Lists with FlatList
- **Summary**: FlatList renders large lists efficiently with lazy loading and key extraction.
- **Example**:
```jsx
import { FlatList } from 'react-native';

<FlatList
  data={data}
  renderItem={({ item }) => <Text>{item.title}</Text>}
  keyExtractor={(item) => item.id}
/>
```
- **Tips**:
  - Provide keyExtractor for unique keys.
  - Use getItemLayout for faster scrolling if item sizes are known.
  - Add ListHeaderComponent or ListFooterComponent for extras.

### Making Items Deletable & Using IDs
- **Summary**: Use unique IDs for list items and filter state to delete them.
- **Example**:
```jsx
const deleteItem = (id) => setItems(items.filter((item) => item.id !== id));
```
- **Tips**:
  - Generate IDs with libraries like uuid.
  - Avoid using index as key; prefer stable IDs.
  - Update state immutably to trigger re-renders.

## Components and Props
### Splitting Components Into Smaller Components
- **Summary**: Break UI into reusable components for better organization and maintainability.
- **Example**:
```jsx
// GoalItem.js
export const GoalItem = ({ text }) => <Text>{text}</Text>;

// App.js
import { GoalItem } from './GoalItem';
<GoalItem text="Learn RN" />
```
- **Tips**:
  - Extract when a component grows large or is reused.
  - Keep components focused on single responsibility.
  - Use folders to organize component files.

### Utilizing Props
- **Summary**: Props pass data from parent to child components for customization.
- **Example**:
```jsx
const Child = ({ message }) => <Text>{message}</Text>;
<Child message="Hello from Parent" />
```
- **Tips**:
  - Props are read-only; don't mutate them.
  - Use defaultProps for fallback values.
  - Destructure props in function parameters for cleaner code.

### Working on the "Goal Input" Component
- **Summary**: Create input components with TextInput for user data entry.
- **Example**:
```jsx
import { TextInput, Button, useState } from 'react-native';

const [input, setInput] = useState('');
<TextInput value={input} onChangeText={setInput} />
<Button title="Add" onPress={() => addGoal(input)} />
```
- **Tips**:
  - Use multiline prop for multi-line inputs.
  - Clear input after submission: setInput('').
  - Style with placeholderTextColor and other props.

## Modals
### Adding a Modal Screen
- **Summary**: Modal component displays overlay screens for focused interactions.
- **Example**:
```jsx
import { Modal, Text } from 'react-native';

<Modal visible={isVisible} animationType="slide">
  <Text>Modal Content</Text>
</Modal>
```
- **Tips**:
  - Control visibility with state.
  - Use animationType: 'slide', 'fade', or 'none'.
  - Add transparent backdrop for dimming.

### Styling the Modal Overlay
- **Summary**: Style modals with absolute positioning and backgrounds for overlays.
- **Example**:
```jsx
<Modal visible={true} transparent={true}>
  <View style={{ flex: 1, justifyContent: 'center', backgroundColor: 'rgba(0,0,0,0.5)' }}>
    <View style={{ backgroundColor: 'white', padding: 20 }}>
      <Text>Content</Text>
    </View>
  </View>
</Modal>
```
- **Tips**:
  - Set transparent={true} for custom overlays.
  - Use rgba for semi-transparent backgrounds.
  - Center content with flex properties.

### Opening & Closing the Modal
- **Summary**: Toggle modal visibility using state updates on events.
- **Example**:
```jsx
const [modalVisible, setModalVisible] = useState(false);
<Button title="Open" onPress={() => setModalVisible(true)} />
<Modal visible={modalVisible} onRequestClose={() => setModalVisible(false)} />
```
- **Tips**:
  - Handle Android back button with onRequestClose.
  - Add close buttons inside the modal.
  - Prevent closing on backdrop tap if needed by ignoring onRequestClose.

## App Finishing Touches
- **Summary**: Polish app with icons, safe areas, and platform tweaks for production readiness.
- **Example**:
```jsx
import { SafeAreaView } from 'react-native';

<SafeAreaView style={{ flex: 1 }}>
  {/* App Content */}
</SafeAreaView>
```
- **Tips**:
  - Use SafeAreaView to avoid notches/status bars.
  - Add app icons via assets configuration.
  - Test on multiple devices for edge cases.

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
| `StyleSheet.create` | Creates optimized styles | `StyleSheet.create({ key: { prop: value } })` |
| `Platform.select` | Applies platform-specific values | `Platform.select({ ios: {}, android: {} })` |
| `Platform.OS` | Detects current platform | `if (Platform.OS === 'ios') {}` |
| `uuid` | Generates unique IDs (import from 'uuid') | `import uuid from 'uuid'; uuid.v4();` |