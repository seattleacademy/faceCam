[Go to step 10](https://github.com/seattleacademy/faceCam/tree/step10)
## Step 11 Add status indicator
1.  At the top within the 'body' tag, add a span for status div with id imageDiv

```html
Status: <span id="status"></span>
```
2.  Add updateStatus function to 'script' tag
 ```javascript  
        function updateStatus(str) {
        document.getElementById("status").innerHTML = str;
    }
```
3. Add updateStatus calls to loadModels function
 ```javascript  
        updateStatus('loadModels');
        //let weightsURI = "weights";
        let weightsURI = "https://seattleacademy.github.io/faceRoster/weights";
        updateStatus('ssdMobilenetv1');
        await faceapi.nets.ssdMobilenetv1.load(weightsURI);
        updateStatus('faceLandmark68Net');
        await faceapi.nets.faceLandmark68Net.load(weightsURI);
        updateStatus('faceExpressionNet');
        await faceapi.nets.faceExpressionNet.load(weightsURI);
        updateStatus('ageGenderNet');
        await faceapi.nets.ageGenderNet.load(weightsURI);
        updateStatus('faceRecognitionNet');
        await faceapi.nets.faceRecognitionNet.loadFromUri(weightsURI)
```

4.  Add updateStatus calls to updateResults() function.
```javascript
    async function updateResults() {
        updateStatus('upateResults');
        results = await faceapi.detectAllFaces("myImg").withFaceLandmarks().withFaceExpressions().withAgeAndGender().withFaceDescriptors();

        results.forEach(function(result, i, results) {
            if (faceMatcher) {
                results[i].bestMatch = faceMatcher.findBestMatch(result.descriptor)
            } else {
                results[i].bestMatch = new faceapi.FaceMatch('unknown', 1);
            }
        })

        drawFaceRecognitionResults(results);
        updateStatus('');
    }

```
5. Confirm that status is updated as page loads and new images are recognized

[Go to step 12](https://github.com/seattleacademy/faceCam/tree/step12)
