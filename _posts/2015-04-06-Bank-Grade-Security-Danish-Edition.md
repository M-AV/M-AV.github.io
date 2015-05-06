---
layout: post
title: Bank Grade Security - Danish bank edition
date: 2015-04-06
comments: true
tags: [Security, SSL]
category: 
---

A few days ago, Troy Hunt published a [blog post][TroyHunt] about various banks and their SSL. Using SSL Labs' [SSL Server Test][SSLLabs], he scanned a bunch of Australian banks' websites and summarized the results. Interestingly, very few banks achieved "all green". Most banks lack support for Forward Secrecy and many also still support the RC4 cipher suite. A few were even vulnerable to the [POODLE][WikiPoodle] vulnerability. These results made me curious about how the Danish banks compare. 

I threw a bunch of Danish bank URLs through the SSL Server Test and the results can be seen in the table below. It should be noted that I have taken the URL to the page displaying the [NemID][NemId] login form (a common login platform used by all Danish banks).

<table><thead>
<tr>
<th style="text-align: center">Bank</th>
<th style="text-align: center">Grade</th>
<th style="text-align: center">Supports SSL 3</th>
<th style="text-align: center">Supports SHA1</th>
<th style="text-align: center">No TLS 1.2</th>
<th style="text-align: center">Supports RC4</th>
<th style="text-align: center">Forward Secrecy</th>
<th style="text-align: center">POODLE</th>
</tr>
</thead><tbody>
<tr>
<td style="text-align: center; background-color:lawngreen"><a href="https://www.ssllabs.com/ssltest/analyze.html?d=https%3A%2F%2Fwww.danskebank.dk" title="SSLLabs - www.danskebank.dk">Danske Bank</a></td>
<td style="text-align: center; background-color:lawngreen"><strong>A-</strong></td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
</tr>
<tr>
<td style="text-align: center; background-color:orange"><a href="https://www.ssllabs.com/ssltest/analyze.html?d=vestjyskbank.dk" title="SSLLabs - Vestjyskbank.dk">Vestjysk Bank</a></td>
<td style="text-align: center; background-color:orange"><strong>B</strong></td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
</tr>
<tr>
<td style="text-align: center; background-color:orange"><a href="https://www.ssllabs.com/ssltest/analyze.html?d=https%3A%2F%2Fnetbank.sparnord.dk" title="SSLLabs - netbank.sparnord.dk">Spar Nord</a></td>
<td style="text-align: center; background-color:orange"><strong>B</strong></td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:green; color:white">Pass*</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
</tr>
<tr>
<td style="text-align: center; background-color:orange"><a href="https://www.ssllabs.com/ssltest/analyze.html?d=https%3A%2F%2Fjutlander-netbank.dk" title="SSLLabs - jutlander-netbank.dk">Jutlander Bank</a></td>
<td style="text-align: center; background-color:orange"><strong>B</strong></td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
</tr>
<tr>
<td style="text-align: center; background-color:orange"><a href="https://www.ssllabs.com/ssltest/analyze.html?d=www.himmerland.dk" title="SSLLabs - www.himmerland.dk">Himmerland.dk</a></td>
<td style="text-align: center; background-color:orange"><strong>B</strong></td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
</tr>
<tr>
<td style="text-align: center; background-color:orange"><a href="https://www.ssllabs.com/ssltest/analyze.html?d=al-bank.dk" title="SSLLabs - al-bank.dk">Arbejdernes Landsbank</a></td>
<td style="text-align: center; background-color:orange"><strong>B</strong></td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
</tr>
<tr>
<td style="text-align: center; background-color:orange"><a href="https://www.ssllabs.com/ssltest/analyze.html?d=lsb.dk" title="SSLLabs - lsb.dk">Lån &amp; Spar Bank</a></td>
<td style="text-align: center; background-color:orange;"><strong>B</strong></td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
</tr>
<tr>
<td style="text-align: center; background-color:red"><a href="https://www.ssllabs.com/ssltest/analyze.html?d=portal4.sydbank.dk" title="SSLLabs - portal4.sydbank.dk">Sydbank</a></td>
<td style="text-align: center; background-color:red;"><strong>F</strong></td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
</tr>
<tr>
<td style="text-align: center; background-color:red"><a href="https://www.ssllabs.com/ssltest/analyze.html?d=portal4.nrsbank.dk" title="SSLLabs - portal4.nrsbank.dk">Nordjyske Bank</a></td>
<td style="text-align: center; background-color:red;"><strong>F</strong></td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
</tr>
<tr>
<td style="text-align: center; background-color:red"><a href="https://www.ssllabs.com/ssltest/analyze.html?d=portal.bankdata.dk" title="SSLLabs - portal.bankdata.dk">Finansbanken</a></td>
<td style="text-align: center; background-color:red;"><strong>F</strong></td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:green; color:white">Pass</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
<td style="text-align: center; background-color:red; color:white">Fail</td>
</tr>
</tbody></table>

