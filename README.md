# faceCam
A face recognition tutorial using the browser
## Step 8 Add face recognition
1.  Add faceRecognitionNet detection to loadModels function
```javascript
	await faceapi.nets.faceRecognitionNet.loadFromUri(weightsURI)
```
2.  Replace the one line btn.innerHTML so lable is made
 ```javascript  
		btn.innerText = result.bestMatch.label;
```
3.  Add withFaceDescriptors to the updateResults function and add code to add bestMatch to results
```javascript
        results = await faceapi.detectAllFaces("myImg").withFaceLandmarks().withFaceExpressions().withAgeAndGender().withFaceDescriptors();
        faceMatcher = new faceapi.FaceMatcher(results);
        results.forEach(function(result, i, results) {

            if (results.length > 0) {
                results[i].bestMatch = faceMatcher.findBestMatch(result.descriptor)
            };
        })
````
4. Confirm that each face is labled with a unique name like person 1, person 2, etc.
5. This step can be checked at https://github.com/seattleacademy/faceCam/tree/step8

