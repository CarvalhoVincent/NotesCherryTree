# 🔷 Nessus



Pour démarrer le service Nessus:

```bash
sudo systemctl start nessusd.service
```



Puis pour accéder à la console&#x20;

{% embed url="https://localhost:8834" fullWidth="false" %}



{% tabs %}
{% tab title="Scan" %}
## Nessus Scan

***

A new Nessus scan can be configured by clicking `New Scan`, and selecting a scan type. Scan templates fall into three categories: `Discovery`, `Vulnerabilities`, and `Compliance`.

Note: The scans shown in this section have already been pre-run to save you the time of waiting for them to finish. If you re-run the scan, it's best to go through vulnerabilities as they come, instead of waiting for the scan to finish, as they can take 1-2 hours to finish.

***

### New Scan

Here we have options for a basic `Host Discovery` scan to identify live hosts/open ports or a variety of scan types such as the `Basic Network Scan`, `Advanced Scan`, `Malware Scan`, `Web Application Tests`, as well as scans targeted at specific CVEs and audit & compliance standards. A description of each scan type can be found [here](https://docs.tenable.com/nessus/Content/ScanAndPolicyTemplates.htm).

![image](https://academy.hackthebox.com/storage/modules/108/nessus/nessus\_scan\_types.png)

For the purposes of this exercise, we will choose the `Basic Network Scan` option, and we can enter our targets:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/general.png" alt=""><figcaption></figcaption></figure>

Note: For this module, the Windows target will be `172.16.16.100` and the Linux target will be `172.16.16.160`.

***

### Discovery

In the `Discovery` section, under `Host Discovery`, we're presented with the option to enable scanning for fragile devices. Scanning devices such as network printers often result in them printing out reams of paper with garbage text, leaving the devices unusable. We can leave this setting disabled:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/options.png" alt=""><figcaption></figcaption></figure>

In `Port Scanning`, we can choose whether to scan common ports, all ports, or a self-defined range, depending on our requirements:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/discovery.png" alt=""><figcaption></figcaption></figure>

Within the `Service Discovery` subsection, the `Probe all ports to find services` option is selected by default. It's possible that a poorly designed application or service could crash as a result of this probing, but most applications should be robust enough to handle this. Searching for SSL/TLS services is also enabled by default on a custom scan, and Nessus can additionally be instructed to identify expiring and revoked certificates.

***

### Assessment

Under the `Assessment` category, web application scanning can also be enabled if required, and a custom user agent and various other web application scanning options can be specified (e.g., a URL for Remote File Inclusion (RFI) testing):&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/webapp.png" alt=""><figcaption></figcaption></figure>

If desired, Nessus can attempt to authenticate against discovered applications and services using provided credentials (if running a credentialed scan), or else can perform a brute-force attack with the provided username and password lists:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/hydra.png" alt=""><figcaption></figcaption></figure>

User enumeration can also be performed using various techniques, such as RID Brute Forcing:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/userenum.png" alt=""><figcaption></figcaption></figure>

If we opt to perform RID Brute Forcing, we can set the starting and ending UIDs for both domain and local user accounts:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/ridbf.png" alt=""><figcaption></figcaption></figure>

***

### Advanced

On the `Advanced` tab, safe checks are enabled by default. This prevents Nessus from running checks that may negatively impact the target device or network. We can also choose to slow or throttle the scan if Nessus detects any network congestion, stop attempting to scan any hosts that become unresponsive, and even choose to have Nessus scan our target IP list in random order:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/advanced.png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Advanced settings" %}
## Advanced Settings

***

We can configure a number of advanced settings for Nessus and its scans, like scan policies, plugins, and credentials, all of which we will cover in this section.

***

### Scan Policies

Nessus gives us the option to create scan policies. Essentially these are customized scans that allow us to define specific scan options, save the policy configuration, and have them available to us under `Scan Templates` when creating a new scan. This gives us the ability to create targeted scans for any number of scenarios, such as a slower, more evasive scan, a web-focused scan, or a scan for a particular client using one or several sets of credentials. Scan policies can be imported from other Nessus scanners or exported to be later imported into another Nessus scanner.

![image](https://academy.hackthebox.com/storage/modules/108/nessus/nessus\_policies.png)

***

### Creating a Scan Policy

To create a scan policy, we can click on the `New Policy` button in the top right, and we will be presented with the list of pre-configured scans. We can choose a scan, such as the `Basic Network Scan`, then customize it, or we can create our own. We will choose `Advanced Scan` to create a fully customized scan with no pre-configured recommendations built-in.

After choosing the scan type as our base, we can give the scan policy a name and a description if needed:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/policy.png" alt=""><figcaption></figcaption></figure>

From here, we can configure settings, add in any necessary credentials, and specify any compliance standards to run the scan against. We can also choose to enable or disable entire [plugin](https://docs.tenable.com/nessus/Content/Plugins.htm) families or individual plugins.

Once we have finished customizing the scan, we can click on `Save`, and the newly created policy will appear in the polices list. From here on, when we go to create a new scan, there will be a new tab named `User Defined` under `Scan Templates` that will show all of our custom scan policies:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/htb_policydefined.png" alt=""><figcaption></figcaption></figure>

***

### Nessus Plugins

Nessus works with plugins written in the [Nessus Attack Scripting Language (NASL)](https://en.wikipedia.org/wiki/Nessus\_Attack\_Scripting\_Language) and can target new vulnerabilities and CVEs. These plugins contain information such as the vulnerability name, impact, remediation, and a way to test for the presence of a particular issue.

Plugins are rated by severity level: `Critical`, `High`, `Medium`, `Low`, `Info`. At the time of this writing Tenable has published `145,973` plugins that cover `58,391` CVE IDs and `30,696` [Bugtraq](https://en.wikipedia.org/wiki/Bugtraq) IDs. A searchable database of all published plugins is on the [Tenable website](https://www.tenable.com/plugins).

The `Plugins` tab provides more information on a particular detection, including mitigation. When conducting recurring scans, there may be a vulnerability/detection that, upon further examination, is not considered to be an issue. For example, Microsoft DirectAccess (a technology that provides internal network connectivity to clients over the Internet) allows insecure and null cipher suites. The below scan performed with `sslscan` shows an example of insecure and null cipher suites:

```shell-session
Sn0oker@htb[/htb]$ sslscan example.com

<SNIP>

Preferred TLSv1.0  128 bits  ECDHE-RSA-AES128-SHA          Curve 25519 DHE 253
Accepted  TLSv1.0  256 bits  ECDHE-RSA-AES256-SHA          Curve 25519 DHE 253
Accepted  TLSv1.0  128 bits  DHE-RSA-AES128-SHA            DHE 2048 bits
Accepted  TLSv1.0  256 bits  DHE-RSA-AES256-SHA            DHE 2048 bits
Accepted  TLSv1.0  128 bits  AES128-SHA                   
Accepted  TLSv1.0  256 bits  AES256-SHA                   

<SNIP>
```

However, this is by design. SSL/TLS is not [required](https://directaccess.richardhicks.com/2014/09/23/directaccess-ip-https-ssl-and-tls-insecure-cipher-suites/) in this case, and implementing it would result in a negative performance impact. To exclude this false positive from the scan results while keeping the detection active for other hosts, we can create a plugin rule:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/plugin_rules.png" alt=""><figcaption></figcaption></figure>

Under the `Resources` section, we can select `Plugin Rules`. In the new plugin rule, we input the host to be excluded, along with the Plugin ID for Microsoft DirectAccess, and specify the action to be performed as `Hide this result`:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/new-rule.png" alt=""><figcaption></figcaption></figure>

We may also want to exclude certain issues from our scan results, such as plugins for issues that are not directly exploitable (e.g., [SSL Self-Signed Certificate](https://www.tenable.com/plugins/nessus/57582)). We can do this by specifying the plugin ID and host(s) to be excluded:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/plugins2.png" alt=""><figcaption></figcaption></figure>

***

### Scanning with Credentials

Nessus also supports credentialed scanning and provides a lot of flexibility by supporting LM/NTLM hashes, Kerberos authentication, and password authentication.

Credentials can be configured for host-based authentication via SSH with a password, public key, certificate, or Kerberos-based authentication. It can also be configured for Windows host-based authentication with a password, Kerberos, LM hash, or NTLM hash:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/creds.png" alt=""><figcaption></figcaption></figure>

Nessus also supports authentication for a variety of databases types including Oracle, PostgreSQL, DB2, MySQL, SQL Server, MongoDB, and Sybase:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/db_creds.png" alt=""><figcaption></figcaption></figure>

Note: To run a credentialed scan on the target, use the following credentials: `htb-student_adm`:`HTB_@cademy_student!` for Linux, and `administrator`:`Academy_VA_adm1!` for Windows. These scans have already been set up in the Nessus target to save you time.

In addition to that, Nessus can perform plaintext authentication to services such as FTP, HTTP, IMAP, IPMI, Telnet, and more:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/plaintext_auth.png" alt=""><figcaption></figcaption></figure>

Finally, we can check the Nessus output to confirm whether the authentication to the target application or service with the supplied credentials was successful:&#x20;

<figure><img src="https://academy.hackthebox.com/storage/modules/108/nessus/sqlserv.png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Output" %}
## Working with Nessus Scan Output

***

Nessus gives us the option to export scan results in a variety of report formats as well as the option to export raw Nessus scan results to be imported into other tools, archived, or passed to tools, such as [EyeWitness](https://github.com/FortyNorthSecurity/EyeWitness), which can be used to take screenshots of all web applications identified by Nessus and greatly assist us with working through the results and finding more value in them.

***

### Nessus Reports

Once a scan is completed we can choose to export a report in `.pdf`, `.html`, or `.csv` formats. The .pdf and .html reports give the option for either an Executive Summary or a custom report. The Executive Summary report provides a listing of hosts, a total number of vulnerabilities discovered per host, and a `Show Details` option to see the severity, CVSS score, plugin number, and name of each discovered issue. The plugin number contains a link to the full plugin writeup from the Tenable plugin database. The PDF option provides the scan results in a format that is easier to share. The CSV report option allows us to select which columns we would like to export. This is particularly useful if importing the scan results into another tool such as Splunk if a document needs to be shared with many internal stakeholders responsible for remediation of the various assets scanned or to perform analytics on the scan data.

![image](https://academy.hackthebox.com/storage/modules/108/nessus/exportreport.png)

Note: These scan reports should only be shared as either an appendix or supplementary data to a custom penetration test/vulnerability assessment report. They should not be given to a client as the final deliverable for any assessment type.

An example of the HTML report is shown below:

![image](https://academy.hackthebox.com/storage/modules/108/nessus/htmlreport.png)

It is best to always make sure the vulnerabilities are grouped together for a clear understanding of each issue and the assets affected.

***

### Exporting Nessus Scans

Nessus also gives the option to export scans into two formats `Nessus (scan.nessus)` or `Nessus DB (scan.db)`. The `.nessus` file is an `.xml` file and includes a copy of the scan settings and plugin outputs. The `.db` file contains the `.nessus` file and the scan's KB, plugin Audit Trail, and any scan attachments. More information about the `KB` and `Audit Trail` can be found [here](https://community.tenable.com/s/article/What-is-included-in-a-nessus-db-file).

Scripts such as the [nessus-report-downloader](https://raw.githubusercontent.com/eelsivart/nessus-report-downloader/master/nessus6-report-downloader.rb) can be used to quickly download scan results in all available formats from the CLI using the Nessus REST API:

```shell-session
Sn0oker@htb[/htb]$ ./nessus_downloader.rb 

Nessus 6 Report Downloader 1.0

Enter the Nessus Server IP: 127.0.0.1
Enter the Nessus Server Port [8834]: 8834
Enter your Nessus Username: admin
Enter your Nessus Password (will not echo): 

Getting report list...
Scan ID Name                                               Last Modified                  Status         
------- ----                                               -------------                  ------         
1     Windows_basic                                Aug 22, 2020 22:07 +00:00      completed      
         
Enter the report(s) your want to download (comma separate list) or 'all': 1

Choose File Type(s) to Download: 
[0] Nessus (No chapter selection)
[1] HTML
[2] PDF
[3] CSV (No chapter selection)
[4] DB (No chapter selection)
Enter the file type(s) you want to download (comma separate list) or 'all': 3

Path to save reports to (without trailing slash): /assessment_data/inlanefreight/scans/nessus

Downloading report(s). Please wait...

[+] Exporting scan report, scan id: 1, type: csv
[+] Checking export status...
[+] Report ready for download...
[+] Downloading report to: /assessment_data/inlanefreight/scans/nessus/inlanefreight_basic_5y3hxp.csv

Report Download Completed!
```

We can also write our own scripts to automate many Nessus feature
{% endtab %}
{% endtabs %}

