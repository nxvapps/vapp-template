# vapp
This is the template for a basic app. The idea is that this is the core. Everything extends this.

To see the spec and source of this extension see, see: https://github.com/nxvapps/vapp

## Components
There are a few critical components

### X11 Session
This is what powers everything. We run the app directly in an X11 session with no desktop.

### vapp
vapp is the underlying project this extends. Everything for the barebones of this project should exist
there. The template is for unique aspects and facilitation of apps.

### app_install.sh
This file, located at `files/root-files/root/app_install.sh`, is what is used to install the app during
the docker build routine. Add unique requirements here.

### app_run.sh
This file, located at `files/root-files/root/app_run.sh` is the file that specifies unique actions for
the app at runtime.

### root-files
This folder, located at `files/root-files`, if specified in your project will override any file in the files/root-files of vapp.
The intention is that you can override any file if unique issues present themselves.

## FAQ
This is for common, or what will be, common questions.

### How do I update the vapp repo in my project?
```
cd vapp
git pull
```
