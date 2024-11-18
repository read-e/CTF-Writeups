# Spider
Liam Reidy

**Instructions:** Some paths are left deliberately unvisited, shielded from the spider’s web. But what’s intentionally hidden often holds the most valuable secrets.

The `robots.txt` file:

```
# robots.txt for http://www.hotmail.com/
# do not delete this file, contact MSCOMSYS for edits!!!!
#

User-agent: *
Disallow: /isapi/	# keep robots out of the executable tree
Disallow: /scripts/
Disallow: /australia/careers/library/
Disallow: /backoffice/
Disallow: /canada/Library/mnp/2/aspx/
Disallow: /careers/international/
Disallow: /catalog/
Disallow: /communities/bin.aspx
Disallow: /communities/eventdetails.mspx
Disallow: /communities/blogs/PortalResults.mspx
Disallow: /communities/rss.aspx
Disallow: /downloads/info.aspx
Disallow: /france/formation/centres/planning.asp
Disallow: /france/mnp_utility.mspx
Disallow: /germany/library/images/mnp/
Disallow: /germany/mnp_utility.mspx
Disallow: /hwdev/
Disallow: /hwdq/
Disallow: /ie/ie40/
Disallow: /info/customerror.htm
Disallow: /info/smart404.asp
Disallow: /intl_kb/
Disallow: /intlkb/
Disallow: /isapi/
Disallow: /japan/enable/textview.asp
Disallow: /japan/hwdq/hwtest/
Disallow: /japan/mnp_utility.mspx
Disallow: /japan/products/library/search.asp
Disallow: /japan/showcase/print/default.aspx
Disallow: /japan/terminology/query.asp
Disallow: /library/errorpages/smarterror.aspx
Disallow: /library/toolbar/3.0/
Disallow: /mnp_utility.mspx
Disallow: /netherlands/mnp_utility.mspx
Disallow: /portugal/consumo/
Disallow: /proxy/
Disallow: /resources/casestudies/casestudyimageshow.asp
Disallow: /resources/casestudies/CompanyLogoShow.asp
Disallow: /resources/casestudies/ddi/companylogoshow.asp
Disallow: /resources/casestudies/ddi/showfile.asp
Disallow: /resources/casestudies/FindCaseStudyResults.aspx
Disallow: /resources/casestudies/showfile.asp
Disallow: /servers/
Disallow: /sna/
Disallow: /solutions/
Disallow: /technet/support/ee/
Disallow: /top_secret_experiments/
Disallow: /uk/mnp_utility.mspx
Disallow: /windows.netserver/
Disallow: /windows/catalog/
Disallow: /windows/embedded/
Disallow: /windows/powered/
Disallow: /windowsmobile/catalog/
Disallow: /winhec/
```

Clearly the `/top_secret_experiments/` is suspicious.

That page had the flag `EKO{classic_but_easy}` in the flag1.txt file. This directory had other flags for some of the other web challenges, but I was unable to solve them.