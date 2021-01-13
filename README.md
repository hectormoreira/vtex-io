# vtex-io
Notes for windows instalation

[Vtex IO - Full documentation](https://vtex.io/docs/)

# Step 1 Installing the VTEX IO Toolbelt
## VTEX IO CLI installation and command reference [Doc](https://vtex.io/docs/recipes/development/vtex-io-cli-installation-and-command-reference/)

To install the VTEX IO’s CLI, you need to ensure that Node.js and Yarn are installed on your machine. 

```
<!-- Install global Yarn-->
$ npm install -g yarn

<!-- Install global vtex-->
$ yarn global add vtex
```
>Test yarn with: `$ yarn help`

>If response this error:  "...cannot be loaded because running scripts is disabled on this system. For more information, see about_Execution_Policies". Please run this in your PowerShell: `$ Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`

>To confirm that the installation occurred as expected, you can execute the `vtex` command. This should display all available commands in a help text.

### Troubleshooting
1. Runs the `yarn global bin` command in your terminal. It will return the path in which the yarn global binaries were saved.
2. Copy it to your clipboard. This path now must be added to the Windows Environment Variable Path.
3. Click on the windows button and search for environment. Then, click on `Edit the system environment variables`.
4. In the `System Properties` dialog, click on the `Environment Variables...` button.
5. In `User Variables`, select `Path` and then click on the `Edit...` button.
6. Click on the `New` button to add a new path to the search.
7. Paste the yarn global binary path copied in step 2 and click `OK` when prompted. This will save your changes.
5. Log in and log out of your terminal for the changes to take effect.


# Step 2 - Logging in to your VTEX account

```
$ vtex login {account}
```
By running the command, a browser window will open and ask for your credentials.
# Step 3 - Creating your own workspace
To start performing the desired changes in your storefront, we will need to create a Development workspace.

Use the vtex use command in order to start configuring Store Framework in your store. For example:
```
$ vtex use examplename
```

>The `vtex use` command makes all your operations run in the workspace specified in the command, which means you can shift your operations to Master simply by running `vtex use master` in Toolbelt, for example.

# Step 4 - Accessing your store using a workspace

>Tip: you can simply run `vtex browse` in your terminal to automatically open your browser using the workspace and account in which you are working.


Having created your own development workspace in VTEX IO, you can now go to your store by accessing https://{workspace}--{account}.myvtex.com, where {workspace} should be replaced with the name of the workspace that you've just created and {account} with the name of the VTEX account in which you are working.

# Step 5 - Installing the Store Theme app
VTEX IO Toolbelt offers the `vtex init` command which can quickly copy the Store Theme app repository to your computer, where it may be configured and fine-tuned according to your business needs.
1. Using your terminal, navigate to an already existing local files directory where you want Store Theme to be copied to:
```
$ cd {example folder}
```
>Note that {example folder} should be replaced with the folder name where the Store Theme is going to be copied to.

2. Run the `vtex init` command:
```
$ vtex init
```
3. Select the `store-theme` option and confirm that you want to download the theme folder to the destination you just chose:
>Once you select the `store-theme` option, Toolbelt will ask you for important information about the app, such as a value for the vendor, name, title and description. With the exception of vendor, press enter to keep each field's predefined values
4. Replace the predefined vendor value with the account name of the store that you are developing so that you'll be able to correctly publish its theme app later on.

##  Understanding the Store Theme's structure
Once you select the `store-theme` option, Toolbelt will create a copy of the Store Theme app in your local files, allowing you to work on it as you please.

Open the newly created Store Theme folder in your local files using any code editor, such as Visual Studio Code. You can also use your terminal directly to achieve the same result:
```
$ cd store-theme
```

- `manifest.json` - App's main file. It stores important metadata, such as the app's vendor, name, version, dependencies and builders(https://vtex.io/docs/concepts/builders/).
- `store` - Folder responsible for defining the store's templates. It's where you configure each page's components and properties.
- `styles`: folder responsible for setting the store's visual theme. It's where you configure colors, typography and anything related to the store's style


## Command Reference VTEX IO
Every command executed in Toolbelt must begin with vtex, irrespective of its name, as can be seen in the examples in the command table below.

| Command name | Functionality | Example |
|-----------|--------|-------------|
|`add`|Adds an app to the dependencies of the app you are currently working on.	|`vtex add vtex.store-header@2.x`|
|`browse`|Opens an endpoint in a browser window based on the current logged in account, workspace and environment data.|`vtex browse`|
|`deploy`|Publishes an app as a stable version. It only works in apps already published as a release candidate version.|`vtex deploy vtex.modal-layout@0.1.1`|
|`deprecate`| Deprecates an app's version.|`vtex deprecate vtex.store-components@3.104.2`|
`deps list`|Lists the apps dependencies of the workspace in which you are working.|`vtex deps list`|
|`deps update`|Updates all app dependencies of the workspace in which you are working or a single app dependency (when specified).|`vtex deps update` or `vtex deps vtex.product-summary@2.52.0`|
|`deps diff`|Compares app dependencies list of two workspaces and lists the apps that appear in both.|`vtex deps diff workspace1 workspace2`|
|`edition`|Gets the edition of the account you are logged in.|`vtex edition`|
|`edition set`|Sets an edition for the account you are logged in.|`vtex edition set vtex.edition-store@2.x`|
|`init`|Displays a list with boilerplate files or directories for new VTEX apps.|`vtex init`|
|`install`|Installs an app to the account you are logged into.|`vtex install vtex.store-drawer@0.8.0`|
|`link`|Locally links the app directory you are working into the development workspace you are working on.|`vtex link`|
|`list`|Lists all VTEX apps running in the account you are logged into.|`vtex list`|
|`local account`|Displays the account name you are logged into and copies it to the clipboard.|`vtex local account`
|`local workspace`|Displays the workspace name you are working in and copies it to the clipboard.|`vtex local workspace`|
|`local token`|Displays the user's authentication token current being used and copies it to the clipboard.|`vtex local token`|
|`promote`|Promotes the production workspace you are working in to Master.|`vtex workspace promote`|
|`publish`|Publishes the app as a release candidate version.|`vtex publish vtex.menu@2.23.1` or `vtex publish`|
|`redirects import`|Adds a URL redirect into the account and workspace you are logged into.|`vtex redirects import {fileName}.csv`|
|`redirects export`|Gets existing redirects from the account and workspace you are logged into.|`vtex redirects export {fileName}.csv`|
|`redirects delete`|Deletes redirects in the the account and workspace you are logged into.|`vtex redirects delete {urlPath}`|
|`release`|Only for git users. When executed in the app's directory, it releases the app's new version in the `manifest.json` file according to SemVer (semantic versioning) best practices, updates the `CHANGELOG.md` file, assigns commit tags and sends the performed changes to the app's repository.|`vtex release major beta`|
|`support`|Logs you into an account using a support role.|`vtex support storecomponents`|
|`test`|Runs the app's unit tests according to the directory you are in (in case the app has any tests already configured for it).|`vtex test`|
|`undeprecate`|Reverts an app's deprecation.|`vtex undeprecate vtex.store-components@3.104.2`|
|`uninstall`|Uninstalls an app from the account you are logged into.|`vtex uninstall vtex.menu@2.23.1`|
|`unlink`|Unlinks the app directory you are in from the development workspace you are working in.|`vtex unlink`|
|`update`|Update all installed apps to the latest version in the account you are logged into (valid only for patches and minors, Majors are not updated when using this command).|`vtex update`|
|`url`|Displays a complete URL in the terminal, based on the current logged in account, workspace and environment data.|`vtex url`|