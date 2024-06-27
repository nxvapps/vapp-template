# vapp-template
This is the template for a basic app. The idea is that this is the core. Everything extends this.

To see the spec and source of this extension see, see: https://github.com/nxvapps/vapp

## Building
```
. .INFO
docker build \
  --build-arg CUDA_VERSION=${CUDA_VERSION} \
  --build-arg UBUNTU_VERSION=${UBUNTU_VERSION} \
  --build-arg VIRTUALGL_VERSION=${VIRTUALGL_VERSION} \
  --build-arg LIBNVIDIA_VERSION=${LIBNVIDIA_VERSION} \
  --build-arg APP=${APP} \
  --build-arg APP_START=${APP_START} \
  --build-arg APP_INSTALL=${APP_INSTALL} \
  -t "${APP}:cuda${CUDA_VERSION}-ubuntu${UBUNTU_VERSION}" \
  .
```

## Components
There are a few critical components

### X11 Session
This is what powers everything. We run the app directly in an X11 session with no desktop.

### v4l2loopback
This needs to be enabled and loaded on the host in order to function. Please use the v4l2loopback_install.sh
script to set this up.

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

### How do I change the port?
You can change the port with the `PORT` environment variable at runtime. The default port is 7777/TCP
