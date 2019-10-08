# faceCam
A face recognition tutorial using the browser
## Step 7 Add age and gender recognition
1.  Add age and gender recognition detection to loadModels function
```javascript
        await faceapi.nets.ageGenderNet.load(weightsURI);
```
2.  Change drawFaceRecognitionResults btn.innerText and style to show expression of dections
 ```javascript  
            btn.innerText = result.expressions.asSortedArray()[0].expression + ' ' + result.detection.classScore.toFixed(2);
            btn.style = 'position:absolute; top:' + result.detection.box.top + 'px;left:' + result.detection.box.left + 'px; zindex:2';
```
3.  Add withAgeAndGender to the updateResults
```javascript
   results = await faceapi.detectAllFaces("myImg").withFaceLandmarks().withFaceExpressions().withAgeAndGender();
````
4. Confirm that age and gender is being predicted with uploaded images
5. This step can be checked at https://github.com/seattleacademy/faceCam/tree/step7

