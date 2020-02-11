[Go to step 4](https://github.com/seattleacademy/faceCam/tree/step4)
## Step 5  Place button over each face with classScore
1.  Add a clearFaceTag function to remove old buttons with class faceName
```javascript
    function clearFaceNames() {
        let paras = document.getElementsByClassName('faceNames');
        while (paras[0]) {
            paras[0].parentNode.removeChild(paras[0]);
        }
    }
```
2.  Create drawFaceRegonition function to create an place button with classScore
 ```javascript  
    function drawFaceRecognitionResults(results) {
        clearFaceNames()
        inputImgEl = document.getElementById("myImg");
        results = faceapi.resizeResults(results, inputImgEl);

        results.forEach(function(result) {
            let btn = document.createElement("button");
            btn.innerText = result.classScore.toFixed(2);
            btn.style = 'position:absolute; top:' + result.box.top + 'px;left:' + result.box.left + 'px; zindex:2';
            btn.className = 'faceNames';
            document.getElementById("imagediv").appendChild(btn);
        })
    }
```
3.  Add call to drawFaceRecognitionResults and the bottome of updateResults function.
```javascript
      drawFaceRecognitionResults(results);
```
4. Verify that class scores are placed above each face on original picure.

[Go to step 6](https://github.com/seattleacademy/faceCam/tree/step6)
