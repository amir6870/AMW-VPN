# Live VPN server deployment checklist

For each of the seven advertised countries:
1. Contract a reputable VPS provider with an actual server location in that country.
2. Confirm local law, provider acceptable-use rules, bandwidth limits, and data-processing terms.
3. Install and harden WireGuard; apply firewall policy and IPv4/IPv6 routing.
4. Configure NAT/masquerading, DNS resolvers, MTU, key rotation, monitoring, and abuse handling.
5. Generate a separate client key/config per user/device. Never reuse one private key across customers.
6. Test external IPv4/IPv6 address, DNS leaks, reconnect behavior, kill switch, throughput, and latency.
7. Publish only locations that pass testing. Do not display Kuwait as a VPN exit location.

The Google Play app must disclose VpnService use, collect only necessary data, provide a clear privacy policy, and comply with current Play policies. Google Play country/account/payment profile are not changed by VPN IP alone.
