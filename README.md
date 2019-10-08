# faceCam
A face recognition tutorial using the browser
## Step 3  Add file input to update image
1.  Surround img tag with div with id of imagediv.  Give the image a style for max-width of 800px.
```html
    <div id="imagediv">
        <img id="myImg" src="bbt1.jpg" alt="" style="max-width: 800px;">
    </div>
```
1.  Download from https://github.com/justadudewhohacks/face-api.js/tree/master/dist and place face-api.js in the js directory.
1.  Just before the close of the body, add the following script to upload the image
```html
    <script>
    async function uploadImage(e) {
        const imgFile = e.target.files[0]
        const img = await faceapi.bufferToImage(imgFile)
        document.getElementById("myImg").src = img.src
    }
    </script>
    ```
1. Verify that the image is replaced when you select a new image.  The function uses faceapi method to turn the image into a buffer.  Read up on async/await which is an advanced type of function.
1.  This step can be checked at https://github.com/seattleacademy/faceCam/tree/step3

