# AMW VPN — Android starter + website

This is a production-oriented **starter project**, not a live VPN service yet.

## Included
- Android app shell with seven selectable locations: India, USA, UK, Singapore, Japan, Canada, Switzerland.
- WireGuard tunnel integration point and secure configuration loading.
- No Kuwait server entry.
- Static landing website and privacy/terms pages.
- Server provisioning checklist.

## Important deployment boundary
A VPN app cannot change the public IP by itself. Each location needs a real WireGuard server, a static public IP, firewall rules, routing/NAT, DNS, monitoring, and a unique client configuration. No server credentials or live endpoints are fabricated here. Until those are provisioned and added, the app must not claim it is connected.

## Android build
Open this folder in Android Studio (Giraffe or newer), allow Gradle sync, then build the `app` module.
The WireGuard Android tunnel library is referenced as a Maven dependency. Verify the dependency version against the official WireGuard Android release before production release.

## Add real servers
For each country, provision a server and create a WireGuard client config. Place configs in:
`app/src/main/assets/wireguard/`
Use exactly these filenames:
- india.conf
- usa.conf
- uk.conf
- singapore.conf
- japan.conf
- canada.conf
- switzerland.conf

Do not commit private keys or production configs to a public repository. For a real release, fetch encrypted configs after user authentication from a secure API, or inject them through a private build pipeline.

## Play Store
The Android `VpnService` permission flow is required. Google Play country, payments profile, and account region are separate from VPN IP and do not automatically change when connecting to India.

## Build APK from a phone with GitHub Actions
The archive includes `.github/workflows/android-apk.yml`. Upload the extracted project contents to a new GitHub repository on branch `main`. GitHub Actions then builds a debug APK and stores it as an artifact. Open Actions → Build AMW VPN APK → latest run → Artifacts → AMW-VPN-debug-apk.

This workflow builds the UI starter APK only. It is not yet a functioning VPN tunnel: real server infrastructure and WireGuard backend integration are still required.
