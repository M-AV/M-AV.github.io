<div class='post_title_wrapper'> 
	<h1 class='post_title'>Security advisories </h1>
</div>
In the fall 2014, I started (as part of my Master's thesis) to look into web security and common vulnerabilities. Here is a list of all vulnerabilities found since then where I can claim at least some of the credit. 

# WordPress plugins
|  Name                             | Version  | Vulnerability     | Published  |
| :------------------------------:  | :------: | :---------------: | :--------: |
| [WP Accurate Form Data][WPP-38]   | 1.2      | XSS               | 2015-07-31 |
| [Ninja Forms][WPP-37]             | 2.9.21   | XSS               | 2015-07-30 |
| [Altos Connect Widget][WPP-36]    | 1.3.0    | XSS               | 2015-07-30 |
| [Database Sync][WPP-35]           | 0.4      | XSS               | 2015-07-30 |
| [Admin Pack by SITE CAS..][WPP-34]| 1.1      | XSS               | 2015-07-30 |
| [Customize Youtube Videos][WPP-33]| 0.2      | XSS               | 2015-07-30 |
| [Copy or Move Comments][WPP-32]   | 1.0.0    | XSS               | 2015-07-30 |
| [Advertisement Management][WPP-31]| 1.0      | XSS               | 2015-07-30 |
| [arcResBookingWidget][WPP-30]     | 1.0      | XSS & CSRF        | 2015-07-30 |
| [Content Grabber][WPP-29]         | 1.0      | XSS               | 2015-07-30 |
| [Default Facebook Thum..][WPP-28] | 0.4      | XSS               | 2015-07-30 |
| [Chief Editor][WPP-27]            | 3.6.1    | XSS               | 2015-07-29 |
| [1-click Retweet/Share..][WPP-26] | 5.2      | XSS               | 2015-07-29 |
| [Author Manager][WPP-25]          | 1.0      | XSS               | 2015-07-29 |
| [Ads in bottom right][WPP-24]     | 1.0      | XSS               | 2015-07-29 |
| [Google 'Plus one' ..][WPP-23]    | 1.5.0    | XSS & CSRF        | 2015-07-29 |
| [Advance Categorizer][WPP-22]     | 0.3      | XSS & CSRF        | 2015-07-28 |
| [F/T/G Social Widgets][WPP-21]    | 1.3.7    | XSS & CSRF        | 2015-07-28 |
| [Contact Form DB][WPP-20]         | 2.8.26   | XSS               | 2015-02-09 |
| [Cart66 Lite][WPP-19]             | 1.5.4    | XSS               | 2015-02-09 |
| [Acobot Live Chat..][WPP-18]      | 2.0      | XSS & CSRF        | 2015-02-09 |
| [Google Doc Embedder][WPP-17]     | 2.5.18   | XSS               | 2015-02-09 |
| [Redirection Page][WPP-16]        | 1.2      | XSS & CSRF        | 2015-02-09 |
| [Spider Facebook][WPP-15]         | 1.0.10   | XSS               | 2015-02-09 |
| [Cross Slide][WPP-14]             | 2.0.5    | XSS & CSRF        | 2015-02-09 |
| [Mobile Domain][WPP-13]           | 1.5.2    | Stored XSS & CSRF | 2015-02-09 |
| [WP Constuction Mode][WPP-12]     | 1.91     | Reflected XSS     | 2014-12-12 |
| [Simple Visitor Stat][WPP-11]     | 1.0      | Stored XSS        | 2014-12-12 |
| [Timed Popup][WPP-10]             | 1.3      | Stored XSS & CSRF | 2014-12-12 |
| [Sliding Social Icons][WPP-9]     | 1.61     | Stored XSS & CSRF | 2014-12-12 |
| [Sliding Recent Posts][WPP-8]     | 1.0.0    | Stored XSS & CSRF | 2014-12-12 |
| [Our Team Showcase][WPP-7]        | 1.2      | Stored XSS & CSRF | 2014-12-12 |
| [Lightbox Photo Gallery][WPP-6]   | 1.0      | Stored XSS & CSRF | 2014-12-12 |
| [IP Ban][WPP-5]                   | 1.2.3    | Stored XSS & CSRF | 2014-12-12 |
| [Simple Sticky Footer][WPP-4]     | 1.3.2    | Stored XSS & CSRF | 2014-12-12 |
| [WP-ViperGB][WPP-3]               | 1.3.10   | Stored XSS & CSRF | 2014-12-12 |
| [Facebook Like Box][WPP-2]        | 2.8.2    | Stored XSS & CSRF | 2014-12-12 |
| [WP-FB Autoconnect][WPP-1]        | 4.0.5    | Stored XSS & CSRF | 2014-12-12 |
<br />  

# Other vulnerabilities

|      Name                      |     Version       | Vulnerability | Published  |
| :----------------------------: |:-----------------:| :------------:| :--------: |
| [HumHub Mail Module][HumHub-1] | 0.5.8             | Reflected XSS | 2014-10-31 |


[WPP-1]: https://packetstormsecurity.com/files/129508/WordPress-WP-FB-AutoConnect-4.0.5-CSRF-XSS.html "Packet Storm: WordPress WP-FB-AutoConnect 4.0.5 CSRF/XSS"
[WPP-2]: https://packetstormsecurity.com/files/129506/WordPress-Facebook-Like-Box-2.8.2-CSRF-XSS.html "Packet Storm: WordPress Facebook Like Box 2.8.2 CSRF/XSS"
[WPP-3]: https://packetstormsecurity.com/files/129501/WordPress-WP-ViperGB-1.3.10-CSRF-XSS.html "Packet Storm: WordPress WP-ViperGB 1.3.10 CSRF / XSS"
[WPP-4]: https://packetstormsecurity.com/files/129503/WordPress-Simple-Sticky-Footer-1.3.2-CSRF-XSS.html "Packet Storm: WordPress Simple Sticky Footer 1.3.2 CSRF / XSS"
[WPP-5]: https://packetstormsecurity.com/files/129500/WordPress-IP-Ban-1.2.3-CSRF-XSS.html "Packet Storm: WordPress IP Ban 1.2.3 CSRF / XSS"
[WPP-6]: https://packetstormsecurity.com/files/129507/WordPress-Lightbox-Photo-Gallery-1.0-CSRF-XSS.html "Packet Storm: WordPress Lightbox Photo Gallery 1.0 CSRF / XSS"
[WPP-7]: https://packetstormsecurity.com/files/129499/WordPress-Our-Team-Showcase-1.2-CSRF-XSS.html "Packet Storm: WordPress Our Team Showcase 1.2 CSRF / XSS"
[WPP-8]: https://packetstormsecurity.com/files/129504/WordPress-Sliding-Recent-Posts-1.0-CSRF-XSS.html "Packet Storm: WordPress Sliding Recent Posts 1.0 CSRF / XSS"
[WPP-9]: https://packetstormsecurity.com/files/129509/WordPress-Sliding-Social-Icons-1.61-CSRF-XSS.html "Packet Storm: WordPress Sliding Social Icons 1.61 CSRF / XSS"
[WPP-10]: https://packetstormsecurity.com/files/129510/WordPress-Timed-Popup-1.3-CSRF-XSS.html "Packet Storm: WordPress Timed Popup 1.3 CSRF / XSS"
[WPP-11]: https://packetstormsecurity.com/files/129502/WordPress-Simple-Visitor-Stat-Cross-Site-Scripting.html "Packet Storm: WordPress Simple Visitor Stat Cross Site Scripting"
[WPP-12]: https://packetstormsecurity.com/files/129511/WordPress-WP-Construction-Mode-1.91-XSS.html "Packet Storm: WordPress WP Construction Mode 1.91 XSS"
[WPP-13]: https://packetstormsecurity.com/files/130316/WordPress-Mobile-Domain-1.5.2-Cross-Site-Request-Forgery-Cross-Site-Scripting.html "Packet Storm: WordPress Mobile Domain 1.5.2 Cross Site Request Forgery / Cross Site Scripting"
[WPP-14]: https://packetstormsecurity.com/files/130313/WordPress-Cross-Slide-2.0.5-Cross-Site-Request-Forgery-Cross-Site-Scripting.html "Packet Storm: WordPress Cross Slide 2.0.5 Cross Site Request Forgery / Cross Site Scripting"
[WPP-15]: https://packetstormsecurity.com/files/130318/WordPress-Spider-Facebook-1.0.10-Cross-Site-Scripting.html "Packet Storm: WordPress Spider Facebook 1.0.10 Cross Site Scripting"
[WPP-16]: https://packetstormsecurity.com/files/130314/WordPress-Redirection-Page-1.2-CSRF-XSS.html "Packet Storm: WordPress Redirection Page 1.2 CSRF / XSS"
[WPP-17]: https://packetstormsecurity.com/files/130309/WordPress-Google-Doc-Embedder-2.5.18-Cross-Site-Scripting.html "Packet Storm: WordPress Google Doc Embedder 2.5.18 Cross Site Scripting"
[WPP-18]: https://packetstormsecurity.com/files/130306/WordPress-Acobot-Live-Chat-And-Contact-Form-2.0-CSRF-XSS.html "Packet Storm: WordPress Acobot Live Chat And Contact Form 2.0 CSRF / XSS"
[WPP-19]: https://packetstormsecurity.com/files/130307/WordPress-Cart66-Lite-1.5.4-Cross-Site-Scripting.html "Packet Storm: WordPress Cart66 Lite 1.5.4 Cross Site Scripting"
[WPP-20]: https://packetstormsecurity.com/files/130311/WordPress-Contact-Form-DB-2.8.26-Cross-Site-Scripting.html "Packet Storm: WordPress Contact Form DB 2.8.26 Cross Site Scripting"
[WPP-21]: https://packetstormsecurity.com/files/132878/WordPress-F-T-G-Social-Widgets-1.3.7-Cross-Site-Scripting.html "Packet Storm: WordPress F/T/G Social Widgets 1.3.7 Cross Site Scripting"
[WPP-22]: https://packetstormsecurity.com/files/132877/WordPress-Advance-Categorizer-0.3-Cross-Site-Scripting.html "Packet Storm: WordPress Advance Categorizer 0.3 Cross Site Scripting"
[WPP-23]: https://packetstormsecurity.com/files/132880/WordPress-Google-Plus-One-Button-By-KMS-1.5.0-CSRF-XSS.html "WordPress Google Plus One Button By KMS 1.5.0 CSRF / XSS"
[WPP-24]: https://packetstormsecurity.com/files/132883/WordPress-Ads-In-Bottom-Right-1.0-Cross-Site-Scripting.html "Packet Storm: WordPress Ads In Bottom Right 1.0 Cross Site Scripting"
[WPP-25]: https://packetstormsecurity.com/files/132881/WordPress-Author-Manager-1.0-Cross-Site-Scripting.html "Packet Storm: WordPress Author Manager 1.0 Cross Site Scripting"
[WPP-26]: https://packetstormsecurity.com/files/132882/WordPress-1-Click-Retweet-Share-Like-5.2-Cross-Site-Scripting.html "Packet Storm: WordPress 1-Click Retweet/Share/Like 5.2 Cross Site Scripting"
[WPP-27]: https://packetstormsecurity.com/files/132879/WordPress-Chief-Editor-3.6.1-Cross-Site-Scripting.html "Packet Storm: WordPress Chief Editor 3.6.1 Cross Site Scripting"
[WPP-28]: https://packetstormsecurity.com/files/132912/WordPress-Default-Facebook-Thumbnails-0.4-Cross-Site-Scripting.html "Packet Storm: WordPress Default Facebook Thumbnails 0.4 Cross Site Scripting"
[WPP-29]: https://packetstormsecurity.com/files/132910/WordPress-Content-Grabber-1.0-Cross-Site-Scripting.html "Packet Storm: WordPress Content Grabber 1.0 Cross Site Scripting"
[WPP-30]: https://packetstormsecurity.com/files/132914/WordPress-arcResBookingWidget-1.0-Cross-Site-Scripting.html "Packet Storm: WordPress arcResBookingWidget 1.0 Cross Site Scripting"
[WPP-31]: https://packetstormsecurity.com/files/132886/WordPress-Advertisement-Management-1.0-Cross-Site-Scripting.html "Packet Storm: WordPress Advertisement Management 1.0 Cross Site Scripting"
[WPP-32]: https://packetstormsecurity.com/files/132905/WordPress-Copy-Or-Move-Comments-1.0.0-Cross-Site-Scripting.html "Packet Storm: WordPress Copy Or Move Comments 1.0.0 Cross Site Scripting"
[WPP-33]: https://packetstormsecurity.com/files/132906/WordPress-Customize-Youtube-Videos-0.2-Cross-Site-Scripting.html "Packet Storm: WordPress Customize Youtube Videos 0.2 Cross Site Scripting"
[WPP-34]: https://packetstormsecurity.com/files/132909/WordPress-Admin-Pack-By-Site-Caseiro-1.1-Cross-Site-Scripting.html "Packet Storm: WordPress Admin Pack By Site Caseiro 1.1 Cross Site Scripting"
[WPP-35]: https://packetstormsecurity.com/files/132907/WordPress-Database-Sync-0.4-Cross-Site-Scripting.html "Packet Storm: WordPress Database Sync 0.4 Cross Site Scripting"
[WPP-36]: https://packetstormsecurity.com/files/132908/WordPress-Altos-Connect-Widget-1.3.0-Cross-Site-Scripting.html "Packet Storm: WordPress Altos Connect Widget 1.3.0 Cross Site Scripting"
[WPP-37]: https://packetstormsecurity.com/files/132913/WordPress-Ninja-Forms-2.9.21-Cross-Site-Scripting.html "Packet Storm: WordPress Ninja Forms 2.9.21 Cross Site Scripting"
[WPP-38]: https://packetstormsecurity.com/files/132911/WordPress-WP-Accurate-Form-Data-1.2-XSS-CSRF.html "Packet Storm: WordPress WP Accurate Form Data 1.2 XSS / CSRF"

[HumHub-1]: https://packetstormsecurity.com/files/128919/HumHub-Modules-Mail-0.5.8-Cross-Site-Scripting.html "Packet Storm: HumHub Modules Mail 0.5.8 Cross Site Scripting"