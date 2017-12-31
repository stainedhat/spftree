# SPFTree
Parses an SPF record and displays the includes and all IP addresses nested in the record as well as some stats


# Using SPFTree
####### Create an instance of SPFTree #######

spf = SPFTree()

####### Parse the domain #######

spf.parse_spf("google.com")

####### Print the nested list to the console #######

spf.print_spf_tree()

####### Output #######
<pre>
######## SPF Lookup Tree for google.com ########
|domain: google.com
|        | ---> includes: ['_spf.google.com']
|        domain: _spf.google.com
|                | ---> includes: ['_netblocks.google.com', '_netblocks2.google.com', '_netblocks3.google.com']
|                domain: _netblocks.google.com
|                        | ---> ip4: ['64.233.160.0/19', '66.102.0.0/20', '66.249.80.0/20', '72.14.192.0/18', '74.125.0.0/16', '108.177.8.0/21', '173.194.0.0/16', '209.85.128.0/17', '216.58.192.0/19', '216.239.32.0/19']
|                domain: _netblocks2.google.com
|                        | ---> ip6: ['2001:4860:4000::/36', '2404:6800:4000::/36', '2607:f8b0:4000::/36', '2800:3f0:4000::/36', '2a00:1450:4000::/36', '2c0f:fb50:4000::/36']
|                domain: _netblocks3.google.com
|                        | ---> ip4: ['172.217.0.0/19', '172.217.32.0/20', '172.217.128.0/19', '172.217.160.0/20', '172.217.192.0/19', '108.177.96.0/19']

Stats for google.com:
 DNS Lookups: 5
 IPv4s: 16
 IPv6s: 6
 Fail type: SoftFail
 Raw record: v=spf1 include:_spf.google.com ~all
 </pre>