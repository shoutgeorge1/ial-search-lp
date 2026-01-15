# PPC Implementation Checklist

## PHASE 1 — TRACKING (NON-NEGOTIABLE)

### GTM Setup
- [ ] Get GTM container ID from tagmanager.google.com
- [ ] Replace `GTM-XXXXXXX` in index.html (2 places: head and body)
- [ ] Remove hard-coded CallRail script from HTML
- [ ] Add CallRail DNI script to GTM as Custom HTML tag
- [ ] Verify GTM container is installed on main website
- [ ] Verify GTM container is installed on Vercel landing page
- [ ] Remove/disable any hard-coded GA4 tags
- [ ] Remove/disable any hard-coded Google Ads tags

### GA4 Setup (Via GTM)
- [ ] Create GA4 Configuration tag in GTM
- [ ] Set tag to fire on All Pages
- [ ] Enable Enhanced Measurement in GA4 config
- [ ] Create Custom Event Trigger: `engaged_30s` (Timer - 30 seconds)
- [ ] Create Custom Event Trigger: `scroll_90` (Scroll depth - 90%)
- [ ] Create Custom Event Trigger: `phone_click` (Click on tel: links)
- [ ] Create Custom Event Trigger: `form_start` (First form field focus)
- [ ] Create Custom Event Trigger: `form_submit` (Form submission)
- [ ] Mark `form_submit` as conversion in GA4
- [ ] Mark `phone_click` as conversion in GA4
- [ ] Mark `engaged_30s` as conversion in GA4 (temporary)

### Google Ads Setup
- [ ] Import GA4 conversions into Google Ads
- [ ] Set `form_submit` as primary conversion
- [ ] Set `phone_click` as primary conversion
- [ ] Keep CallRail calls as secondary conversion (avoid double counting)
- [ ] Test conversion tracking in GTM Preview mode

### Tracking Events (Already Added to Page)
- [x] `engaged_30s` - Timer event (30 seconds on page)
- [x] `scroll_90` - Scroll depth (90% of page)
- [x] `phone_click` - Click tracking on all phone links
- [x] `form_start` - When user starts filling form
- [x] `form_submit` - Form submission event

---

## PHASE 2 — CALLRAIL

### CallRail Pool Setup
- [ ] Create website pool in CallRail
- [ ] Set source: All website traffic
- [ ] Set pool size: 10-15 numbers
- [ ] Configure DNI script to load via GTM (not hard-coded)
- [ ] Set call threshold: Count calls ≥ 60 seconds as conversions
- [ ] Enable call recording
- [ ] Enable call tagging
- [ ] Get static CallRail number for call extensions
- [ ] Get static CallRail number for landing page
- [ ] Add static number to Google Ads call extensions
- [ ] Replace landing page phone number with CallRail static number
- [ ] Do NOT use Google forwarding numbers yet
- [ ] Verify CallRail integration with Google Ads is enabled
- [ ] Set CallRail to send conversions to Google Ads

---

## PHASE 3 — LANDING PAGE (PPC MODE)

### Above the Fold Requirements
- [ ] Update headline to: "Injured in California? Talk to a Lawyer Today."
- [ ] Add click-to-call phone number with DNI (CallRail static number)
- [ ] Simplify form to Name + Phone only (remove all other fields)
- [ ] Change form CTA to: "Get Help Now" or "Call Now"
- [ ] Remove extra navigation links
- [ ] Remove distracting elements above fold
- [ ] Ensure only ONE clear CTA above fold

### Landing Page Cleanup
- [ ] Remove or minimize content below fold
- [ ] Remove unnecessary sections
- [ ] Keep page focused on conversion
- [ ] Test mobile responsiveness
- [ ] Verify form submission still works
- [ ] Test phone number DNI swapping

### Decision: Create New Page or Modify Existing?
- [ ] Option A: Create `index-ppc.html` for PPC traffic (recommended)
- [ ] Option B: Modify existing `index.html` (loses brand content)

---

## PHASE 4 — CAMPAIGN HYGIENE

### Campaign Setup
- [ ] Keep Search – Web Visits as primary learning campaign
- [ ] Let Call Ads run (don't judge performance yet)
- [ ] Let Demand Gen run (don't judge performance yet)
- [ ] Do NOT add aggressive negative keywords for 7-10 days
- [ ] Let bid strategies finish learning before touching budgets
- [ ] Monitor CTRs (should be good)
- [ ] Monitor CPCs (should be cheap for CA PI)
- [ ] Monitor traffic quality (should be fine)

### Post-Launch Monitoring
- [ ] Wait 7-10 days before making major changes
- [ ] Review conversion data after learning period
- [ ] Identify bottleneck: tracking + funnel (not ads)
- [ ] Tighten → don't flinch

---

## TESTING CHECKLIST (Before Launch)

### GTM Testing
- [ ] GTM container ID is correct
- [ ] GTM Preview mode shows pageview fires
- [ ] `engaged_30s` event fires in GTM Preview (wait 30 seconds)
- [ ] `scroll_90` event fires in GTM Preview (scroll to bottom)
- [ ] `phone_click` event fires in GTM Preview (click phone link)
- [ ] `form_start` event fires in GTM Preview (focus first form field)
- [ ] `form_submit` event fires in GTM Preview (submit form)
- [ ] GA4 Configuration tag fires on all pages
- [ ] Google Ads conversion tag fires on form submit
- [ ] Google Ads conversion tag fires on phone click

### CallRail Testing
- [ ] CallRail DNI swaps phone numbers correctly
- [ ] Static number displays on landing page
- [ ] Static number used in call extensions
- [ ] Test call connects properly
- [ ] CallRail dashboard shows call tracking

### Form Testing
- [ ] Form submission works end-to-end
- [ ] Email received at intake@insiderlawyers.com
- [ ] CC email received at john@insiderlawyers.com
- [ ] Form data formatted correctly

### Conversion Tracking Verification
- [ ] Check Google Ads conversion tracking receiving data (after 24-48 hours)
- [ ] Verify GA4 conversions are importing to Google Ads
- [ ] Check CallRail conversions are sending to Google Ads
- [ ] Verify no double counting between GA4 and CallRail

---

## NOTES

- Tracking events (`engaged_30s`, `scroll_90`, `phone_click`, `form_start`, `form_submit`) are already added to index.html
- CallRail script is currently hard-coded - needs to be moved to GTM
- Current landing page doesn't match Phase 3 requirements - needs PPC optimization
- GTM container ID placeholder (`GTM-XXXXXXX`) needs to be replaced with actual ID
