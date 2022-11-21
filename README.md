## Script to exploit `DOM XSS in jQuery anchor href attribute sink using location.search source` in the PortSwigger Web Security Lab

I recommend going through the <a href="https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-href-attribute-sink" target="_blank" rel="noopener noreferrer">lab</a>  manually first. This will increase learning. <br> Want a write-up? I have one <a href="https://pho3nix-writeups.github.io/codelabs/ctf-portswigger-web-security-academy-dom-xss-in-innerhtml-sink-using-source-location-search/index.html?index=..%2F..index#5" target="_blank" rel="noopener noreferrer">here</a>.

## Installation

### Clone Repo & Install Dependencies 

```
git clone https://github.com/pho3nix-writeups/wps-lab-dom-xss-in-jquery-anchor-href-attribute-sink-using-locationSearch-source-script.git && \
cd wps-lab-dom-xss-in-jquery-anchor-href-attribute-sink-using-locationSearch-source-script && \
pip install -r requirements.txt
```

![clone](https://user-images.githubusercontent.com/77143564/201503901-57f658aa-0961-404f-86a4-dcdadca8ddcb.jpeg)

What are you installing?
- <a href="https://pypi.org/project/colorama/" target="_blank" rel="noopener noreferrer">colorama</a>
- <a href="https://pypi.org/project/requests/" target="_blank" rel="noopener noreferrer">requests</a> 
- <a href="https://pypi.org/project/urllib3/" target="_blank" rel="noopener noreferrer">urllib3</a> 

---

## Usage

### Help Info

```
./exploit.py -h
```

```
usage: exploit.py [-h] [-u [url]] [-p [payload]]

This is a script to exploit DOM XSS in jQuery anchor href attribute sink using location.search source in the PortSwigger Web Security Lab.

options:
  -h, --help            show this help message and exit
  -u [url], --url [url]
                        your lab url, make sure to include the / at the end - example: ./exploit.py -u https://YOUR-LAB-ID.web-security-academy.net/
  -p [payload], --payload [payload]
                        your custom payload (optional) default: javascript:alert(document.domain)
```

### Custom Payload
The lab url is required. There is an option to use a custom payload. <br>

```
exploit.py -u <your lab url> -p <your custom payload>
``` 

If you don't include a payload `javascript:alert(document.domain)` will be used by default.


### Example of Use
Here's a link to the <a href="https://pho3nix-writeups.github.io/codelabs/ctf-portswigger-web-security-academy-dom-xss-in-innerhtml-sink-using-source-location-search/index.html?index=..%2F..index#5" target="_blank" rel="noopener noreferrer">script portion of the write-up</a>.<br>

---
## Errors

### Proxy Error
`exploit.py` requires a proxy (Burp Suite) open using `127.0.0.1:8080`. If a proxy isn't open, you'll get an error like the following.
![burperror](https://user-images.githubusercontent.com/77143564/201503965-6e1b2d0c-99d2-47a7-8e05-7b0c72758e5f.jpeg)

If you have a different proxy setup, you can edit it in `exploit.py` here: 

```
proxies = {
    'http': 'http://127.0.0.1:8080',
    'https': 'http://127.0.0.1:8080'
}
```

### Timeout Error
The Web Security Academy labs will time out after a bit. If you get a `[!] HTTP status code of 504 returned, but 200 was expected. Exiting...` error, make sure to check your browser. You need to click on <a href="https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-href-attribute-sink" target="_blank" rel="noopener noreferrer">access the lab</a> to generate a new lab session.
![error](https://user-images.githubusercontent.com/77143564/201504145-bb74fee4-e3c7-4dbe-aea6-cea05c8471e0.jpeg)

---
Have some ideas? Feel free to create an  <a href="https://github.com/pho3nix-writeups/wps-lab-dom-xss-in-jquery-anchor-href-attribute-sink-using-locationSearch-source-script/issues" target="_blank" rel="noopener noreferrer">issue</a>. <br>
Have fun. <br> Made with 💙 by Pho3nix
