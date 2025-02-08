# React Native AppsInsights

![GitHub License](https://img.shields.io/github/license/ashokdevatwal/react-native-apps-insights)
![npm](https://img.shields.io/npm/dw/%40ashokdevatwal/react-native-apps-insights)
![npm](https://img.shields.io/npm/v/%40ashokdevatwal%2Freact-native-apps-insights)
![GitHub package.json version (branch)](https://img.shields.io/github/package-json/v/ashokdevatwal/react-native-apps-insights/master)



## Install 

The **recommended** way to install the latest version of react-native-apps-insights is by running the command below:

NPM Install
```bash
npm i @ashokdevatwal/react-native-apps-insights
```
Yarn Install
```bash
yarn add @ashokdevatwal/react-native-apps-insights
```

### Usages

```javascript
import AppsInsights from "@ashokdevatwal/react-native-apps-insights";

// Needed Only To Track Facebook App Install Campaign 
AppsInsights.config({
  installReferrerDecryptionKey : "2575590594a9cd809e5bfacf397f8c1ac730dbc38a3e137ecd1ab66591c8c3c9" 
});

// Install Track
 AppsInsights.getInstallReferrerInfoFromPlay()
 .then(installReferrerInfo => {
  // Handle the install referrer info here
  console.log('Install Referrer Info:', installReferrerInfo);
})
.catch(error => {
  // Handle any errors here
  console.error('Error:', error);
});
```
## How To Test
 - Your app must be on the Play Store to test this feature.
 - Start Google Play on the device using the campaign link.
 - ``DON’T TAP ON INSTALL BUTTON`` in PlayStore.
 - Install your test build using adb. `adb install -r app-debug.apk` Open the app through the play store.
 - Google Play will be returning your test campaign now
 - When you put your app to close testing you don’t need to follow above steps to check out the referral feature just click on campaign link and install app

 ### Note: 
 If you have previously opened the Play Store via a referral link, you must clear Play Store data before testing another link for the same app. This is because the Play Store retains data from the previous link, and if that link was broken or invalid, you won’t be able to test a new one.

 
#### Dummy Facebook App Install Campaign link
```Link
https://l.facebook.com/l.php?u=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.example.application%26referrer%3Dutm_source%253Dapps.facebook.com%2526utm_campaign%253Dfb4a%2526utm_content%253D%25257B%252522app%252522%25253A0%25252C%252522t%252522%25253A1694258301%25252C%252522source%252522%25253A%25257B%252522data%252522%25253A%252522afe56cf6228c6ea8c79da49186e718e92a579824596ae1d0d4d20d7793dca797bd4034ccf467bfae5c79a3981e7a2968c41949237e2b2db678c1c3d39c9ae564c5cafd52f2b77a3dc77bf1bae063114d0283b97417487207735da31ddc1531d5645a9c3e602c195a0ebf69c272aa5fda3a2d781cb47e117310164715a54c7a5a032740584e2789a7b4e596034c16425139a77e507c492b629c848573c714a03a2e7d25b9459b95842332b460f3682d19c35dbc7d53e3a51e0497ff6a6cbb367e760debc4194ae097498108df7b95eac2fa9bac4320077b510be3b7b823248bfe02ae501d9fe4ba179c7de6733c92bf89d523df9e31238ef497b9db719484cbab7531dbf6c5ea5a8087f95d59f5e4f89050e0f1dc03e464168ad76a64cca64b79%252522%25252C%252522nonce%252522%25253A%252520%252522b7203c6a6fb633d16e9cf5c1%252522%25257D%25257D%26fbclid%3DIwAR2zaxdWKFCLGQqSbX_bN2kt50HaTBmYbAQKaP_xtHMcx6q1schqSX3vW2k&h=AT3PHbTNUnQUC0SbF9l16mGLj566b-Ogme_DoA-5aUSg6jLCphNQ8YtTj2pXlNZH7INKlUFvFrrUyHXhSQiDgJsDWaqUGBgAjj_TQ0VG-OsiTRgMaBExoeDlzzB-oiMZ4uqSRg&__tn__=*J%2C%3C%2CmH-R&c[0]=AT0ogjXkb2N_f18mVy8H-tve_wRPwW5yflj7Zo9Pz0-hL9tsfC3k_hhCN4gs5nW1xef5RINy5BvJ6bc_QksEW25WyGHF0ZN18AKtFdkRXE6B3rsI7kkGHxdcMXDUNutkg1d_J00hLMC2pN43DJ-ghJx0rJ53IU3WrJiFny6UmLLIO6PIZYhQQNBHuUhFHX4
```
#### Dummy campaign link
```Link
https://play.google.com/store/apps/details?id=com.example.application&referrer=utm_source%3Dgoogle%26utm_medium%3Dcpc%26utm_term%3Drunning%252Bshoes%26utm_content%3Dlogolink%26utm_campaign%3Dspring_sale
```
 - You can generate a test link from [this website](https://developers.google.com/analytics/devguides/collection/android/v4/campaigns#google-play-url-builder) for your app.
- Make Sure replace application id  `com.example.application` with your application id (The final package that is used in your built .apk's manifest, e.g. com.example.application)

#### Note : 
- Decryption key is required for facebook app install campaign.
- Get decryption key from your facebook developer account. Here is [guide to get decryption key](https://developers.facebook.com/docs/app-ads/install-referrer/)  

### If App Installed From Google Play Store 
```json
{
  "googlePlayInstant": "false",
  "installBeginTimestampSeconds": "2022-10-15 11:42:30", 
  "installBeginTimestampServerSeconds": "2022-10-15 11:42:29", 
  "installReferrer": "utm_source=google-play&utm_medium=organic",  
  "installVersion": "1.9.6",
  "referrerClickTimestampSeconds": "1970-01-01 05:30:00",
  "referrerClickTimestampServerSeconds": "1970-01-01 05:30:00",
  "utm_medium": "organic", 
  "utm_source": "google-play"
}
```

 - `googlePlayInstant`: Information if your app's instant version (if you have one) was launched in past 7 days
 - `installBeginTimestampSeconds`: Timestamp of when app installation on device begun
 - `installBeginTimestampServerSeconds`: Server timestamp of when app installation on device begun
 - `installReferrer`: Install referrer string value 
 - `installVersion`: Original app version which was installed
 - `referrerClickTimestampSeconds`: Timestamp of when user clicked on URL which redirected him/her to Play Store to download your app
 - `referrerClickTimestampServerSeconds`: Server timestamp of when user clicked on URL which redirected him/her to Play Store to download your app

### If App Installed From Google Play Store Ads

```json
{
  "gclid": "EAIaIQobChMIrKLVotP2gIVhFj9Ch3eDwNhEAAYASAAEgIrDvD_BwE",
  "installBeginTimestampServerSeconds": "2023-09-19 16:34:53",
  "referrerClickTimestampSeconds": "2023-09-19 16:33:06",
  "installBeginTimestampSeconds": "2023-09-19 16:34:54",
  "installVersion": "1.9.6",
  "referrerClickTimestampServerSeconds": "2023-09-19 16:33:06",
  "googlePlayInstant": "false",
  "installReferrer": "gclid=EAIaIQobChMIrKLVotP2gIVhFj9Ch3eDwNhEAAYASAAEgIrDvD_BwE"
}
```

### If App Installed From Facebook App Install Campaign Link
```json
{
  "account_id": "444444",
  "ad_id": "12345",
  "ad_objective_name": "APP_INSTALLS",
  "adgroup_id": "54321",
  "adgroup_name": "Adams Test Ad Group",
  "campaign_group_id": "654321",
  "campaign_group_name": "Adams Test Campaign Group",
  "campaign_id": "987654",
  "campaign_name": "Adams Test Campaign",
  "googlePlayInstant": "false",
  "installBeginTimestampSeconds": "2023-09-08 11:28:23",
  "installBeginTimestampServerSeconds": "2023-09-08 11:28:21",
  "installReferrer": "utm_source=apps.facebook.com&utm_campaign=fb4a&utm_content=%7B%22app%22%3A0%2C%22t%22%3[...long Hash....]301%2C%22source%22%3Anull%7D",
  "installVersion": "1.9.6",
  "referrerClickTimestampSeconds": "1970-01-01 05:30:00",
  "referrerClickTimestampServerSeconds": "1970-01-01 05:30:00",
  "utm_campaign": "Adams Test Campaign",
  "utm_source": "apps.facebook.com",
  "utm_content": "%7B%22app%22%3A0%2C%22t%22%3[...long Hash....]301%2C%22source%22%3Anull%7D"
}
```
