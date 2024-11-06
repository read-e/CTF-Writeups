# Roboto Sans
Liam Reidy

**Instructions:** The flag is somewhere on this web application not necessarily on the website. Find it.

Given the name, I thought the flag might have something to do with the font. I parsed the api requests for the font, but they weren't custom, they were regular fonts distributed by Google and Cloudflare.

After not finding anything suspicious on the website, I checked the `robots.txt` file. Here's what it said:
```
User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/
```

Clearly there is base64 because of the `==`, so let's see what it means unencoded:
```
ZmxhZzEudHh0         = flag1.txt
anMvbXlmaW           = js/myfi
anMvbXlmaWxlLnR4dA== = js/myfile.txt
svssshjweuiwl        = *gibberish*
oiho                 = ¢(h   [lol, ohio]
bsvdaslejg           = *gibberish*
```

`/flag1.txt` didn't have the flag, but `js/myfile.txt` did!
