# Export html

### Style sheets

With the XML output, we can easily create HTML reports that are easy to read, even for non-technical people. This is later very useful for documentation, as it presents our results in a detailed and clear way. To convert the stored results from XML format to HTML, we can use the tool `xsltproc`.

XML Output

Sn0oker@htb\[/htb]$ xsltproc target.xml -o target.html

commande directe:

nmap 10.129.182.129 -oX target2 && xsltproc target2 -o target2.html
