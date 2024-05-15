# [Python downloader](https://github.com/PatrickL546/Hydrax-Abyss.to-DownloadHelper-Python)

# [Userscript downloader](https://github.com/PatrickL546/Hydrax-Abyss.to-DownloadHelper-Userscript)

# Guide

Not all websites use the same links, so you'll have to adapt to that

- Test: https://gojo2.xyz/asre-zero-224-pised/
- Password: nade

### Dev tools blocking bypass

- Click on the URL and press F12

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/6b79adcb-d93e-45ce-a131-38c6e6001a9b)

- Or find it in the menu

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/2a1f9464-bd91-452a-a868-d4ac407e253a)

### Find Vid_ID for use with [Python downloader](https://github.com/PatrickL546/Hydrax-Abyss.to-DownloadHelper-Python)

- After you open the dev tools, and the debugger is paused, close the dev tools and it will remove the video and show the ID

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/043480cf-4901-46fe-9afb-e02e671863e2)

- Or click the Doc filter to find Vid_ID URL. Use filter `?v=` and refresh the page

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/160b0a0c-7b7b-4f48-b6c4-0a2dd3405d1b)

- Get Vid_ID. `VswFqVUmq`

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/a63f88d6-4e6f-4237-bfe0-1692d1a3d315)

### For downloading

- Go to the sources tab and find `?v=VswFqVUmq`. Decode the Base64 to get the info

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/c23492cf-affe-466e-b7cb-d2d4a877b719)

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/25a8cd5a-63ba-4d31-bd0a-e20e3d973a08)

- Combine the "domain" and "id" as a link. And use the URL `https://abysscdn.com/?v=VswFqVUmq` as the Referer to download. See [Download](#download) section below for an example

# Old method

## [Use modified .js](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/blob/master/Recommended.%20Download%20zip.md)

## [How to create modified .js scripts](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/blob/master/How%20to%20create%20modified%20.js%20scripts.md)

### Anti-debug bypass

- If a website has anti-debug, click this to bypass it and reload. This might not work on Firefox

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/1ad57d58-6fd8-41c8-9736-6ee7060d16d5)

### Find video file name

- Go to the network tab and click the Media filter to find the video file name. It should look like this `ce0f5de002c90461a9`. Do not copy `.txt`

![image](https://github.com/PatrickL546/How-to-download-hydrax-abyss.to/assets/75874561/8847ebab-0239-493e-a6c4-6fa972e478fd)

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
- `ce0f5de002c90461a9` is 360p
- `www`+`ce0f5de002c90461a9` is 720p
- `whw`+`ce0f5de002c90461a9` is 1080p

# Download

- Combine the video cdn `https://sfbhnfiy1.globalcdn39.one/` with the prefix + video file name `whw`+`ce0f5de002c90461a9` = `https://sfbhnfiy1.globalcdn39.one/whwce0f5de002c90461a9`

Here's an example Python code that downloads each video source

```Python
from requests import get

headers = {"Referer": "https://abysscdn.com"}

url_360p_480p = "https://sfbhnfiy1.globalcdn39.one/ce0f5de002c90461a9"
response = get(url_360p_480p, headers=headers, stream=True)
with open("video_360p_480p.mp4", "wb") as f:
    for chunk in response.iter_content(chunk_size=64 * 1024):
        f.write(chunk)

url_720p = "https://sfbhnfiy1.globalcdn39.one/wwwce0f5de002c90461a9"
response = get(url_720p, headers=headers, stream=True)
with open("video_720p.mp4", "wb") as f:
    for chunk in response.iter_content(chunk_size=64 * 1024):
        f.write(chunk)

url_1080p = "https://sfbhnfiy1.globalcdn39.one/whwce0f5de002c90461a9"
response = get(url_1080p, headers=headers, stream=True)
with open("video_1080p.mp4", "wb") as f:
    for chunk in response.iter_content(chunk_size=64 * 1024):
        f.write(chunk)
```
