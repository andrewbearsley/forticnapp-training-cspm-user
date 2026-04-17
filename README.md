# FortiCNAPP Training for Service Owners: Compliance Self-Service

A ~20-minute training video for technical service owners who receive compliance alerts and need to action them in FortiCNAPP.

## Audience

Service owners who own AWS, Azure, or GCP resources and have received a compliance notification.

## Outcomes

By the end of this training you will be able to:

1. Log in to FortiCNAPP and set your notification preferences
2. Find the non-compliant resources you own in the Compliance section
3. Read a violation and follow the remediation instructions
4. Create an exception for a single resource
5. Create an exception that covers multiple resources by tag

## Format notes (for the video producer, not shown on screen)

- Each section has a **Slide**, an **image** (embedded screenshot, or a broken-image placeholder with alt text if not yet captured), a **Talk track** (spoken verbatim), and **Presenter notes** (commentary, not spoken)
- Screenshots to be captured from your FortiCNAPP tenant with representative (non-sensitive) data
- Run time target: 20 minutes. Talk track is ~1,100 words at ~110 wpm, which is about 10 minutes of pure narration. The remaining ten minutes come from visual dwell time: pointing at the screen, letting UI transitions play out, and letting viewers read dialogs and lists before moving on. Don't rush. Let the screen breathe
- Keep cursor movements slow and deliberate. The audience is watching the screen, not just listening

---

## Section 1: Welcome and what you'll learn (~1 min)

### Slide: Title card

![Title card: FortiCNAPP logo with title Actioning Compliance Alerts, a guide for service owners](images/01-title-card.png)

### Talk track

> Hi, and welcome. This is for anyone who owns a cloud resource (an S3 bucket, a VM, a database, a subscription) and has received a compliance notification email from the Cyber Security team.
>
> The email tells you one of your resources isn't meeting a security standard. In the next twenty minutes I'll show you what to do: log in, set your preferences, find the resource, follow the fix, and file an exception if you can't remediate.
>
> Nothing complicated. By the end you'll be self-serving, no ticket needed.

### Presenter notes

- Keep energy conversational. This is for people who didn't ask for this training
- Emphasise self-service so they know the goal is to unblock them

---

## Section 2: Logging in (~1 min)

### Slide: Accessing FortiCNAPP

![FortiCNAPP dashboard right after SSO completes, showing alert overview, non-compliant resources, exposed hosts, and the non-compliant resources trend](images/02-console-landing.png)

### Talk track

> The console URL is in the notification email. Bookmark it.
>
> Sign in with your usual single sign-on. If that breaks, it's an IT ticket, not something we cover here.
>
> Once you're in, this is the dashboard. What you see depends on your access. We're going straight to the compliance view.

### Presenter notes

- Do NOT record the SSO flow. Just jump-cut from the URL bar to the post-login dashboard

---

## Section 3: Setting your user preferences (~2 min)

### Slide: Finding your profile

