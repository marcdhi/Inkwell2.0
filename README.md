
# Inkwell - The Note's App

Inkwell aims to serve as a chrome extension. User will be able to jot down points/notes along with browsing websites. The notes will auto sync with the user's Google Drive. Alongwith that, if the user uninstalls the extension, notes will still be available in the drive.


## Project Setup

Fork this repo from here.

```bash
git clone https://github.com/marcdhi/Inkwell2.0.git
cd inkwell
npm install
```
Set the upstream remote to the original repository url so that git knows where to fetch updates from in future:

```bash 
git remote add upstream https://github.com/marcdhi/Inkwell2.0.git
```
## Sample Git Workflow

* Follow the above installation guide.
* Create a new feature branch with ``` git checkout -b <name-of-your-feature-branch> ```
* Make changes and commit them in the feature branch.
* Once done developing, switch back to the main branch with ``` git checkout main ```; pull the latest version of the repo with ```git pull https://github.com/marcdhi/Inkwell2.0.git main```
* Switch back to the feature branch with ```git checkout <name-of-your-feature-branch>```. Apply the new changes on top of the latest version of the repo with ```git rebase main```
* Submit a Pull Request to the main branch.


## Loading the extension locally

Run the following command on the terminal
```bash
npm run build
```
Once the build is completed: 

* Enable the developer mode

[![devmode](https://www.linkpicture.com/q/devmode.png)](https://www.linkpicture.com/view.php?img=LPic6409fb8e01e6a783677026)


* Click on ```Load unpacked``` to load the extension

[![image](https://www.linkpicture.com/q/loaun.png)](https://www.linkpicture.com/view.php?img=LPic6409fc3d770fb1496871445)


* Now, point the extension to the ```dist``` folder to activate the ```manifest.json``` file. And press ```enter```


[![image](https://www.linkpicture.com/q/newww.png)](https://www.linkpicture.com/view.php?img=LPic6411c4aa82b561060808992)
