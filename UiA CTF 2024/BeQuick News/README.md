*An anonymous informant identity was compromised today. For now, the only communication between us and the informant has been through via our tip hotline. Could you figure out how the identity of the source may have been exposed?*

In this CTF challenge, from the web category, we are provided with a website at: https://bequick-news.chall.uiactf.no

The homepage tells us this website is a tip-submitting website where users can upload news story ideas or tips. Clicking the "Submit Tip" button brings us to the /upload directory.

We can view the source-code for this directory and analyze the upload functionality.

```
document.getElementById('uploadButton').addEventListener('click', function() {
    const fileInput = document.getElementById('fileInput');
    const originalFile = fileInput.files[0];

    if (!originalFile) {
        alert('Please select a file to upload.');
        return;
    }

    // Get cookie value
    const userCookie = getCookie('user');
    if (!userCookie) {
        alert('User cookie not found.');
        return;
    }

    // Get current timestamp in minutes
    const timestamp = Math.floor(Date.now() / 60000);

    // Generate filename
    const rawString = userCookie + timestamp;
    const secure = CryptoJS.MD5(rawString).toString();
    const newFileName = secure + '.txt';

    // Create FormData and append the file
    const formData = new FormData();
    formData.append('file', originalFile, newFileName);

    // Upload file
    // Replace 'your-server-endpoint' with your actual upload handling endpoint
    fetch('upload-tips', {
        method: 'POST',
        body: formData
    })
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error(error));
});

// Function to get cookie by name
function getCookie(name) {
    const value = `; ${document.cookie}`;
    const parts = value.split(`; ${name}=`);
    if (parts.length === 2) return parts.pop().split(';').shift();
}
```

It seems like the script gets our username from the cookie, aswell as the current timestamp in minutes, then concatenates the strings before performing a md5 hash on it. When the file is uploaded, the filename is then replaced with ```<hash>.txt```

If we try to upload a file, we are faced with the following error / response:

```
For now, we have limited access to this functionality to a few organizations. Only the shared user 'tipuser' is allowed to upload for now, to stop the recent waves of fake tips. Want access? Contact us.
```
