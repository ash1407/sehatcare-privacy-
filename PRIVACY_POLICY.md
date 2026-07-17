# SehatCare — Privacy Policy

**Effective date:** 17 July 2026
**App:** SehatCare — Offline AI Health Companion (`com.example.sehatapp`)
**Publisher:** *Ashish Kumar Ray*
**Contact:** *ashishray2696@gmail.com*

This policy explains what SehatCare collects, where it is stored, who can see it, and what your rights are. It is written to satisfy Google Play's User Data policy and India's Digital Personal Data Protection Act, 2023.

## 1. In short

SehatCare is an **offline-first** health app. All health information you enter — symptoms, vitals, medicine reminders, family profiles, mental-health screening scores, menstrual cycle logs, diary entries, and chat conversations with the on-device AI Doctor — stays on your phone. **We do not run a server that receives your health data. We cannot see your data.**

The app does make network requests in three specific, user-initiated situations, described in §3.

## 2. What data SehatCare stores on your device

The following categories are stored only on your device, in the app's private storage (`SharedPreferences` and the app's private `files/` directory):

- **Personal profile** — display name, age, gender, allergies, chronic conditions, DOB (if you set one).
- **Family members** — same profile fields per member, plus the currently active member id.
- **Vitals log** — blood pressure, blood sugar, weight, temperature, and their timestamps.
- **Medicine reminders** — medicine name, strength, instructions, dose interval, start and end dates.
- **Prescription-scan output** — extracted medicine names/frequencies from photos you scanned.
- **Symptom check history** — symptom text you entered, the AI's suggested condition and severity.
- **Symptom diary** — daily entries you logged.
- **Mental-health screening** — PHQ-9 and GAD-7 scores, band, timestamp, safety flag. **Individual answers are not stored.**
- **Menstrual cycle log** — start/end dates, flow, symptoms, notes.
- **Vaccine schedule** — dates of vaccines you marked "given"; any custom vaccines you added.
- **Government schemes list** — the default set, anything synced from a URL you provided, or added manually.
- **Drug interactions list** — the default set plus any you added.
- **Chat sessions** — multi-session AI Doctor conversations, message text, timestamps, and per-session guided-flow state.
- **Sign-in state** — a PBKDF2-hashed PIN (never plaintext), a per-install random salt, an optional biometric-enabled flag, your display name.
- **App preferences** — language choice, permission-onboarding flag, model-download variant.

None of this leaves your phone.

## 3. Network activity — what and why

SehatCare uses the internet only for these operations, all triggered by you:

1. **AI model download.** The Gemma 4 language model (E2B or E4B variant, ~2.5–3.6 GB) is downloaded from a source you explicitly pick — HuggingFace (`huggingface.co`) or Google Drive. No health data is sent with the request. The download server sees only your phone's public IP address, User-Agent, and the fact that a Gemma file was requested.
2. **Government scheme lookup ("From webpage").** If you tap **From webpage** and provide a URL, SehatCare fetches that URL's HTML for one-time on-device parsing by the AI. The URL is one you typed; only that URL is fetched. Your health data is not sent.
3. **Find Nearby Doctor.** If you tap this button, SehatCare opens Google Maps with a search query built from the suggested specialist name. Google Maps then follows its own privacy policy.

SehatCare does not send analytics, telemetry, crash reports, or advertising identifiers anywhere.

## 4. AI processing — where it happens

The AI Doctor (Gemma 4) runs entirely on your device after the one-time model download. Every message you type into the chat, every symptom you enter into Symptom Checker, every question fed to the AI for pattern-spotting or briefing generation is processed **locally**. Nothing is uploaded to any AI service.

## 5. Firebase (optional, legacy)

Older versions of SehatCare offered Firebase Authentication as a cloud sign-in. The current version uses a **local PIN**, and Firebase Auth is not used on the sign-in path. Firebase code remains in the app for users who previously linked a cloud account; those users can sign out from **Profile → Sign-in settings → Sign out of cloud account**. No health data has ever been uploaded to Firebase.

If you never signed in with Firebase, no Firebase account exists for you and no Firebase network calls are made.

## 6. Permissions and why we ask for them

- **Notifications** — to fire medicine-reminder alarms.
- **Camera** — for the prescription scanner and chatbot photo attachments.
- **Microphone** — for voice input in the AI Doctor chat.
- **Exact alarms** — so reminders fire on time even when the phone is idle.
- **Battery optimization exemption** — so reminders aren't killed by aggressive OEM battery savers.
- **Install unknown apps** — only if you use "Share SehatCare with a Friend" to share the APK.
- **Storage (read only, via Android's Storage Access Framework)** — only when you tap "I already have the file" to point us at a pre-downloaded model on your device.

You can deny any permission and still use the app; the affected feature will explain what it needs.

## 7. Children

SehatCare is intended for users 13 years and older. It is not designed for children under 13 and should not be used to make medical decisions for infants without a doctor's supervision.

## 8. Data retention and deletion

Because SehatCare stores everything locally, deleting the app deletes your data. To delete data while keeping the app installed:

- Individual features have "Clear" / "Delete" controls (Reports, Chat sessions, Medicine reminders, Diary, etc.).
- To wipe *everything* the app has stored on your device: Android **Settings → Apps → SehatCare → Storage & cache → Clear storage**. This resets the PIN, deletes health data, and removes the AI model file.

We have no server-side data, so there is no server-side deletion request to make.

## 9. Security

- **PIN storage:** the PIN is hashed with PBKDF2-HMAC-SHA256 (100,000 iterations) using a 16-byte per-install random salt. Only the hash is stored. Verification uses constant-time comparison.
- **Biometric unlock:** uses AndroidX BiometricPrompt at the `BIOMETRIC_WEAK` level. Biometric templates never leave the phone's secure enclave.
- **Health data:** stored in the app's private directory, accessible only to SehatCare and to the device user via ADB backup — which we disable in the manifest (`allowBackup="false"`).
- **Network:** all downloads use HTTPS. Cleartext HTTP is denied by default in the network-security config.

## 10. Third-party services

SehatCare intentionally minimises third parties. The following are contacted only in the specific scenarios above:

- **HuggingFace** ([huggingface.co](https://huggingface.co)) — model host you can pick when downloading Gemma. [HuggingFace Privacy Notice](https://huggingface.co/privacy).
- **Google Drive** ([drive.google.com](https://drive.google.com)) — alternative model host you can pick. [Google Privacy Policy](https://policies.google.com/privacy).
- **Google Maps** ([maps.google.com](https://maps.google.com)) — used only if you tap **Find Nearby Doctor**. [Google Privacy Policy](https://policies.google.com/privacy).
- **Firebase** ([firebase.google.com](https://firebase.google.com)) — contacted only if you had a legacy cloud account and haven't signed out.

The AI Doctor is Google's Gemma 4 (E2B / E4B) open-weights model, run on-device. No inference request reaches Google or any AI provider.

## 11. Medical disclaimer

SehatCare is an **informational aid only**. It does not replace professional medical advice, diagnosis, or treatment. The AI Doctor's outputs are model-generated and may be wrong. Always consult a qualified doctor for medical decisions. In an emergency, call your local emergency number.

## 12. Changes to this policy

If we update this policy, we will publish the new version at the same URL and update the "Effective date" at the top. Substantive changes will be announced in-app.

## 13. Contact

Questions or complaints about privacy: *[your support email]*.

If you are in India, you have rights under the DPDP Act, 2023, including the right to access, correct, and erase your personal data. Since SehatCare stores data only on your device, these actions are performed directly by you on your device (§8).
