[Go to step 11](https://github.com/seattleacademy/faceCam/tree/step11)
## Step 12 Identify age, gender, and expression of unknown faces

1.  Replace the drawFaceRecognitionResults() function with the following improved version
 ```javascript  
    function drawFaceRecognitionResults(results) {
        clearFaceNames()
        inputImgEl = document.getElementById("myImg");
        results = faceapi.resizeResults(results, inputImgEl);

        results.forEach(function(result) {
            let btn = document.createElement("button");
            if (result.bestMatch.label != 'unknown') {
                btn.innerText = result.bestMatch.label;
            } else {
                btn.innerText = result.age.toFixed(0) + ' year old ' + result.expressions.asSortedArray()[0].expression + ' ' + result.gender;
            }
            btn.title = (100 * (1 - result.bestMatch.distance)).toFixed(0) + ' %';
            btn.style.position = 'absolute';
            btn.style.top = result.detection.box.top + 'px';
            btn.style.left = result.detection.box.left + 'px';
            btn.className = 'faceNames';
            btn.dataset.person = result.bestMatch.label;
            btn.dataset.descriptor = result.descriptor;
            btn.addEventListener("click", personClick);
            document.getElementById("imagediv").appendChild(btn);
        })
    }
```
2. Confirm that unknown faces show age, expression, and gender. Confirm that when you hover over a button, percent match is displayed.

[Go to step 13](https://github.com/seattleacademy/faceCam/tree/step13)
