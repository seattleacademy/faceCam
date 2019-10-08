# faceCam
A face recognition tutorial using the browser
## Step 4  Load models and recognize faces
1.  In the script tag at the bottom of index.html, add the loadModels function to load weights. 
```javascript
    async function loadModels() {
        //let weightsURI = "weights";
        let weightsURI = "https://seattleacademy.github.io/faceRoster/weights";
        await faceapi.nets.ssdMobilenetv1.load(weightsURI);
    }
```
1.  Add also to the scripts to display in the console faces detected.
 ```javascript  
    async function updateResults() {
        results = await faceapi.detectAllFaces("myImg");
        console.log(results);
    } 
```
1.  Just before the end of the script tag, call the function loadModels followed by updateResults after the models have been loaded.
```javascript
    loadModels().then(updateResults);
```
1.  Add updateResults() at the end of the uploadImage function
```javascript
    loadModels().then(updateResults);
````
1. Remove any other calls to console. 
1. Check in the debugger that the software is detecting all face in the sample and uploaded images. In particular, the score should give a value that signifies the likelyhood of matching a face.
1. This step can be checked at https://github.com/seattleacademy/faceCam/tree/step4

