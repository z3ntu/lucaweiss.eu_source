---
layout: post
title:  "Deploying Unity WebGL with Apache"
date:   2015-10-31 12:25:57 +0100
tags: [unity3d, tutorial]
comments: true
---
<script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.7/jquery.min.js"></script>
<link rel="stylesheet" href="{{ site.baseurl }}/css/jquery.fancybox.css" type="text/css" media="screen" />
<script type="text/javascript" src="{{ site.baseurl }}/js/jquery.fancybox.pack.js"></script>
<script>
        $(document).ready(function() {
            $('.fancybox').fancybox();
        });
    </script>
# Deploying Unity WebGL on Apache

Have you had troubles getting your exported Unity WebGL project to work?

> GET /Release/UnityConfig.js **404 (Not Found)**
>
> GET /Release/fileloader.js **404 (Not Found)**
>
> GET /Release/1446299115.js **404 (Not Found)**

I got the instructions here:

- Export your Unity project as WebGL (probably already did this).
<a href="{{ site.baseurl }}/images/unity_webgl_export.png" class="fancybox" title="Export settings">Click for a screenshot of my Build Settings</a>

- Move every file from the `Release` folder into the `Compressed` folder. You can now delete the `Release` folder.
Your folder structure should look like this:

{% highlight text %}
.htaccess
index.html
Compressed
- many files (.datagz, .jsgz, .memgz)
TemplateData
- many image files, 1 .css & 1 .js file
{% endhighlight %}

- Enter `sudo a2enmod rewrite` in the terminal (to activate the `rewrite` Apache module).

- Open `/etc/apache2/apache2.conf` with your favorite text editor and find the following part:
`<Directory /var/www/>` / `<Directory /var/www/html/>` (or wherever your "main" folder is)

- Change `AllowOverride` from `None` to `All` and save the file.

I hope this helped you!
