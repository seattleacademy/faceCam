[Go to step 2](https://github.com/seattleacademy/faceCam/tree/step2)

## Step 3  Add file input to update image
1.  Surround img tag with div with id of imagediv.  Give the image a style for max-width of 800px.
```html
<div id="imagediv">
    <img id="myImg" src="bbt1.jpg" alt="" style="max-width: 800px;">
</div>
```
2.  Under the 'body' tag, add a file input element to upload files.
```html
<label>Upload Image:</label> <input type="file" onchange="uploadImage(event)" accept=".jpg, .jpeg, .png">
```
3.  Just before the end of the body, add the following function within a new 'script' tag to upload the image
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

[Go to step 4](https://github.com/seattleacademy/faceCam/tree/step4)

