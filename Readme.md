# Deploying a React App* to GitHub Pages

### 1. First created using create-react-app

### 2. After that Do Respective Project Work

### 3. Then Upload Project Work to Respective Repository
```bash
$ git init

$ git add "<folder_name>/<file_nae>" or $ git add .

$ git commit -m "first comment"

$ git branch -M main

$ git remote add origin https://github.com/ayandas1234/repository_name.git

git push -u origin main
```

### 3. After Done With Project Work Install the `gh-pages` npm package
```bash
 $ npm install gh-pages --save-dev
```

### 4. Add a `homepage` property to the `package.json` file
1. Open the `package.json` file in a text editor.
    ```bash
    $ vi package.json
    ```
2. Add a `homepage` property in this format*: `https://{username}.github.io/{repo-name}`
    ```bash
        {
            "name": "my-app",
            "version": "0.1.0",
          + "homepage": "https://gitname.github.io/react-gh-pages",
            "private": true,
    ```
At this point, the React app's `package.json` file includes a property named `homepage.`

### 5. Add deployment scripts to the `package.json` file
1. Add a `predeploy` property and a `deploy` property to the scripts object:
    ```bash
        "scripts": {
        +   "predeploy": "npm run build",
        +   "deploy": "gh-pages -d build",
            "start": "react-scripts start",
            "build": "react-scripts build",
    ```
- Remember This is for `TypeScript` when our Project Based On `TypeScript`, where source code files will have the `.tsx (for React components)` or `.ts (for non-React files)` extensions

- project is built using Vite, which outputs files to the `build`

2. For `JavaScript` Using `Vite` Server We use
    ```bash
        "scripts": {
            "predeploy": "npm run build",
            "deploy": "gh-pages -d dist"
        }
    ```
- because project is built using Vite, which outputs files to the `dist`

### 6. Most Important Fix Routing Issues (for React-Router)
- If you're using React Router, GitHub Pages serves only `index.html`, so refresh or deep linking (`/about`, `/contact`) may break.

## __Solution: Update `vite.config.js`__

Modify your `vite.config.js:`

```javascript
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [react()],
  base: '/repository-name/',  // <- Add this line
});

```

### 7. Then Run `npm run build` and then `npm run deploy`

### 8. After that run again few comands
```bash
$ git init

$ git add .

$ git push
```

### 9. then go to git repository where everything was uploaded -->> go to `settings` -->> `pages` here the published site link will appear

### 10. Rebuild and Deploy
- if there is soe chages occur After making these changes,**delete the old build, then rebuild and deploy again:**

- To delete the old build use the command `rm -rf dist` or `rm -rf build`

    #### 1️⃣ Using PowerShell:
        ```bash
            Remove-Item -Recurse -Force dist
        ```
    #### 2️⃣ Using Command Prompt (cmd):
        ```bash
            rmdir /s /q dist
        ```
    #### 3️⃣ Using Git Bash (if installed):
        ```bash
            rm -rf dist
        ```

    - After deleting the `dist` or `build` folder, __run the build and deploy commands again:__

    ```bash
    npm run build
    npm run deploy
    ```
### 11. After that Again Repeat the `step 8` and `step 9`.