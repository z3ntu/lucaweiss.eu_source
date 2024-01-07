---
title:  "Deploying Unity WebGL with Apache"
date:   2015-10-31 12:25:57 +0100
tags: [unity3d, tutorial]
comments: true
aliases:
    - /2015/10/31/Deploying-Unity-WebGL-with-Apache.html
---

# Deploying Unity WebGL on Apache

Have you had troubles getting your exported Unity WebGL project to work?

> GET /Release/UnityConfig.js **404 (Not Found)**
>
> GET /Release/fileloader.js **404 (Not Found)**
>
> GET /Release/1446299115.js **404 (Not Found)**

I got the instructions here:

* Export your Unity project as WebGL (probably already did this).
<a href="/images/unity_webgl_export.png" target="_blank">Click for a screenshot of my Build Settings</a>

* Move every file from the `Release` folder into the `Compressed` folder. You can now delete the `Release` folder.
Your folder structure should look like this:

```
.htaccess
index.html
Compressed
* many files (.datagz, .jsgz, .memgz)
TemplateData
* many image files, 1 .css & 1 .js file
```

* Enter `sudo a2enmod rewrite` in the terminal (to activate the `rewrite` Apache module).

* Open `/etc/apache2/apache2.conf` with your favorite text editor and find the following part:
`<Directory /var/www/>` / `<Directory /var/www/html/>` (or wherever your "main" folder is)

* Change `AllowOverride` from `None` to `All` and save the file.

I hope this helped you!
