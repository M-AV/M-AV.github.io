<div class='post_title_wrapper'> 
	<h1 class='post_title'>Security advisories </h1>
</div>
In the fall 2014, I started (as part of my Master's thesis) to look into web security and common vulnerabilities. Here is a list of all vulnerabilities found since then where I can claim at least some of the credit. 

# WordPress plugins
|  Name                            |     Version       | Vulnerability     |
| :------------------------------: | :---------------: | :---------------: |
| [WP-FB Autoconnect][WPP-1]       | 4.0.5             | Stored XSS & CSRF |
| [Facebook Like Box][WPP-2]       | 2.8.2             | Stored XSS & CSRF |
| [WP-ViperGB][WPP-3]              | 1.3.10            | Stored XSS & CSRF |
| [Simple Sticky Footer][WPP-4]    | 1.3.2             | Stored XSS & CSRF |
| [IP Ban][WPP-5]                  | 1.2.3             | Stored XSS & CSRF |
| [Lightbox Photo Gallery][WPP-6]  | 1.0               | Stored XSS & CSRF |
| [Our Team Showcase][WPP-7]       | 1.2               | Stored XSS & CSRF |
| [Sliding Recent Posts][WPP-8]    | 1.0.0             | Stored XSS & CSRF |
| [Sliding Social Icons][WPP-9]    | 1.61              | Stored XSS & CSRF |
| [Timed Popup][WPP-10]            | 1.3               | Stored XSS & CSRF |
| [Simple Visitor Stat][WPP-11]    | 1.0               | Stored XSS        |
| [WP Constuction Mode][WPP-12]    | 1.91              | Reflected XSS     |

<br />  

# Other vulnerabilities

|      Name                      |     Version       | Vulnerability |
| :----------------------------: |:-----------------:| :------------:|
| [HumHub Mail Module][HumHub-1] | 0.5.8             | Reflected XSS |


[WPP-1]: http://packetstormsecurity.com/files/129508/WordPress-WP-FB-AutoConnect-4.0.5-CSRF-XSS.html  "PacketStorm: WordPress WP-FB-AutoConnect 4.0.5 CSRF/XSS"
[WPP-2]: http://packetstormsecurity.com/files/129506/WordPress-Facebook-Like-Box-2.8.2-CSRF-XSS.html "PacketStorm: WordPress Facebook Like Box 2.8.2 CSRF/XSS"
[WPP-3]: http://packetstormsecurity.com/files/129501/WordPress-WP-ViperGB-1.3.10-CSRF-XSS.html "PacketStorm: WordPress WP-ViperGB 1.3.10 CSRF / XSS"
[WPP-4]: http://packetstormsecurity.com/files/129503/WordPress-Simple-Sticky-Footer-1.3.2-CSRF-XSS.html "PacketStorm: WordPress Simple Sticky Footer 1.3.2 CSRF / XSS"
[WPP-5]: http://packetstormsecurity.com/files/129500/WordPress-IP-Ban-1.2.3-CSRF-XSS.html "PacketStorm: WordPress IP Ban 1.2.3 CSRF / XSS"
[WPP-6]: http://packetstormsecurity.com/files/129507/WordPress-Lightbox-Photo-Gallery-1.0-CSRF-XSS.html "PacketStorm: WordPress Lightbox Photo Gallery 1.0 CSRF / XSS"
[WPP-7]: http://packetstormsecurity.com/files/129499/WordPress-Our-Team-Showcase-1.2-CSRF-XSS.html "PacketStorm: WordPress Our Team Showcase 1.2 CSRF / XSS"
[WPP-8]: http://packetstormsecurity.com/files/129504/WordPress-Sliding-Recent-Posts-1.0-CSRF-XSS.html "PacketStorm: WordPress Sliding Recent Posts 1.0 CSRF / XSS"
[WPP-9]: http://packetstormsecurity.com/files/129509/WordPress-Sliding-Social-Icons-1.61-CSRF-XSS.html "PacketStorm: WordPress Sliding Social Icons 1.61 CSRF / XSS"
[WPP-10]: http://packetstormsecurity.com/files/129510/WordPress-Timed-Popup-1.3-CSRF-XSS.html "PacketStorm: WordPress Timed Popup 1.3 CSRF / XSS"
[WPP-11]: http://packetstormsecurity.com/files/129502/WordPress-Simple-Visitor-Stat-Cross-Site-Scripting.html "PacketStorm: WordPress Simple Visitor Stat Cross Site Scripting"
[WPP-12]: http://packetstormsecurity.com/files/129511/WordPress-WP-Construction-Mode-1.91-XSS.html "PacketStorm: WordPress WP Construction Mode 1.91 XSS"

[HumHub-1]: http://packetstormsecurity.com/files/128919/HumHub-Modules-Mail-0.5.8-Cross-Site-Scripting.html "PacketStorm: HumHub Modules Mail 0.5.8 Cross Site Scripting"