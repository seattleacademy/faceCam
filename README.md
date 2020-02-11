[Go to step 13](https://github.com/seattleacademy/faceCam/tree/step13)
## Step 14 Add webCam support

1.  Add the follwing new 'script' tag to the top of 'head' to use secure connection for webcam
 ```html  
    <script>
        // Needed if webcam is used
    if (location.protocol == "http:") {
        location.protocol = "https:";
    }
    </script>
```
2. Add imgUploadInput id (id="imgUploadInout") to Upload Image label at the top of 'body' and create webCamToggle checkbox line after it
 ```html  
<label>Upload Image:</label> <input type="file" id="imgUploadInput" onchange="uploadImage(event)" accept=".jpg, .jpeg, .png">
<label>Webcam:</label><input id="webCamToggle" type="checkbox">
```
3.  Add video below img with id="myImg"
```html
<video style ="display:none;" "id="webCam"></video>
```
4.  Add srcId and webCamTimeout global variables under the 'script' tag within 'body'
```javascript
    var srcId = "myImg";
    var webCamTimeout = 0;
```
5.  Change reference "myImg" to srcID in drawFaceRecognitionResults function
```javascript
inputImgEl = document.getElementById(srcId);
```
6.  Change reference "myImg" to srcID in updateResults function
```javascript
results = await faceapi.detectAllFaces(srcId, options).withFaceLandmarks().withFaceExpressions().withAgeAndGender().withFaceDescriptors();
```
7.  Add timeOut at bottom of updateResults function when webCam is being used.
```javascript
if (document.getElementById('webCamToggle').checked) {
 webCamTimeout = setTimeout(updateResults, 200);
}
```
8.  Add toggleWebCam function
```javascript
function toggleWebCam(enable) {
    clearFaceNames()
    webCam = document.getElementById('webCam');
    let constraints = true;

    if (enable) {
        navigator.mediaDevices.getUserMedia({ video: constraints }).then(function(stream) {
            document.getElementById("webCam").width = stream.getTracks()[0].getSettings().width;
            document.getElementById("webCam").height = stream.getTracks()[0].getSettings().height;
            srcId = "webCam"
            document.getElementById("imgUploadInput").value = "";
            document.getElementById("myImg").style.display = "none";
            document.getElementById("webCam").style.display = "block";
            webCam.srcObject = stream;
            webCam.play().then(updateResults);
        });
    } else {
        if (webCam.srcObject) {
            webCam.srcObject.getTracks().forEach(function(track) {
                track.stop();
            });
        }
        webCam.src = "";
        srcId = "myImg";
        document.getElementById("webCam").style.display = "none";
        document.getElementById("myImg").style.display = "block";
        clearTimeout(webCamTimeout);
        updateResults();
    }
    document.getElementById('webCamToggle').checked = enable;
}
 ````
 9.  Add eventListeners to respond to changes in webCamToggle checkbox
 ```javascript
document.getElementById('webCamToggle').addEventListener('change', function(event) {
    toggleWebCam(event.target.checked);
}, false);
```
10. Change addPerson function so update is not called when webCamTimer is in use
```javascript
if (!document.getElementById('webCamToggle').checked) {
    updateResults();
}
```
11. Verify that the webCam feature operates correctly

[Go to step 15](https://github.com/seattleacademy/faceCam/tree/step15)
