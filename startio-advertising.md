# Start.io advertising setup and privacy

The Play Store build includes Start.io Android SDK 5.4.0 and reserves a Home banner
slot. The F-Droid build does not include this SDK. Ad initialization is currently
**blocked**: this project has no consent management platform or age-aware consent management system. The SDK's automatic initialization
provider and boot receiver are removed from the Play Store manifest. There are no
app-initiated splash, return, interstitial, exit, or background ad placements.

Before enabling ads:

1. The supplied Start.io App ID is configured in `app/build.gradle.kts` and can be
   overridden with `-PSTART_IO_APP_ID=YOUR_APP_ID`. It is not the seller account ID
   in `app-ads.txt`.
2. The developer describes the target audience as adults and teens, not children.
   Start.io’s publisher agreement prohibits sharing users’ personal data with
   Start.io when the user is under 16. The app stores a broad age band selected
   in Privacy choices; under-16 and unknown values fail the initialization gate. Apply the corresponding Start.io and
   Play Store settings and review the SDK-merged permissions.
3. A suitable candidate is Google UMP, configured with a Google-certified TCF CMP
   message. It requires a separate AdMob application ID (`ca-app-pub-…~…`), an
   AdMob account and published EEA/UK/Switzerland and applicable US-state privacy
   messages, with Start.io and required purposes/vendors included. At review time
   the [IAB global vendor list](https://vendor-list.consensu.org/v3/vendor-list.json)
   identifies Start.io Inc as vendor 1216 with consent purposes 1, 3 and 4; check
   the current vendor list and CMP policy configuration before production. UMP's
   `canRequestAds()` alone is not evidence of consent to Start.io. Confirm Start.io
   vendor-specific TCF consent and applicable US GPP/opt-out signals before
   initialization. The code has no UMP SDK, adapter, form or signal processing yet.
   Integrate an appropriate consent management platform, including any required
   IAB TCF/GPP signals, regional opt-outs, consent revocation and privacy options.
   The existing project has no such system. Wire its verified consent decision and
   timestamp to `StartIoAds.initializeAfterConsent` only after both consent and
   audience requirements are satisfied. The two fail-closed constants in that
   object must remain false until these changes have actually been implemented and
   reviewed. A boolean alone is not a substitute for a compliant CMP.
4. Publish an accurate XS-VPN privacy policy and replace the existing upstream
   v2rayNG privacy-policy link. Complete Google Play Data safety, obtain dashboard
   approval, and configure Start.io payment and tax details before release.
5. Publish the repository-root `app-ads.txt` unchanged at
   `https://MY_DEVELOPER_DOMAIN/app-ads.txt`; add that domain as the developer
   website in Play Console → Store presence → Store settings → Store listing
   contact details. No website is published by this project.

## Advertising data disclosure for the XS-VPN policy

The 5.4.0 SDK manifest also adds the Android advertising-ID, Wi-Fi state,
Privacy Sandbox Topics and install-referrer permissions and a launcher-app query.
Review these merged declarations before shipping, especially for younger users.

When advertising is enabled and the SDK is initialized, Start.io may process
network and device information such as IP address, device model, OS version,
advertising identifier, carrier and device settings, and interactions with ads
or apps. Start.io and its advertising partners use information for advertising,
measurement, fraud prevention and related services. Data processing, sharing,
retention, user choices and any use of approximate location inferred from IP must
be described in the actual published privacy policy and consent interface after
reviewing the current SDK version and applicable jurisdictions. Do not describe
this integration as collecting no data. See [Start.io privacy FAQ](https://www.start.io/privacy-faq/)
and [Start.io end-user privacy policy](https://www.start.io/policy/privacy-policy-site/).

Debug builds explicitly enable Start.io test ads; release builds explicitly
turn test ads off. Test ads are not loaded until the initialization gate is
satisfied. Never click live ads while testing. Validate banner load/failure,
activity recreation, consent withdrawal and both audience/consent paths on a
physical device or emulator before release.
