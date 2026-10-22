# transsera-web

Static website for the Transsera iOS app: home page, Privacy Policy, Terms of Use and Support.
Plain HTML and CSS, no build step.

Live: https://alexandrgraschenkov.github.io/transsera-web/

| Page | URL | Used in |
| --- | --- | --- |
| Home | `/` | App Store Connect → Marketing URL |
| Support | `/support_page.html` | App Store Connect → Support URL, app Options, sign-in help |
| Privacy Policy | `/privacy_policy.html` | App Store Connect → Privacy Policy URL, app Options, Purchases, sign-in help |
| Terms of Use | `/terms.html` | app Options, Purchases |

The app opens these URLs from `CourseraTest/UI/AppLinks.swift`. Keep file names stable.

## Publishing

GitHub → Settings → Pages → Source: **Deploy from a branch**, branch `main`, folder `/ (root)`.

Links inside pages are relative, so the site works under `/transsera-web/`. `404.html` is served for any missing path, so it uses absolute `/transsera-web/...` links. Update them if the site moves to a custom domain.

## Local preview

```sh
mkdir -p /tmp/site && ln -sfn "$PWD" /tmp/site/transsera-web
python3 -m http.server 8000 --directory /tmp/site
```

Open http://localhost:8000/transsera-web/.

## Keeping texts accurate

The Privacy Policy describes the app's actual data handling (Coursera session storage, translation requests, Firebase Analytics with 2-month event retention and 14-month user retention, Crashlytics, and the opt-out switch in Options → Privacy). Update it and the "Last updated" date whenever the app's SDKs or data flows change.

Verified on October 22, 2026 in Google Analytics → Transsera (property 214881949) → Admin → Data collection and modification → Data retention: event data is set to 2 months, user data to 14 months, and “Reset on new user activity” is enabled. Settings were inspected without changes. Recheck this page if the console settings change. Analytics deletion runs monthly, aggregated reports are outside these retention settings, and Crashlytics starts its deletion process after 90 days. Signing out removes the Coursera session but does not clear all local files.

The privacy notice still needs the developer's confirmed legal identity and the applicable legal bases and international transfer safeguards before treating its EU disclosures as complete. Do not infer these details from the app's browser positioning.
