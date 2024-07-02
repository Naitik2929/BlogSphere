# BLOG SPHERE APPLICATION

This application is designed for those who love writing and sharing their thoughts. Users can read blog posts, log in or sign up to like posts, and staff/admin can manage posts and users.

# Table of Contents

1. [Features](#features)
2. [Tech Stack Versions](#tech-stack-versions)
3. [Configuration](#configuration)
4. [Getting Started](#getting-started)
5. [Build and Deployment](#build-and-deployment)

## 🌟 Features

- **User Authentication**: Secure authentication using JWT tokens for user login and signup.
- **Blog Reading**: Users can read blog posts and view details about each post.
- **Interaction**: Users can like posts to engage with the content.
- **User Management**: Staff/Admin can manage user accounts, including adding, updating users.
- **Post Management**: Staff/Admin members can create, edit, or delete blog posts.

## 📌 Tech Stack Versions

Please note that the versions listed below are the ones used during the development of this application. The application may work with other versions as well, but these are the ones that have been tested and confirmed to work.

- **Java**: 17
- **Spring Boot**: 3.2.5
- **JWT**: 0.11.5
- **MySQL**: 8.0
- **Angular CLI**: 16.2.10
- **Node.js**: 18.20.2
- **npm**: 10.5.0
- **PrimeNG**: 17.15.0
- **Electron**: 30.0.2
- **Capacitor**: 6.0.0

## ⚙️ Configuration

The application can be configured by modifying the [application.properties](https://github.com/56duong/angular-springboot-blog-webapp/blob/master/backend/src/main/resources/application.properties) file and the [config.ts](https://github.com/56duong/angular-springboot-blog-webapp/blob/master/frontend/src/app/core/config/config.ts) file in your JavaScript project. Here are some of the configurations you might need to change:

- **Database Connection**: Update the `spring.datasource.url`, `spring.datasource.username`, and `spring.datasource.password` properties in the `application.properties` file to match your own database connection details. You can choose to connect to a local database or an Azure database.

  ```properties
  #localhost
  spring.datasource.url=jdbc:mysql://your-localhost-database-url:3306/your-database-name?createDatabaseIfNotExist=true
  spring.datasource.username=your-localhost-username
  spring.datasource.password=your-localhost-password

  #azure
  spring.datasource.url=jdbc:mysql://your-azure-database-url:3306/your-database-name?useSSL=true
  spring.datasource.username=your-azure-username
  spring.datasource.password=your-azure-password
  ```

- **API URL**: In your `config.ts` file, change the API URL to your own API URL as follows:

  ```javascript
  // localhost
  export const API_URL = "http://your-localhost-api-url";

  // azure
  export const API_URL = "https://your-azure-api-url";
  ```

## 🚀 Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Database

3. Run the Project:
   Ensure your project is running to allow DDL auto to create the necessary tables in your database.

4. Import TSV Data:
   - In IntelliJ IDEA's Database tool, find the `role` table, right-click, and choose "Import Data From File".
   - Select the TSV file containing role data, map columns, and confirm import.
   - Note: Import data for the `role` table before proceeding to the `user` table.
   - After importing data for the `role` table, find the `user` table, right-click, and select "Import Data From File".
   - Choose the TSV file containing user data, map columns, and confirm import.

### Backend

5. Navigate to the backend directory: `cd backend`
6. Install dependencies: `mvn install`
7. Run the application: `mvn spring-boot:run`

### Frontend

8. Navigate to the frontend directory: `cd frontend`
9. Install dependencies: `npm install`
10. Run the application: `npm start`

## 🔧 Build and Deployment

**1. Angular Build and Copy Files to `resources/static`**:

- Use the Angular CLI to build your project with the command `ng build`.
- Then, copy the output files to the `resources/static` directory in your Spring Boot project.

**2. Docker Build and Push to Docker Hub**: Use Docker to build an image of your application and then push it to Docker Hub.

```bash
docker build -t your-dockerhub-username/your-image-name .

docker push your-dockerhub-username/your-image-name
```

**3. Mobile App Export**: Use Capacitor to prepare your app for mobile app.

- First, ensure that your `capacitor.config.json` file is properly configured. If not, delete it and create a new one using `npx cap init`.
- Next, install the necessary Capacitor packages:

  ```bash
   # For Android
   npm i @capacitor/android

   # For iOS
   npm i @capacitor/ios
  ```

- Then, add Android and iOS as platforms to your Capacitor project:

  ```bash
   # For Android
   npx cap add android

   # For iOS
   npx cap add ios
  ```

- Sync your project:

  ```bash
   npx cap sync
  ```

- Finally, open your project in Android Studio and Xcode to generate the APK and IPA files respectively:

  ```bash
   # For Android
   npx cap open android

   # For iOS
   npx cap open ios
  ```

- In Android Studio, use the "Generate Signed Bundle / APK" option in the "Build" menu to export your Android app. In Xcode, use the "Product" -> "Archive" option to export your iOS app.

- **Note**: When you run the npx cap sync command, Capacitor copies the built web assets (the output of your npm run build command) into each platform's native project. For Android, these assets are copied to `android/app/src/main/assets/public`. For iOS, they are copied to `ios/App/App/public`. This ensures that the latest version of your web app is included in the native project each time you build it.

**4. Windows App Export**:

- Build your Electron app:
  ```bash
  npm run electron-build
  ```
- Package your app with Electron Packager: This will generate a folder named PostShare-win32-x64 in the project root directory, which contains the Windows executable (.exe) file.
  ```bash
  electron-packager ./ PostShare --platform=win32
  ```
  Please replace the `PostShare` with your actual app name if it's different.
- Delete all folders inside `PostShare-win32-x64/resources/app` except for the `dist` folder. Note: Only delete folders, do not delete any files.
# BlogSphere
