[Go to step 12](https://github.com/seattleacademy/faceCam/tree/step12)
## Step 13 Add controls for tuning face recognition

1.  Add input controls for tuning before status indication line at the top of 'body' tag
 ```html  
    <label>Threshold:</label><input id="threshold" type="number" value=".30" step="0.01" min=".01" max="1.00">
    <label>maxDiff:</label><input id="maxDiff" type="number" value=".60" step="0.01" min=".01" max="1.00">
```
2. Within the 'head' tag, add a new '<style>' tag. Then within that tag, add style for number input to avoid up/down arrows
 ```html  
    <style>
        input[type=number]::-webkit-inner-spin-button, input[type=number]::-webkit-outer-spin-button { 
            -webkit-appearance: none; 
        }
    </style>
```
3.  Add threshold and maxDiff variables to top of script within 'body.'
```javascript
    var threshold = .3;
    var maxDiff = .6;
```
4.  Create makeFaceMatcher function
```javascript
   function makeFaceMatcher() {
        if (labeledFaceDescriptors.length > 0) {
            faceMatcher = new faceapi.FaceMatcher(labeledFaceDescriptors, maxDiff);
        }
    }
```
5.  Replace the two calls to faceMatcher in the addDescriptor() function
```javascript
makeFaceMatcher();
```
6.  Replace line to detectAllFaces in the updateResults function with these two lines
```javascript
    let options = new faceapi.SsdMobilenetv1Options({ minConfidence: Number(threshold) })
    results = await faceapi.detectAllFaces("myImg", options).withFaceLandmarks().withFaceExpressions().withAgeAndGender().withFaceDescriptors();
````
7.  Add eventListeners within the 'script' tag to respond to changes in the new input fields
```javascript
   document.getElementById('threshold').addEventListener('change', function(event) {
        threshold = event.target.value;
        makeFaceMatcher();
        updateResults();
    }, false);

    document.getElementById('maxDiff').addEventListener('change', function(event) {
        maxDiff = event.target.value;
        makeFaceMatcher();
        updateResults();
    }, false);

```
8.  Verify that the new controls work.  Lowering threshold will detect more faces.  Setting maxDiff close to 1 will make it easier to match faces but result in more false matches.

[Go to step 14](https://github.com/seattleacademy/faceCam/tree/step14)
