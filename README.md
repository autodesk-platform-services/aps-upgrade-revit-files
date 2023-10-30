# Upgrade Revit files with Design Automation

[![Node.js](https://img.shields.io/badge/Node.js-14.0-blue.svg)](https://nodejs.org/)
[![npm](https://img.shields.io/badge/npm-6.0-blue.svg)](https://www.npmjs.com/)
![Platforms](https://img.shields.io/badge/Web-Windows%20%7C%20MacOS%20%7C%20Linux-lightgray.svg)

[![OAuth2](https://img.shields.io/badge/OAuth2-v2-green.svg)](http://developer.autodesk.com/)
[![Data-Management](https://img.shields.io/badge/Data%20Management-v1-green.svg)](http://developer.autodesk.com/)
[![Design-Automation](https://img.shields.io/badge/Design%20Automation-v3-green.svg)](http://developer.autodesk.com/)


![Windows](https://img.shields.io/badge/Plugins-Windows-lightgrey.svg)
![.NET](https://img.shields.io/badge/.NET%20Framework-4.8-blue.svg)
[![Revit-2023](https://img.shields.io/badge/Revit-2023-lightgrey.svg)](http://autodesk.com/revit)


![Advanced](https://img.shields.io/badge/Level-Advanced-red.svg)
[![MIT](https://img.shields.io/badge/License-MIT-blue.svg)](http://opensource.org/licenses/MIT)

# Description

This sample demostrated how to upgrade Revit project/family/template to the latest version using Design Automation for Revit API, including upgrade one file or one folder.

# Thumbnail
![thumbnail](/thumbnail.png)

# Main Parts of The Work
1. Create a Revit Plugin to be used within AppBundle of Design Automation for Revit. Please check [PlugIn](./FileUpgrader/PlugIn/) 
2. Create your App, upload the AppBundle, define your Activity, you can simply use the `**Configure**` button in the Web Application to create the Appbundle & Activity.
3. Create the Web App to call the workitem.

# Web App Setup

## Prerequisites

1. **APS Account**: Learn how to create a APS Account, activate subscription and create an app at [this tutorial](https://tutorials.autodesk.io/). 
2. **Visual Code**: Visual Code (Windows or MacOS).
3. **ngrok**: Routing tool, [download here](https://ngrok.com/)
4. **Revit 2023**: required to compile changes into the plugin
5. **JavaScript ES6** syntax for server-side.
6. **JavaScript** basic knowledge with **jQuery**


For using this sample, you need an Autodesk developer credentials. Visit the [Autodesk Developer Portal](https://developer.autodesk.com), sign up for an account, then [create an app](https://developer.autodesk.com/myapps/create). For this new app, use **http://localhost:3000/api/aps/callback/oauth** as Callback URL, although is not used on 2-legged flow. Finally take note of the **Client ID** and **Client Secret**.

## Running locally

Install [NodeJS](https://nodejs.org), version 14 or newer.

Clone this project or download it (this `nodejs` branch only). It's recommended to install [GitHub desktop](https://desktop.github.com/). To clone it via command line, use the following (**Terminal** on MacOSX/Linux, **Git Shell** on Windows):

    git clone https://github.com/Autodesk-Platform-Services/aps-upgrade-revit-files

Install the required packages using `npm install`.

### ngrok

Run `ngrok http 3000` to create a tunnel to your local machine, then copy the address into the `APS_WEBHOOK_URL` environment variable. Please check [WebHooks](https://aps.autodesk.com/en/docs/webhooks/v1/tutorials/configuring-your-server/) for details.

### Environment variables

Set the enviroment variables with your client ID & secret and finally start it. Via command line, navigate to the folder where this repository was cloned and use the following:

Mac OSX/Linux (Terminal)

    npm install
    export APS_CLIENT_ID=<<YOUR CLIENT ID FROM DEVELOPER PORTAL>>
    export APS_CLIENT_SECRET=<<YOUR CLIENT SECRET>>
    export APS_CALLBACK_URL=<<YOUR CALLBACK URL>>
    export APS_WEBHOOK_URL=<<YOUR DESIGN AUTOMATION FOR REVIT CALLBACK URL>>
    export DESIGN_AUTOMATION_NICKNAME=<<YOUR DESIGN AUTOMATION FOR REVIT NICK NAME>>
    export DESIGN_AUTOMATION_ACTIVITY_NAME=<<YOUR DESIGN AUTOMATION FOR REVIT ACTIVITY NAME>>
    export DESIGN_AUTOMATION_ACTIVITY_ALIAS=<<YOUR DESIGN AUTOMATION FOR REVIT ACTIVITY ALIAS>>    
    npm start

Windows (use **Node.js command line** from Start menu)

    npm install
    set APS_CLIENT_ID=<<YOUR CLIENT ID FROM DEVELOPER PORTAL>>
    set APS_CLIENT_SECRET=<<YOUR CLIENT SECRET>>
    set APS_CALLBACK_URL=<<YOUR CALLBACK URL>>
    set APS_WEBHOOK_URL=<<YOUR DESIGN AUTOMATION FOR REVIT CALLBACK URL>>
    set DESIGN_AUTOMATION_NICKNAME=<<YOUR DESIGN AUTOMATION FOR REVIT NICK NAME>>
    set DESIGN_AUTOMATION_ACTIVITY_NAME=<<YOUR DESIGN AUTOMATION FOR REVIT ACTIVITY NAME>>
    set DESIGN_AUTOMATION_ACTIVITY_ALIAS=<<YOUR DESIGN AUTOMATION FOR REVIT ACTIVITY ALIAS>>
    npm start

**Note.**
environment variable examples:
- APS_CALLBACK_URL: `http://localhost:3000/api/aps/callback/oauth`
- APS_WEBHOOK_URL: `http://808efcdc123456.ngrok.io/api/aps/callback/designautomation`

The following are optional:
- DESIGN_AUTOMATION_NICKNAME: Only necessary if there is a nickname, APS client id by default.
- DESIGN_AUTOMATION_ACTIVITY_NAME: Only necessary if the activity name is customized, FileUpgraderAppActivity by default.
- DESIGN_AUTOMATION_ACTIVITY_ALIAS: Only necessary if the activity alias is customized, dev by default.

### Using the app

Open the browser: [http://localhost:3000](http://localhost:3000), there are 2 ways to upgrade files: 

1. Select Revit file in BIM360 Hub from Source File/Folder, Right Click and select `Upgrade to Revit 2023`. It will create a new version after successfully upgraded.
2. Select Source Folder and Destination Folder, then click `Upgrade`, it will upgrade all the files under the folder to destinated folder.
`Note`: When you deploy the app, you have to open the `Configure` button to create the AppBundle & Activity before running the upgrade feature, please check the video for the steps at [https://youtu.be/1NCeH7acIko](https://youtu.be/1NCeH7acIko)

## Deployment

To deploy this application to Heroku, the **Callback URL** for APS must use your `.herokuapp.com` address. After clicking on the button below, at the Heroku Create New App page, set your Client ID, Secret, Callback URL and Revit Design Automation variables for APS.

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/Autodesk-Platform-Services/aps-upgrade-revit-files)

Watch [this video](https://www.youtube.com/watch?v=Oqa9O20Gj0c) as reference on how to deploy samples to Heroku.



## Packages used

The [Autodesk APS](https://www.npmjs.com/package/forge-apis) packages is included by default. Some other non-Autodesk packaged are used, including [socket.io](https://www.npmjs.com/package/socket.io), [express](https://www.npmjs.com/package/express).

## Further Reading

Documentation:
- [Design Automation API](https://aps.autodesk.com/en/docs/design-automation/v3/developers_guide/overview/)
- [BIM 360 API](https://developer.autodesk.com/en/docs/bim360/v1/overview/) and [App Provisioning](https://aps.autodesk.com/blog/bim-360-docs-provisioning-forge-apps)
- [Data Management API](httqqqps://developer.autodesk.com/en/docs/data/v2/overview/)

Desktop APIs:

- [Revit](https://knowledge.autodesk.com/support/revit-products/learn-explore/caas/simplecontent/content/my-first-revit-plug-overview.html)

## Tips & Tricks
- Before using the sample to call the workitem, you need to setup your Appbundle & Activity of Design Automation, you can simply use the `Configure` button in the Web Application to create the Appbundle & Activity([https://youtu.be/1NCeH7acIko](https://youtu.be/1NCeH7acIko)). 

## Troubleshooting

After installing Github desktop for Windows, on the Git Shell, if you see a ***error setting certificate verify locations*** error, use the following:

    git config --global http.sslverify "false"

## Limitation
- For Demo purpose, we only support **5** files to be upgraded as maximum
- Only support upgrading to Revit 2023
- Override is not implemented yet
- Only support upgrade file from/to BIM360
- Client JavaScript requires modern browser

## License

This sample is licensed under the terms of the [MIT License](http://opensource.org/licenses/MIT). Please see the [LICENSE](LICENSE) file for full details.

## Written by

Zhong Wu [@johnonsoftware](https://twitter.com/johnonsoftware), [Autodesk Partner Development](http://aps.autodesk.com)
