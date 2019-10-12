[Go to step 14](https://github.com/seattleacademy/faceCam/tree/step14)

## Step 15 Add localStorage support

1.  Add after variable declaration at top of script
 ```javascript  
    //localStorage.removeItem('faceMatcher'); //Uncomment to clear faceMatcher on load
    if (localStorage.getItem('faceMatcher')) {
        faceMatcher = faceapi.FaceMatcher.fromJSON(JSON.parse(localStorage.getItem('faceMatcher')));
        labeledFaceDescriptors = faceMatcher.labeledDescriptors;
        maxDiff = faceMatcher.distanceThreshold;
        document.getElementById('maxDiff').value = maxDiff;
    }
```
2. Add after faceMatcher created in makeFaceMatcher function
 ```javascript  
    localStorage.setItem('faceMatcher', JSON.stringify(faceMatcher.toJSON()));
```
3. Verify that face are remembered when browser is relaunched

[Go to step 16](https://github.com/seattleacademy/faceCam/tree/step16)
