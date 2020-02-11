[Go to step 6](https://github.com/seattleacademy/faceCam/tree/step6)
## Step 7 Add age and gender recognition
1.  Add age and gender recognition detection to loadModels function
```javascript
        await faceapi.nets.ageGenderNet.load(weightsURI);
```
2.  Change drawFaceRecognitionResults btn.innerText and style to show age and gender of dections
 ```javascript  
 btn.innerText = result.age.toFixed(0) + ' year old ' + result.expressions.asSortedArray()[0].expression + ' ' + result.gender;
 btn.style = 'position:absolute; top:' + result.detection.box.top + 'px;left:' + result.detection.box.left + 'px; zindex:2';
 ```
3.  Add withAgeAndGender to the updateResults
```javascript
   results = await faceapi.detectAllFaces("myImg").withFaceLandmarks().withFaceExpressions().withAgeAndGender();
````
4. Confirm that age and gender is being predicted with uploaded images

[Go to step 8](https://github.com/seattleacademy/faceCam/tree/step8)
