# image-game-sample

This is an Image game sample using Azure Functions on Python and Azure Web App (for hosting the front end). The sample shows how to decode/encode images in JSON objects to send and receive over HTTP requests and to perform image tansformation on them. It uses Pillow library in Python to do rotation of images. This can easily be upgraded to do more complex transformations. 

The repository contains two apps-

1. **solve-image-APIs**: This is an Azure Function Project consisting of four APIs to do some basic image processing.
2. **solve-image-front-end**: This directory contains static files for the UI of the sample. The UI is built using Semantic UI Framework. 

The app when launched in the browser, shows a random image acquired from an Azure Storage Blob and a randomly rotated version of the image. The goal is to rotate the second image to match the first one. Something like this could easily be modified to create a new version of ReCAPTCHA that asks users to solve such tiny puzzles.

**In order to deploy this app, you would need-**

1. An Azure Storage with a Blob container filled with any number of random `png` images.
2. An Azure Function App to deploy the `solve-image-APIs` project.
3. An Azure Web App or a similar static hosting platform.

**A couple of notes to keep in mind-**

1. You must change the CORS settings in your Azure Function App to allow requests from your Azure Web App.
2. You must update the `solve-image-front-end/script.js` to use your function app instead of `http://localhost:7071`.
3. You must add an App Setting `AZURE_IMAGE_STORAGE_CONNECTION_STRING` with the connection string of the Azure Storage with images. You must also add an App Setting `AZURE_IMAGE_STORAGE_CONTAINER_NAME` with the name of your Blob container in the Azure Storage with images.

## Screenshots
  
**Homepage** 

<img width="554" alt="sample" src="https://user-images.githubusercontent.com/16520682/53797090-53c1f400-3eea-11e9-8111-784044fb048d.PNG">

**Solved**

<img width="664" alt="solved" src="https://user-images.githubusercontent.com/16520682/53798886-0182d200-3eee-11e9-9c2c-cf7ff7ce201d.PNG">

**Failed**

<img width="642" alt="failed" src="https://user-images.githubusercontent.com/16520682/53798904-0cd5fd80-3eee-11e9-8eb4-58582757ee54.PNG">


