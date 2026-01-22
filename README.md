# Welcome to Expo Starter Kit 👋

This is an [Expo](https://expo.dev) starter kit project setup with [Tailwind CSS](https://tailwindcss.com/). Using the [Nativewind](https://www.nativewind.dev/docs) plugin, you can use the Tailwind CSS classes as React components to style your app.

## Get started

1. Clone the repository

   ```bash
   git clone https://github.com/shekhsahebali/Expo-starter-kit.git
   cd Expo-starter-kit
   ```

2. Install dependencies

   ```bash
   pnpm install # npm install
   ```

3. Start the app

   ```bash
   npx expo start
   ```
   or

   ```bash
   npx expo start --web
   ```

In the output, you'll find options to open the app in a

- [development build](https://docs.expo.dev/develop/development-builds/introduction/)
- [Android emulator](https://docs.expo.dev/workflow/android-studio-emulator/)
- [iOS simulator](https://docs.expo.dev/workflow/ios-simulator/)
- [Expo Go](https://expo.dev/go), a limited sandbox for trying out app development with Expo

You can start developing by editing the files inside the **app** directory. This project uses [file-based routing](https://docs.expo.dev/router/introduction).


## To Setup Tailwind CSS in your project

1. Install Nativewind

   ```bash
   npx expo install nativewind react-native-reanimated@~3.17.4 react-native-safe-area-context@5.4.0 react-native-reanimated tailwindcss
   npx expo install --dev tailwindcss@^3.4.17 prettier-plugin-tailwindcss@^0.5.11
   ```

2. Setup Tailwind CSS
Run `npx tailwindcss init` to create a `tailwind.config.js` file



   ```js
   /** @type {import('tailwindcss').Config} */
    module.exports = {
      content: [
        "./App.{js,jsx,ts,tsx}",
        "./app/**/*.{js,jsx,ts,tsx}",
        "./components/**/*.{js,jsx,ts,tsx}",
      ],
      presets: [require("nativewind/preset")],
      theme: {
        extend: {},
      },
      plugins: [],
    };


   ```
Create a `global.css` file and add the Tailwind directives.

   ```css
@tailwind base;
@tailwind components;
@tailwind utilities;
   ```

3. Add the Babel preset to your `babel.config.js` file

   ```js
   module.exports = function (api) {
      api.cache(true);
      return {
        presets: ["babel-preset-expo"],
        plugins: ["nativewind/babel"],
      };
    };

   ```
4. Create or modify your metro.config.js.

  To generate a new `metro.config.js` file, run the following command.
  ```bash
  npx expo customize metro.config.js
  ```
  And Add in `metro.config.js` file

   ```js
    const { getDefaultConfig } = require("expo/metro-config");
    const { withNativeWind } = require("nativewind/metro");

    const config = getDefaultConfig(__dirname);

    module.exports = withNativeWind(config);

   ```
5. Import your CSS file in your `index.js `or `App.js`

   ```js
    import "./global.css"
    import { Text, View } from "react-native";
    
    export default function App() {
      return (
        <View className="flex-1 items-center justify-center bg-white">
          <Text className="text-xl font-bold text-blue-500">
            Welcome to Nativewind!
          </Text>
        </View>
      );
    }
   ```
6. Modify your app.json

   ```json
    {
      "expo": {
        "web": {
          "bundler": "metro"
        }
      }
    }
   ```
7. Start the app

   ```bash
   npx expo start -c
   ```
   or

   ```bash
   npx expo start --web -c
   ```


## Learn more

To learn more about developing your project with Expo, Tailwind look at the following resources:

- [Expo documentation](https://docs.expo.dev/): Learn fundamentals, or go into advanced topics with our [guides](https://docs.expo.dev/guides).
- [Learn Expo tutorial](https://docs.expo.dev/tutorial/introduction/): Follow a step-by-step tutorial where you'll create a project that runs on Android, iOS, and the web.
- [Tailwind documentation](https://tailwindcss.com/docs): Learn how to use Tailwind to style your project.
- [Nativewind documentation](https://www.nativewind.dev/docs): Learn how to use Nativewind to style your project.
