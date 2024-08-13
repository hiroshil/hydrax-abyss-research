# [Python downloader](https://github.com/PatrickL546/Hydrax-Abyss.to-DownloadHelper-Python)

# [Userscript downloader](https://github.com/PatrickL546/Hydrax-Abyss.to-DownloadHelper-Userscript)

> [!WARNING]  
> Outdated and broken due to new update

> [!NOTE]  
> Still need to figure out how to download 1440p and 2160p videos

# Guide

- Test: [Abyss.to](https://abyss.to/)

### Dev tools blocking bypass

- Click on the URL and press F12

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/6b79adcb-d93e-45ce-a131-38c6e6001a9b)

- Or find it in the menu

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/2a1f9464-bd91-452a-a868-d4ac407e253a)

### Find Vid_ID for use with [Python downloader](https://github.com/PatrickL546/Hydrax-Abyss.to-DownloadHelper-Python)

- After you open the dev tools, and the debugger is paused, close the dev tools and it will remove the video and show the ID

![image](https://github.com/user-attachments/assets/38417ab3-2e12-4c7d-9af4-5b6cb6072f1c)

- Or click the Doc filter to find Vid_ID URL. Use filter `?v=` and refresh the page

![image](https://github.com/user-attachments/assets/a08dd452-6d75-4ec9-8a4a-d350c6e0bd1c)

- Get Vid_ID. `K8R6OOjS7`

![image](https://github.com/user-attachments/assets/22815265-681c-4f9d-b811-367b4428cfa4)

### For downloading

- Go to the sources tab and find `?v=K8R6OOjS7`. Decode the Base64 to get the info

![image](https://github.com/user-attachments/assets/3c2d4e6c-7954-45b3-bcd4-7dd8ebd67d7f)

![image](https://github.com/user-attachments/assets/be43ec90-dbbe-4656-9538-062fc0863d94)

- See [Download](#download) section below for an example URL

### Download from browser

- Use extensions like [Requestly](https://requestly.com/) to modify the headers and modify like below. Visit the link to download

- Modify request with links including `.trycloudflare.com`

```
Referer : https://abysscdn.com/
Sec-Fetch-Mode : cors
```

- Response header

```
Content-Disposition : attachment
```

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/8441179c-28e5-4ba7-b38a-c68093799440)

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/c97b6b34-212f-4348-b70f-c8a780de1925)

# Old method

## [Use modified .js](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/blob/master/Recommended.%20Download%20zip.md)

## [How to create modified .js scripts](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/blob/master/How%20to%20create%20modified%20.js%20scripts.md)

### Anti-debug bypass

- If a website has anti-debug, click this to bypass it and reload. This might not work on Firefox

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/1ad57d58-6fd8-41c8-9736-6ee7060d16d5)

### Find video file name

- Go to the network tab and click the Media filter to find the video file name. It should look like this `d34478903cd03b5fef`. Do not copy `.txt`

![image](https://github.com/user-attachments/assets/ea71c4ca-9c3d-4be4-8980-c9a051690889)

### Find Vid_ID URL

### If you are using the modified scripts

- Go to Console. Make sure the filter is set to Warnings only and Preserve log is checked

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/3eb8c862-5472-4b2f-8e18-a7e9875207b7)

- It should look like this `mmx9cibe11.globalcdn39.one`. Do not copy `wss://`. Replace it with `https://`

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/f36833d3-9d48-418e-862d-3237d003cb25)

### If you are NOT using the modified scripts

- Click the Websocket filter to find the videocdn URL. You might have to wait for the connection to expire. The site will reconnect, and the URL will show up here
- Another way is to disconnect/reconnect the internet connection
- It should look like this `sfbhnfiy1.globalcdn39.one`. Do not copy `wss://`. Replace it with `https://`

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/ab6c94c9-3d22-43b2-8291-73b3d6497879)

### Video source picker

Looking at the [bundle.min.js](https://iamcdn.net/players/bundle.min.js). It shows how to get different video sources

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/d74e1668-e56b-4c3b-b44d-e12489093a5c)

- The video file name without any prefix used in the URL is 360p, `www` prefix is 720p, `whw` prefix is 1080p
- `d34478903cd03b5fef` is 360p
- `www`+`d34478903cd03b5fef` is 720p
- `whw`+`d34478903cd03b5fef` is 1080p

# Download

- Combine the video cdn `https://sfbhnfiy1.globalcdn39.one/` with the prefix + video file name `whw`+`d34478903cd03b5fef` = `https://sfbhnfiy1.globalcdn39.one/whwd34478903cd03b5fef`

Here's an example Python code that downloads each video source

```Python
from requests import get

headers = {"Referer": "https://abysscdn.com"}

url_360p_480p = "https://sfbhnfiy1.globalcdn39.one/d34478903cd03b5fef"
response = get(url_360p_480p, headers=headers, stream=True)
with open("video_360p_480p.mp4", "wb") as f:
    for chunk in response.iter_content(chunk_size=64 * 1024):
        f.write(chunk)

url_720p = "https://sfbhnfiy1.globalcdn39.one/wwwd34478903cd03b5fef"
response = get(url_720p, headers=headers, stream=True)
with open("video_720p.mp4", "wb") as f:
    for chunk in response.iter_content(chunk_size=64 * 1024):
        f.write(chunk)

url_1080p = "https://sfbhnfiy1.globalcdn39.one/whwd34478903cd03b5fef"
response = get(url_1080p, headers=headers, stream=True)
with open("video_1080p.mp4", "wb") as f:
    for chunk in response.iter_content(chunk_size=64 * 1024):
        f.write(chunk)
```