- *Intermediate certificate still supports SHA1  


Himmerland is actually the "old name" for Jutlander Bank, but it seems like it is [still possible][Himmerland-login] to login to their online banking site from the old domain.

These results seem to be consistent with the Aussie banks in Troy Hunt's post. 

Other people had the same thought as I did after reading Troy's post. Here is a list of posts with results from other countries (found in the comments to Troy's post):

*UK banks*: [Wilka Hudson's blog][MagneticMonkey] <br />
*South African banks*: [Ian Gilfillian's blog][IanG] <br />
*Czech Republic banks*: [Google Docs document][GDocs] <br />


<!-- Bibliography -->

[TroyHunt]: http://www.troyhunt.com/2015/05/do-you-really-want-bank-grade-security.html "TroyHunt.com - Do you really want “bank grade” security in your SSL? Here’s how Aussie banks fare"
[SSLLabs]: https://www.ssllabs.com/ssltest/ "Qualys SSL LABS - SSL Server Test"
[WikiPoodle]: https://en.wikipedia.org/wiki/POODLE "Wikipedia - POODLE"
[NemId]: https://en.wikipedia.org/wiki/NemID "Wikipedia - NemID"
[Himmerland-login]: https://www.himmerland.dk/netbank/adgang/logondanid/logondanid_bred/ "www.himmerland.dk - Jutlander/Himmerland NemID login page"
[MagneticMonkey]: http://blog.wilka.co.uk/2015/05/06/uk-bank-ssl/ "Magnetic Monkey - UK 'Bank Grade' SSL"
[IanG]: http://www.greenman.co.za/blog/?p=1734 "Neverness - South African Banks SSL Security"
[GDocs]: https://docs.google.com/spreadsheets/d/1LI1Pk0IwAvD9FE4ShHIU8ajT_NvEtGxO0VFW4OR78TY/edit#gid=0 "Banks & HTTPS in the Czech Republic"

[VB]: https://www.ssllabs.com/ssltest/analyze.html?d=vestjyskbank.dk "SSLLabs - Vestjyskbank.dk"
[DB]: https://www.ssllabs.com/ssltest/analyze.html?d=https%3A%2F%2Fwww.danskebank.dk "SSLLabs - www.danskebank.dk"
[SN]: https://www.ssllabs.com/ssltest/analyze.html?d=https%3A%2F%2Fnetbank.sparnord.dk "SSLLabs - netbank.sparnord.dk"
[JB]: https://www.ssllabs.com/ssltest/analyze.html?d=https%3A%2F%2Fjutlander-netbank.dk "SSLLabs - jutlander-netbank.dk"
[H]: https://www.ssllabs.com/ssltest/analyze.html?d=www.himmerland.dk "SSLLabs - www.himmerland.dk"
[AL]: https://www.ssllabs.com/ssltest/analyze.html?d=al-bank.dk "SSLLabs - al-bank.dk"
[S]: https://www.ssllabs.com/ssltest/analyze.html?d=portal4.sydbank.dk "SSLLabs - portal4.sydbank.dk"
[NB]: https://www.ssllabs.com/ssltest/analyze.html?d=portal4.nrsbank.dk "SSLLabs - portal4.nrsbank.dk"
[F]: https://www.ssllabs.com/ssltest/analyze.html?d=portal.bankdata.dk "SSLLabs - portal.bankdata.dk"
[LSB]: https://www.ssllabs.com/ssltest/analyze.html?d=lsb.dk "SSLLabs - lsb.dk"