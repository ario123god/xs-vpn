# XS-VPN privacy policy — draft, not published

**Owner:** [OWNER LEGAL NAME AND ADDRESS REQUIRED]  
**Privacy contact:** [PRIVACY EMAIL OR CONTACT METHOD REQUIRED]  
**Effective date:** [REQUIRED]  
**Jurisdictions and rights contact:** [REVIEW AND COMPLETE]

This draft describes the current Android code and the proposed Start.io integration.
It must be reviewed, completed and published at a real XS-VPN URL before release.
The app's current upstream policy link has not been replaced.

## VPN and server information

XS-VPN connects your device to a server you select or that the app selects.
Traffic sent through that server is handled by the server operator and destination
services. The operator, logging practices, locations, retention and access controls
for these servers must be documented by the owner; this repository does not establish
whether a particular server stores logs or whether its location is accurate.

The Android app downloads server configurations from the configured XS-VPN feed.
The current feed uses HTTP, so network operators between the app and feed can see
and modify requests and responses, including the embedded feed credential and server
configurations. The feed operator may receive the device's network IP address and
request details. The owner must document feed logs and retention and deploy HTTPS.

Imported server configurations and app preferences are stored on the device using
the app's local storage. Favorites, recently used servers, test results, selected
server and settings may also be stored locally. Removing the app normally removes
its app-private data, subject to Android backup and device settings. The owner must
review retention, backup behavior, and support procedures before publishing.

The app can measure server availability and latency. Automatic selection also sends
small download and upload tests through candidate servers to Cloudflare's speed-test
service; Cloudflare receives the candidate server's exit IP address and test-request
information. The owner should review [Cloudflare's privacy policy](https://www.cloudflare.com/privacypolicy/)
and disclose applicable retention and choices.

## Advertising and age band

Start.io advertising is included in the Play Store build but is currently disabled;
no Start.io SDK initialization or ad request is made by the app's current code.
The F-Droid build does not include the Start.io SDK. The app can store an optional
age band (under 16, 16 or older, or prefer not to say); it does not request a full
birth date for this purpose. Users under 16 and users whose age band is unknown are
ineligible for Start.io initialization under the planned policy.

If advertising is enabled in a future release after consent and age handling are
implemented, Start.io may receive the device's IP address, device and OS details,
advertising identifier, carrier, settings, and ad or app interaction data, and may
share or use data for advertising, measurement and fraud prevention. See
[Start.io's privacy policy](https://www.start.io/policy/privacy-policy/) and
[privacy FAQ](https://www.start.io/privacy-faq/). Complete the actual vendor list,
legal bases, data-sharing arrangements, regional opt-outs and consent withdrawal
information before enabling advertising. Do not represent this draft as a complete
account of Start.io or other third parties' practices.

## Choices, requests and contact

The advertising age band can be changed through Privacy choices in the Play Store
app. Consent management and regional advertising opt-out controls are not yet
implemented; advertising must remain disabled until they are available. Contact
[PRIVACY CONTACT REQUIRED] to make access, correction, deletion or other requests.
The owner must identify request procedures, response periods, retention periods,
international transfers and any additional rights applicable to its users.