![My profile page with the Settings sub-nav on the left (My profile highlighted) and the user's name, email, preferences, time zone, and My access on the right](images/03a-profile-page.png)

### Talk track

> Left nav, bottom, click **Settings**, then **My settings > My profile**.
>
> Name and email at the top. Below that, **My preferences**. Most people change a few things here.

### Slide: Preferences to change

![Close-up of the My preferences toggle group: Dark mode, Default email notification, Onboarding, Receive monthly updates from FortiCNAPP, Always send me updates, and Set time zone automatically](images/03b-profile-preferences.png)

### Talk track (continued)

> Four toggles matter.
>
> **Dark mode.** Your call.
>
> **Default email notification.** Turn off. It's generic FortiCNAPP notifications. Your compliance emails come through a separate pipeline and aren't affected.
>
> **Onboarding.** Turn off. In-app onboarding prompts, only useful the first time.
>
> **Receive monthly updates from FortiCNAPP.** Turn off. Vendor newsletter.
>
> Scroll down, **My access** shows your user group. Useful if you need to ask the access team about permissions.

---

## Section 4: Finding your non-compliant resources (~4 min)

### Slide: Navigate to Cloud Compliance

![Cloud compliance page with Risk Center > Compliance highlighted in the left nav, summary dashboard showing Total accounts, Policies, Resources and severity breakdown, filter bar, and the start of the frameworks list](images/04a-compliance-dashboard.png)

### Talk track

> In the left nav, under **Risk Center**, click **Compliance**, then **Cloud**.
>
> Each row is a framework your resources are evaluated against. CIS AWS, ISO 27001, and your organisation's custom framework if one's set up. That's usually the one your email came from.
>
> Click in.

### Slide: Inside the framework

![Framework drill-down with summary of policies with non-compliant resources, severity breakdown, and sections like Identity and Access Management listed below](images/04b-framework-detail.png)

### Talk track (continued)

> Summary panel on the right, sections below: Identity and Access Management, Data Security, Logging, and so on. Each lists policies and how many are failing.
>
> Your view is scoped to your team, so everything here is yours.

### Slide: Working by severity

![Filter panel open showing Severity, Assessability, and Resource status options with Has non-compliant resources selected](images/04c-filter-panel.png)

### Talk track (continued)

> Work the list by severity, highest first. Criticals, Highs, Mediums, Lows. The summary card tells you how many of each.
>
> Open the filter panel.
>
> **Resource status.** Set to *Has non-compliant resources*. Collapses the list to just the failing policies.
>
> **Severity.** Tick *Critical* only. Clear those. Then untick Critical, tick *High*. Repeat down the ladder.
>
> Click **Show results**.

### Slide: Policies grouped by service

![Policy list inside a framework with policies grouped by cloud service, for example a Storage S3 section listing lacework-global-49, lacework-global-50, and lacework-global-73 with non-compliant resource counts](images/04d-policies-in-section.png)

### Talk track (continued)

> Policies are grouped by service: S3, RDS, IAM, and so on. Scroll to the service you care about. Each row shows the policy ID (like `lacework-global-50`), name, non-compliant versus compliant counts, and severity.
>
> Pick a failing policy, click in.

### Presenter notes

- Use a real-looking but non-sensitive resource. A test S3 bucket is ideal
- Pace this slowly. This is where audience members most often get lost

---

## Section 5: Reading a violation and following remediation (~4 min)

### Slide: Anatomy of a violation

![Violation detail for lacework-global-50 Ensure that S3 is configured with Block Public Access enabled, showing 21 total resources (3 non-compliant, 18 compliant), with a Non-compliant resources tab listing three S3 bucket ARNs, region us-east-1, and account 395054243912](images/05a-violation-detail.png)

### Talk track

> I've clicked into *Ensure that S3 is configured with 'Block Public Access' enabled*. Policy ID `lacework-global-50`, severity High.
>
> Two things matter here.
>
> **On the right**, the summary. Twenty-one buckets evaluated, eighteen pass, three fail. Those three are your job.
>
> **At the bottom**, the **Non-compliant** tab lists them by ARN, region, and account. Each row has a link icon that jumps straight to the AWS Console.
>
> First, know *what* to fix. Click **View context**.

### Slide: Reading the policy context

![Fortinet documentation page for lacework-global-50 showing Profile Applicability Level 1, a Description explaining Block Public Access bucket and account settings, and a Rationale section](images/05b-policy-docs.png)

### Talk track (continued)

> **View context** opens the Fortinet documentation for this policy in a new tab. Three things matter here.
>
> **Description.** What the rule is checking. Here: whether Block Public Access is enabled at the bucket and account level.
>
> **Rationale.** Why it matters. Useful when someone asks why they have to change anything.
>
> And below: the **Remediation** section.

### Slide: Following the remediation

![Remediation section of the policy documentation with step-by-step instructions for enabling Block Public Access from the AWS Console and from the AWS CLI, including the aws s3api put-public-access-block command](images/05c-remediation-steps.png)

### Talk track (continued)

> Remediation gives you the fix two ways.
>
> **From Console.** Click by click: log in to AWS, open the S3 console, pick the bucket, edit public access settings, tick Block all public access, save.
>
> **From Command Line.** Copy the AWS CLI command, like `aws s3api put-public-access-block --bucket <name> ...`. Faster if you've got many buckets.
>
> Pick whichever suits, apply it to each bucket on the punch list.
>
> The compliance scan runs daily. Next day the fixed buckets drop off your list. You don't need to tell anyone. The scan picks it up automatically.

### Presenter notes

- Re-emphasise "you don't need to tell anyone". This is the self-service story
- If a viewer's tenant shows a "Last evaluated" or "First seen" date on the violation page, point it out. Service owners ask about that

---

## Section 6: Exceptions. Exempting a single resource (~3 min)

### Slide: When to use an exception

![Text slide listing valid reasons for an exception: Remediation is a change request, Resource is legacy or scheduled for decommission, Business-approved exception, False positive](images/06a-when-to-except.png)

### Talk track

> Sometimes you can't fix. Legacy system, test account, a documented business sign-off. In those cases, file an exception instead of ignoring the alert.
>
> An exception tells FortiCNAPP *this is failing and that's expected for now.* The finding drops off your notifications but stays visible as an exception for the security team to audit. That's the point. Tracked, not ignored.

### Slide: Creating the exception

![Violation detail page with the Add Exception button highlighted](images/06b-exception-button.png)

![Exception dialog with the scope set to a single resource ID and fields for reason, justification, and expiry date](images/06c-exception-single-resource.png)

### Talk track (continued)

> From the policy page, click **Add Exception**. A dialog opens. Four fields.
>
> **Scope.** What the exception covers. For one resource, select **Resource** and paste its ID. Only that resource is exempted.
>
> **Reason.** Dropdown: false positive, legacy system, risk accepted, and so on. Pick the closest.
>
> **Justification.** One or two sentences. Auditors read this. Don't write "approved". Write *who* approved it and *when*. Link a change ticket or RITM if you have one.
>
> **Expiry.** Always set one. Ninety days is a sensible default. Renew if the reason still holds.
>
> Click **Save**. The finding drops off your list within minutes and appears in the exceptions view for audit.

### Presenter notes

- Hover on the "Justification" field for a beat. This is the part service owners tend to skimp on
- If the UI uses slightly different labels (e.g. "Expiration" vs "Expiry"), match what's actually on screen

---

## Section 7: Exceptions by tag (~3 min)

### Slide: Why tag-based exceptions

![Diagram: one exception rule with a tag selector (for example Environment = sandbox) covering multiple resources](images/07a-tag-scope-diagram.png)

### Talk track

> Single-resource is fine for one-offs. But often what you want is *all my sandbox resources are exempt from this production-only policy*. Twenty individual exceptions for twenty buckets is painful, and you'd miss ones created next week.
>
> Tag-based exceptions solve that. Scope the exception to a tag. Any resource carrying that tag, now or in the future, is covered.

### Slide: Creating a tag-scoped exception

![Exception dialog with scope set to Tag and a tag key/value pair entered, for example Environment = sandbox](images/07b-exception-tag-scope.png)

### Talk track (continued)

> Back on the policy page, click **Add Exception**. For scope, choose **Tag**.
>
> Enter key and value. Say `Environment = sandbox`. Add more tags for an AND, like `Environment = sandbox` AND `Owner = my-team`.
>
> Same reason, justification, expiry fields. Save.
>
> From now on, any resource with those tags, including new ones, skips this policy. Set it once, it keeps applying.

### Slide: A word on tag hygiene

![Text slide: Your exceptions are only as good as your tags](images/07c-tag-hygiene.png)

### Talk track (continued)

> One caveat. This only works if your resources are actually tagged. Miss the `Environment` tag on half your sandbox buckets and they'll keep firing alerts.
>
> Tag your resources. Consistent tagging is what makes this scale.

### Presenter notes

- If the real UI supports multiple tag pairs only as OR (not AND), correct the talk track when recording
- If the UI uses a tag-prefix match or regex, demonstrate that instead of claiming AND

---

## Section 8: Wrap-up and where to get help (~2 min)

### Slide: Recap

![Five-point recap slide: 1. Log in at your FortiCNAPP console URL. 2. Set your notification email in your profile. 3. Find your resources in Compliance. 4. Follow the remediation guidance. 5. File an exception (with an expiry) when you can't remediate](images/08a-recap.png)

### Talk track

> Quick recap. Five things.
>
> One. Log in with your organisation's SSO.
>
> Two. Set your profile preferences. Turn off the notifications you don't need.
>
> Three. Go to Compliance. Everything you see is yours to action.
>
> Four. Open a policy, click View context, follow the remediation, fix the resource. The next daily scan picks up the fix.
>
> Five. When you can't remediate, file an exception. Resource or tag scope, real justification, expiry date. That's what keeps us auditable.

### Slide: Where to go next

![Contacts and links slide: FortiCNAPP console URL, Cyber Security team mailbox, IT Service Desk, FortiCNAPP documentation link](images/08b-contacts.png)

Contacts and links (produced with real contacts at record time):

- FortiCNAPP console URL
- Compliance questions / exception policy: Cyber Security team mailbox
- Can't log in: IT Service Desk
- <a href="https://docs.fortinet.com/product/forticnapp" target="_blank">FortiCNAPP documentation</a>

### Talk track (continued)

> Can't log in: IT. Exception questions: Cyber Security. Going deeper: the FortiCNAPP documentation, linked on the slide.
>
> That's it. Thanks for your time, and thanks for helping keep the environment secure.

### Presenter notes

- End crisply. Don't re-summarise the recap, just close
- Fade to the contacts slide and hold for 3 seconds before cutting

---

## Screenshot capture checklist (for the person recording)

Capture these against your real FortiCNAPP tenant with a non-sensitive test resource. Blur or crop account IDs and resource names where needed.

| # | File | What it shows |
|---|---|---|
| 01 | `01-title-card.png` | Title card (produced in slide tool, not captured) |
| 02 | `02-console-landing.png` | Post-SSO dashboard landing page |
| 03a | `03a-profile-page.png` | Settings sub-nav (My profile highlighted) + profile page |
| 03b | `03b-profile-preferences.png` | Close-up of My preferences toggles |
| 04a | `04a-compliance-dashboard.png` | Risk Center > Compliance highlighted + Cloud compliance page |
| 04b | `04b-framework-detail.png` | Drill-down into a single framework with failing controls |
| 04c | `04c-filter-panel.png` | Filter panel: Severity, Assessability, Resource status |
| 04d | `04d-policies-in-section.png` | Policy list within a framework, grouped by service |
| 05a | `05a-violation-detail.png` | Policy detail with the non-compliant resources list |
| 05b | `05b-policy-docs.png` | Fortinet docs for the policy: description and rationale |
| 05c | `05c-remediation-steps.png` | Remediation section: From Console and From Command Line |
| 06a | `06a-when-to-except.png` | Text slide (produced in slide tool) |
| 06b | `06b-exception-button.png` | Violation page with Add Exception button |
| 06c | `06c-exception-single-resource.png` | Exception dialog scoped to single resource |
| 07a | `07a-tag-scope-diagram.png` | Text/diagram slide |
| 07b | `07b-exception-tag-scope.png` | Exception dialog scoped to tag |
| 07c | `07c-tag-hygiene.png` | Text slide |
| 08a | `08a-recap.png` | Five-point recap slide |
| 08b | `08b-contacts.png` | Contacts and links slide |

---

## Pre-recording checklist

- [ ] Test account has at least one non-compliant resource that's safe to show on screen
- [ ] Notification email feature in profile has been verified. If it's not there in the current build, update Section 3
- [ ] Exception dialog has been walked through end-to-end to confirm the scope/reason/justification/expiry fields exist as described
- [ ] Confirm tag-scoped exceptions support AND vs OR vs single tag, and update Section 7 accordingly
- [ ] Confirm the custom framework name on screen matches what's said on the talk track
- [ ] Browser zoom set to 110 to 125% for readability in video
- [ ] Dark-mode vs light-mode decided and consistent across all screenshots
