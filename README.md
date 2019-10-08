# faceCam
A face recognition tutorial using the browser
## Step 6  Add expression detection
1.  Add landmark and expression detection to loadModels function
```javascript
        await faceapi.nets.faceLandmark68Net.load(weightsURI);
        await faceapi.nets.faceExpressionNet.load(weightsURI);
```
2.  Change drawFaceRecognitionResults btn.innerText and style to show expression of dections
 ```javascript  
            btn.innerText = result.expressions.asSortedArray()[0].expression + ' ' + result.detection.classScore.toFixed(2);
            btn.style = 'position:absolute; top:' + result.detection.box.top + 'px;left:' + result.detection.box.left + 'px; zindex:2';
```
3. Add withFaceExpression to updateResults
```javascript
        results = await faceapi.detectAllFaces("myImg").withFaceLandmarks().withFaceExpressions()
```
4. Add updateResults to uploadImage function
```javascript
updateResults()
```
5. Check with pictures of happy, sad, surprised faces etc. to confirm matchings
6. This step can be checked at https://github.com/seattleacademy/faceCam/tree/step6

