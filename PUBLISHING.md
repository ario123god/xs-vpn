# GitHub Pages publishing

The `docs/` directory is prepared as a GitHub Pages site for the repository
`xs_vpn.github.io`. It contains `index.html` for the XS-VPN privacy policy and
`app-ads.txt`, which is served at the website root.

1. Add the repository to GitHub, or push these files to the repository you want to
   publish. Keep `docs/index.html` and `docs/app-ads.txt` together.
2. In GitHub, open **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**. Select the branch
   containing these files and choose **/docs** as the folder, then save.
4. Wait for the Pages deployment. For the repository named `xs_vpn.github.io`, the
   expected policy URL is `https://xs_vpn.github.io/` and the ads file URL is
   `https://xs_vpn.github.io/app-ads.txt`.
5. The privacy contact email is set to `thealangod55@icloud.com`. Before publishing,
   verify that this address is monitored. The app repository does not contain the
   feed/server implementation or its deployment configuration, so API access logs,
   IP-address logging, diagnostics, and retention/rotation settings remain
   unverified. Keep the policy's explicit disclosure unless you confirm those facts
   from the actual feed host and deployment. Third-party VPN server operator
   practices are unknown.
6. If using a custom domain, add it in **Settings → Pages**, configure DNS as GitHub
   instructs, and confirm `https://<your-domain>/app-ads.txt` loads. Add the website
   domain to the app store developer contact details if required by the ad network.

The root `app-ads.txt` has been copied unchanged from the Android project root.
