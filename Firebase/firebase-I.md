# Firebase I

## Deploy Angular project

1. to host a website, is necesary to configure a project in [Firebase Console](https://console.firebase.google.com/).
2. Go to the console and in the main directory of the angular project, start with Firebase using `firebase init`
3. Use `ng build` command to build the project. 
4. Configure the `firebase.json` file with the path builded previously. By defect `dist/project-name`.
5. To deploy use `firebase deploy -m "commit message" [--only hosting]`