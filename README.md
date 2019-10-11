## Step 10 Add code to learn face descriptions
1.  Add personDescriptors and faceMatcher variables to the top of the script

```javascript
    var labeledFaceDescriptors = [];
    var faceMatcher = null;
```
2.  Add addDescript function add new person to faceMatch method.
```javascript
    function addDescriptor(newPerson, descriptor) {
        for (let i = 0; i < labeledFaceDescriptors.length; i++) {
            if (labeledFaceDescriptors[i].label == newPerson) {
                labeledFaceDescriptors[i].descriptors.push(new Float32Array(descriptor.split(',')));
                faceMatcher = new faceapi.FaceMatcher(labeledFaceDescriptors);
                return;
            }
        }
        descriptors = [];
        descriptors.push(new Float32Array(descriptor.split(',')));
        labeledFaceDescriptors.push(new faceapi.LabeledFaceDescriptors(newPerson, descriptors));
        faceMatcher = new faceapi.FaceMatcher(labeledFaceDescriptors);
    }
```
3. Call addDescriptor to the end of the if statement of the personClick function.
```javascript
    function personClick(e) {
        var newPerson = prompt("Please enter person's name:", e.target.dataset.person);
        if (newPerson == null || newPerson == "" || newPerson == "unknown") {} else {
            e.target.dataset.person = newPerson;
            e.target.innerHTML = newPerson;
            addDescriptor(newPerson, e.target.dataset.descriptor);
            updateResults();
        }
    }
```
4.  Change updateResults to 
```javascript
    async function updateResults() {
        results = await faceapi.detectAllFaces("myImg").withFaceLandmarks().withFaceExpressions().withAgeAndGender().withFaceDescriptors();

        results.forEach(function(result, i, results) {
            if (faceMatcher) {
                results[i].bestMatch = faceMatcher.findBestMatch(result.descriptor)
            } else {
                results[i].bestMatch = new faceapi.FaceMatch('unknown', 1);
            }
        })

        drawFaceRecognitionResults(results);
    }
```
5. Confirm that you can change each named person with a new name and that it recognizes learned faces
6. This step can be checked at https://github.com/seattleacademy/faceCam/tree/step10

