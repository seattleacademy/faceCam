# faceCam
A face recognition tutorial using the browser
## Step 3  Add file input to update image
1.  Surround img tag with div with id of imagediv.  Give the image a style for max-width of 800px.
```html
    <div id="imagediv">
        <img id="myImg" src="bbt1.jpg" alt="" style="max-width: 800px;">
    </div>
```
2.  Add file input element to upload files
```html
        <label>Upload Image:</label> <input type="file" onchange="uploadImage(event)" accept=".jpg, .jpeg, .png">
```
3.  Just before the close of the body, add the following script to upload the image
```html
    <script>
    async function uploadImage(e) {
        const imgFile = e.target.files[0]
        const img = await faceapi.bufferToImage(imgFile)
        document.getElementById("myImg").src = img.src
    }
    </script>
    ```
4. Verify that the image is replaced when you select a new image.  The function uses faceapi method to turn the image into a buffer.  Read up on async/await which is an advanced type of function.
5.  This step can be checked at https://github.com/seattleacademy/faceCam/tree/step3

