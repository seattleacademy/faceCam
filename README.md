[Go to step 8](https://github.com/seattleacademy/faceCam/tree/step8)

## Step 9 Change name on button click
1.  Add these button attributes below btn.className = Facename in the drawFaceRecognitionResults function
```javascript
    btn.dataset.person = result.bestMatch.label;
    btn.dataset.descriptor = result.descriptor;
    btn.addEventListener("click", personClick);
  ```
2.  Add personClick function to script
 ```javascript  
    function personClick(e) {
        var newPerson = prompt("Please enter person's name:", e.target.dataset.person);
        if (newPerson == null || newPerson == "" || newPerson == "unknown") {} else {
            e.target.dataset.person = newPerson;
            e.target.innerHTML = newPerson;
        }
    }
```
4. Confirm that you can change each named person with a new name

[Go to step 10](https://github.com/seattleacademy/faceCam/tree/step10)
