# Values for Geolocation Resource Record Sets<a name="resource-record-sets-values-geo"></a>

When you create geolocation resource record sets, you specify the following values:

**Note**  
Creating geolocation resource record sets in private hosted zones is not supported\.


+ [Name](#rrsets-values-geo-name)
+ [Type](#rrsets-values-geo-type)
+ [Alias](#rrsets-values-geo-alias)
+ [TTL \(Time to Live\)](#rrsets-values-geo-ttl)
+ [Value](#rrsets-values-geo-value)
+ [Routing Policy](#rrsets-values-geo-routing-policy)
+ [Location](#rrsets-values-geo-location)
+ [Sublocation](#rrsets-values-geo-sublocation)
+ [Set ID](#rrsets-values-geo-set-id)
+ [Associate with Health Check/Health Check to Associate](#rrsets-values-geo-associate-with-health-check)

## Name<a name="rrsets-values-geo-name"></a>

Enter the name of the domain or subdomain that you want to route traffic for\. The default value is the name of the hosted zone\. 

**Note**  
If you're creating a resource record set that has the same name as the hosted zone, don't enter a value \(for example, an @ symbol\) in the **Name** field\. 

Enter the same name for all of the resource record sets in the group of geolocation resource record sets\. 

**CNAME resource record sets**  
If you're creating a resource record set that has a value of **CNAME** for **Type**, the name of the resource record set can't be the same as the name of the hosted zone\.

**Special characters**  
For information about how to specify characters other than a\-z, 0\-9, and \- \(hyphen\) and how to specify internationalized domain names, see [DNS Domain Name Format](DomainNameFormat.md)\.

**Wildcard characters**  
You can use an asterisk \(\*\) character in the name\. DNS treats the \* character either as a wildcard or as the \* character \(ASCII 42\), depending on where it appears in the name\. For more information, see [Using an Asterisk \(\*\) in the Names of Hosted Zones and Resource Record Sets](DomainNameFormat.md#domain-name-format-asterisk)\.

## Type<a name="rrsets-values-geo-type"></a>

The DNS record type\. For more information, see [Supported DNS Record Types](ResourceRecordTypes.md)\.

Select the same value for all of the resource record sets in the group of geolocation resource record sets\.

## Alias<a name="rrsets-values-geo-alias"></a>

Select **No**\. 

## TTL \(Time to Live\)<a name="rrsets-values-geo-ttl"></a>

The amount of time, in seconds, that you want DNS recursive resolvers to cache information about this resource record set\. If you specify a longer value \(for example, 172800 seconds, or two days\), you pay less for Amazon Route 53 service because recursive resolvers send requests to Amazon Route 53 less often\. However, it takes longer for changes to the resource record set \(for example, a new IP address\) to take effect because recursive resolvers use the values in their cache for longer periods instead of asking Amazon Route 53 for the latest information\. 

If you're associating this resource record set with a health check, we recommend that you specify a TTL of 60 seconds or less so clients respond quickly to changes in health status\.

## Value<a name="rrsets-values-geo-value"></a>

Enter a value that is appropriate for the value of **Type**\. For all types except **CNAME**, you can enter more than one value\. Enter each value on a separate line\.

**A — IPv4 address**  
An IP address in IPv4 format, for example, **192\.0\.2\.235**\.

**AAAA — IPv6 address**  
An IP address in IPv6 format, for example, **2001:0db8:85a3:0:0:8a2e:0370:7334**\.

**CAA — Certificate Authority Authorization**  
Three space\-separated values that control which certificate authorities are allowed to issue certificates or wildcard certificates for the domain or subdomain that is specified by **Name**\. You can use CAA records to specify the following:  

+ Which certificate authorities \(CAs\) can issue SSL/TLS certificates, if any

+ The email address or URL to contact when a CA issues a certificate for the domain or subdomain

**CNAME — Canonical name**  
The fully qualified domain name \(for example, *www\.example\.com*\) that you want Amazon Route 53 to return in response to DNS queries for this resource record set\. A trailing dot is optional; Amazon Route 53 assumes that the domain name is fully qualified\. This means that Amazon Route 53 treats *www\.example\.com* \(without a trailing dot\) and *www\.example\.com\.* \(with a trailing dot\) as identical\.

**MX — Mail exchange**  
A priority and a domain name that specifies a mail server, for example, **10 mailserver\.example\.com**\.

**NAPTR — Name Authority Pointer**  
Six space\-separated settings that are used by Dynamic Delegation Discovery System \(DDDS\) applications to convert one value to another or to replace one value with another\. For more information, see [NAPTR Format](ResourceRecordTypes.md#NAPTRFormat)\.

**PTR — Pointer**  
The domain name that you want Amazon Route 53 to return\.

**SPF — Sender Policy Framework**  
An SPF record enclosed in quotation marks, for example, **"v=spf1 ip4:192\.168\.0\.1/16\-all"**\. SPF records are not recommended\. For more information, see [Supported DNS Record Types](ResourceRecordTypes.md)\.

**SRV — Service locator**  
An SRV record\. For information about SRV record format, refer to the applicable documentation\. The format of an SRV record is:  
**\[priority\] \[weight\] \[port\] \[server host name\]**  
For example:  
**1 10 5269 xmpp\-server\.example\.com\.**

**TXT — Text**  
A text record\. Enclose text in quotation marks, for example, **"Sample Text Entry"**\. 

## Routing Policy<a name="rrsets-values-geo-routing-policy"></a>

Select **Geolocation**\. 

## Location<a name="rrsets-values-geo-location"></a>

When you configure Amazon Route 53 to respond to DNS queries based on the location that the queries originated from, select the continent or country for which you want Amazon Route 53 to respond with the settings in this resource record set\. If you want Amazon Route 53 to respond to DNS queries for individual states in the United States, select **United States** from the **Location** list, and then select the state from the **Sublocation** list\.

**Important**  
We recommend that you create one geolocation resource record set that has a value of **Default** for **Location**\. This covers geographic locations that you haven't created resource record sets for and IP addresses that Amazon Route 53 can't identify a location for\.

You can't create non\-geolocation resource record sets that have the same values for **Name** and **Type** as geolocation resource record sets\.

For more information, see [Geolocation Routing](routing-policy.md#routing-policy-geo)\.

Here are the countries that Amazon Route 53 associates with each continent\. The country codes are from ISO 3166\. For more information, see the Wikipedia article [ISO 3166\-1 alpha\-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2):

**Africa \(AF\)**  
AO, BF, BI, BJ, BW, CD, CF, CG, CI, CM, CV, DJ, DZ, EG, ER, ET, GA, GH, GM, GN, GQ, GW, KE, KM, LR, LS, LY, MA, MG, ML, MR, MU, MW, MZ, NA, NE, NG, RE, RW, SC, SD, SH, SL, SN, SO, SS, ST, SZ, TD, TG, TN, TZ, UG, YT, ZA, ZM, ZW

**Antarctica \(AN\)**  
AQ, GS, TF

**Asia \(AS\)**  
AE, AF, AM, AZ, BD, BH, BN, BT, CC, CN, GE, HK, ID, IL, IN, IO, IQ, IR, JO, JP, KG, KH, KP, KR, KW, KZ, LA, LB, LK, MM, MN, MO, MV, MY, NP, OM, PH, PK, PS, QA, SA, SG, SY, TH, TJ, TM, TR, TW, UZ, VN, YE

**Europe \(EU\)**  
AD, AL, AT, AX, BA, BE, BG, BY, CH, CY, CZ, DE, DK, EE, ES, FI, FO, FR, GB, GG, GI, GR, HR, HU, IE, IM, IS, IT, JE, LI, LT, LU, LV, MC, MD, ME, MK, MT, NL, NO, PL, PT, RO, RS, RU, SE, SI, SJ, SK, SM, UA, VA, XK

**North America \(NA\)**  
AG, AI, AW, BB, BL, BM, BQ, BS, BZ, CA, CR, CU, CW, DM, DO, GD, GL, GP, GT, HN, HT, JM, KN, KY, LC, MF, MQ, MS, MX, NI, PA, PM, PR, SV, SX, TC, TT, US, VC, VG, VI

**Oceania \(OC\)**  
AS, AU, CK, FJ, FM, GU, KI, MH, MP, NC, NF, NR, NU, NZ, PF, PG, PN, PW, SB, TK, TL, TO, TV, UM, VU, WF, WS

**South America \(SA\)**  
AR, BO, BR, CL, CO, EC, FK, GF, GY, PE, PY, SR, UY, VE

**Note**  
Amazon Route 53 doesn't support creating geolocation resource record sets for the following countries: Bouvet Island \(BV\), Christmas Island \(CX\), Western Sahara \(EH\), and Heard Island and McDonald Islands \(HM\)\. No data is available about IP addresses for these countries\.

## Sublocation<a name="rrsets-values-geo-sublocation"></a>

When you configure Amazon Route 53 to respond to DNS queries based on the state of the United States that the queries originated from, select the state from the **Sublocations** list\. United States territories \(for example, Puerto Rico\) are listed as countries in the **Location** list\.

**Important**  
Some IP addresses are associated with the United States, but not with an individual state\. If you create resource record sets for all of the states in the United States, we recommend that you also create a resource record set for the United States to route queries for these unassociated IP addresses\. If you don't create a resource record set for the United States, Amazon Route 53 responds to DNS queries from unassociated United States IP addresses with settings from the default geolocation resource record set \(if you created one\) or with a "no answer" response\. 

## Set ID<a name="rrsets-values-geo-set-id"></a>

Enter a value that uniquely identifies this resource record set in the group of geolocation resource record sets\.

## Associate with Health Check/Health Check to Associate<a name="rrsets-values-geo-associate-with-health-check"></a>

Select **Yes** if you want Amazon Route 53 to check the health of a specified endpoint and to respond to DNS queries using this resource record set only when the endpoint is healthy\. Then select the health check that you want Amazon Route 53 to perform for this resource record set\. 

Amazon Route 53 doesn't check the health of the endpoint specified in the resource record set, for example, the endpoint specified by the IP address in the **Value** field\. When you select a health check for a resource record set, Amazon Route 53 checks the health of the endpoint that you specified in the health check\. For information about how Amazon Route 53 determines whether an endpoint is healthy, see [How Amazon Route 53 Determines Whether an Endpoint Is Healthy](dns-failover-determining-health-of-endpoints.md)\.

Associating a health check with a resource record set is useful only when Amazon Route 53 is choosing between two or more resource record sets to respond to a DNS query, and you want Amazon Route 53 to base the choice in part on the status of a health check\. Use health checks only in the following configurations:

+ You're checking the health of all of the resource record sets in a group of failover, geolocation, latency, multivalue, or weighted resource record sets, and you specify health check IDs for all the resource record sets\. If the health check for a resource record set specifies an endpoint that is not healthy, Amazon Route 53 stops responding to queries using the value for that resource record set\.

+ You select **Yes** for **Evaluate Target Health** for an alias resource record set or the resource record sets in a group of failover alias, geolocation alias, latency alias, or weighted alias resource record set\. If the alias resource record sets reference non\-alias resource record sets in the same hosted zone, you must also specify health checks for the referenced resource record sets\. 

For geolocation resource record sets, if an endpoint is unhealthy, Amazon Route 53 looks for a resource record set for the larger, associated geographic region\. For example, suppose you have resource record sets for a state in the United States, for the United States, for North America, and for all locations \(**Location** is **Default**\)\. If the endpoint for the state resource record set is unhealthy, Amazon Route 53 checks the resource record sets for the United States, for North America, and for all locations, in that order, until it finds a resource record set that has a healthy endpoint\.

If your health checks specify the endpoint only by domain name, we recommend that you create a separate health check for each endpoint\. For example, create a health check for each HTTP server that is serving content for www\.example\.com\. For the value of **Domain Name**, specify the domain name of the server \(such as us\-east\-2\-www\.example\.com\), not the name of the resource record sets \(example\.com\)\.

**Important**  
In this configuration, if you create a health check for which the value of **Domain Name** matches the name of the resource record sets and then associate the health check with those resource record sets, health check results will be unpredictable\.

For more information about checking the health of endpoints, see [Creating Amazon Route 53 Health Checks and Configuring DNS Failover](dns-failover.md)\.