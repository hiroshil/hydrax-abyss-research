# How to create modified .js scripts

## bundle.min.js

- Go to sources

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/57c43dd9-2186-486e-aea4-d18d221074c7)

- Right click and save as. Open the file

- Search for this `new WebSocket(e.url_tunnel`

- Add this after `console.warn("Copy this as videocdn URL:"+e.url);`

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/9f9f9096-d610-4286-82d7-8014a9dfedb2)

## playhydrax.min.js

- Same as before

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/676f6277-2df8-47ab-baad-88994a7bf42d)

- Search for this `.constructor("debugger")(),` and remove `debugger`

- It should look like this `.constructor("")(),`

- Search for this `function removeJwp() {` and remove the whole function

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/539c9066-3e82-47be-83f9-c4efda70abfe)
