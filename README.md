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

- Each section has a **Slide**, a **Screenshot placeholder**, a **Talk track** (spoken verbatim), and **Presenter notes** (commentary, not spoken)
- Screenshots to be captured from your FortiCNAPP tenant with representative (non-sensitive) data
- Run time target: 20 minutes. Talk track totals ~2,600 words at ~130 wpm
- Keep cursor movements slow and deliberate. The audience is watching the screen, not just listening

---

## Section 1: Welcome and what you'll learn (~1 min)

### Slide: Title card

**Screenshot placeholder:** `images/01-title-card.png`. FortiCNAPP logo with the title "Actioning Compliance Alerts: A Guide for Service Owners".

### Talk track

> Hi, and welcome. This short training is for anyone who owns a cloud resource (an S3 bucket, a VM, a database, a subscription) and has received a compliance notification email from the Cyber Security team.
>
> These emails tell you that one of your resources isn't meeting an organisational security standard. In the next twenty minutes, I'll show you exactly what to do about it. We'll cover four things: logging in and setting your notification email, finding your resource, following the remediation instructions, and, for the cases where you can't or shouldn't remediate right now, creating an exception.
>
> Nothing here is complicated. By the end you'll be able to self-serve, without needing to open a ticket.

### Presenter notes

- Keep energy conversational. This is for people who didn't ask for this training
- Emphasise self-service so they know the goal is to unblock them

---

## Section 2: Logging in (~1 min)

### Slide: Accessing FortiCNAPP

**Screenshot placeholder:** `images/02-console-landing.png`. The FortiCNAPP dashboard as it appears right after SSO completes. Blur any account names or resource IDs.

### Talk track

> Let's start by getting into the console. Your organisation's FortiCNAPP URL has been shared with you in the notification email. I'd recommend bookmarking it now.
>
> You'll sign in with your organisation's single sign-on credentials the same way you sign in to anything else, so I'm not going to walk through that part. If you can't log in, that's a ticket for IT, not something we cover here.
>
> Once you're in, this is what you'll see: the main dashboard. Don't worry about the numbers on this screen. They cover the whole environment, and most of it won't be yours. We're going to drill straight down to just your resources in a moment.

### Presenter notes

- Do NOT record the SSO flow. Just jump-cut from the URL bar to the post-login dashboard
- If the demo account shows cross-tenant data, mention the tenant picker briefly but don't dwell

---

## Section 3: Setting your user preferences (~2 min)

### Slide: Setting your notification email

**Screenshot placeholder:** `images/03a-profile-menu-open.png`. Top-right avatar menu expanded, with "My Profile" or "Profile" highlighted.

**Screenshot placeholder:** `images/03b-profile-page.png`. The profile/preferences page showing the email field and notification options.

### Talk track

> The first thing I want you to do is check your profile. Click your initials or avatar in the top right, then click **My Profile**.
>
> On this page you'll see the email address FortiCNAPP has on file for you. By default, this is your work email, the one your SSO is tied to. For most people that's exactly what you want, and you don't need to change anything.
>
> Where this matters is if you'd rather get notifications at a team mailbox, say a shared cloud-ops inbox, instead of your personal inbox. You can update the notification email here, save, and that's where future compliance emails will land.
>
> A quick word on how you got the email in the first place. The Cyber Security team runs a scheduled scan, groups non-compliant resources by their owner tag, and sends each owner a digest. If your resources aren't tagged with an owner, they'll go to a default mailbox and someone will come find you. So: tag your resources. That's the single most useful thing you can do to make these emails land in the right place.

### Presenter notes

- If the actual UI for notification preferences is minimal, keep this section short. Don't invent features
- The "tag your resources" line is the main point. Say it slowly

---

## Section 4: Finding your non-compliant resources (~4 min)

### Slide: Navigate to Compliance

**Screenshot placeholder:** `images/04a-left-nav-compliance.png`. Left navigation panel with **Posture > Compliance** (or wherever the current build puts it) highlighted.

**Screenshot placeholder:** `images/04b-compliance-dashboard.png`. Compliance overview showing frameworks (e.g. CIS AWS, and your organisation's custom framework) with pass/fail counts.

### Talk track

> Now let's find your resources. In the left-hand navigation, open **Posture**, then click **Compliance**.
>
> This is the compliance overview. Each row here is a framework: a set of rules that resources are evaluated against. You'll see standard ones like CIS for AWS, and you'll also see your organisation's custom framework. That's the internal framework the Cyber Security team maintains, and it's the one your notification email was generated from.
>
> Click on that framework to open it.

### Slide: Inside the framework

**Screenshot placeholder:** `images/04c-framework-detail.png`. Framework report showing categories like "Identity and Access Management", "Data Security", with failed control counts and filter bar visible at top.

### Talk track (continued)

> Inside, you'll see categories: Identity and Access Management, Data Security, Logging, and so on, each with a count of how many controls are failing. At this point you're looking at every failing control across every account in the organisation, which is not what you want.
>
> What you want is just *your* resources. There are two ways to narrow it down, and the one you use depends on what you have.
>
> **If you know the account ID**, for example your team owns a specific AWS account, use the account filter at the top and paste it in. The report will now only show controls failing in that account.
>
> **If you got a notification email**, scroll down in the email. Each finding has a direct link that takes you straight to the resource inside FortiCNAPP, pre-filtered. That's always the fastest path. Don't retype the resource ID; just click the link.

### Slide: Searching for a specific resource

**Screenshot placeholder:** `images/04d-resource-search.png`. Search or filter box with a resource ID partially typed, results narrowing in real time.

### Talk track (continued)

> You can also search by resource ID or resource name if you have it. The search box at the top of the page accepts partial matches, so if you only remember part of your bucket name, that's fine.
>
> Take a minute, find a resource you recognise, and click into it. That's what we'll look at next.

### Presenter notes

- Use a real-looking but non-sensitive resource. A test S3 bucket is ideal
- Pace this slowly. This is where audience members most often get lost

---

## Section 5: Reading a violation and following remediation (~4 min)

### Slide: Anatomy of a violation

**Screenshot placeholder:** `images/05a-violation-detail.png`. Single policy/violation view showing policy name, severity, affected resources count, description.

### Talk track

> Let's open a violation. I've clicked into one called *Ensure S3 buckets employ encryption-at-rest*. This is a medium-severity finding, and it applies to any bucket in your account where default encryption isn't configured.
>
> The page is laid out in three useful parts.
>
> **At the top** you've got the policy itself: the name, a plain-English description of what the rule is checking, and the severity. This is also where you'll see the policy ID, something like `lacework-global-72`. Note that down. You'll want it if you need to open a ticket or ask a question.
>
> **In the middle** is the remediation guidance. This is the part you actually care about. It'll tell you exactly what to change on the resource, often with the specific AWS Console path, the CLI command, or the Terraform snippet. Read it carefully, because the fix is usually a one-liner but it has to be done in the right place.

### Slide: The affected resources list

**Screenshot placeholder:** `images/05b-affected-resources.png`. Table of affected resources below the policy, with columns for resource ID, account, region, tags.

### Talk track (continued)

> **At the bottom** you've got the list of resources that are actually failing this policy. If your filter is set to your account, this is your punch list: every resource you need to fix.
>
> Click on any resource in the table and you'll get the full resource detail page. You'll see the tags that are set on it, which account and region it lives in, when FortiCNAPP first saw it was non-compliant, and a link straight out to the AWS Console for that resource. Use that link. It's the fastest way to get from "I know what's wrong" to "I'm fixing it."

### Slide: Your remediation path

**Screenshot placeholder:** `images/05c-remediation-steps.png`. Remediation guidance panel with numbered steps, highlighted.

### Talk track (continued)

> So the full loop is: open the violation, read the remediation steps, click through to the resource in the AWS Console, make the change, and you're done. The next time FortiCNAPP scans, usually within a few hours, the finding will drop off your list and you'll stop getting notifications for it.
>
> You don't need to tell anyone you fixed it. The scan picks it up automatically.

### Presenter notes

- Re-emphasise "you don't need to tell anyone". This is the self-service story
- If the UI shows a "First Seen" date, point it out. Service owners ask about this

---

## Section 6: Exceptions. Exempting a single resource (~3 min)

### Slide: When to use an exception

**Screenshot placeholder:** `images/06a-when-to-except.png`. A simple text slide listing valid reasons: "Remediation is a change request", "Resource is legacy / scheduled for decommission", "Business-approved exception", "False positive".

### Talk track

> Now, sometimes you can't fix a finding. Maybe it's a legacy system you can't touch without a change request. Maybe it's a test account where the rule genuinely doesn't apply. Maybe there's a documented business reason the security team has already signed off on. In those cases, file an exception instead of ignoring the alert.
>
> An exception tells FortiCNAPP: *yes, this resource is failing this policy, and that's expected for now.* The finding will stop appearing in your notifications, but it'll still be visible in the dashboard as an explicit exception, so the security team can audit it later. That's the difference between an exception and ignoring the email. Exceptions are tracked and reviewable.

### Slide: Creating the exception

**Screenshot placeholder:** `images/06b-exception-button.png`. The violation detail page with an **Add Exception** or **Create Exception** button highlighted.

**Screenshot placeholder:** `images/06c-exception-single-resource.png`. Exception dialog with the resource scope set to a single resource ID, fields visible for reason, justification, and expiry date.

### Talk track (continued)

> Let's walk through it. From the policy page (the same one we were just on), click **Add Exception**.
>
> A dialog opens. There are four things you need to fill in.
>
> **Scope.** This is what the exception applies to. For our first use case, we want this exception to cover just one specific resource, so select **Resource** and paste in the resource ID from the affected list. Only that one resource is exempted; everything else still gets evaluated.
>
> **Reason.** Pick from the dropdown: false positive, legacy system, risk accepted, and so on. Pick the one closest to the truth.
>
> **Justification.** Write a sentence or two explaining why. This is the field auditors read. Don't write "approved". Write *who* approved it and *when*. Reference a change ticket or a RITM number if you have one.
>
> **Expiry.** Always set an expiry. Ninety days is a sensible default. Don't leave exceptions open forever. If the reason is still valid in ninety days, renew it.
>
> Click **Save**. The finding will disappear from your active list within a few minutes, and it'll appear in the exceptions view for the security team to audit.

### Presenter notes

- Hover on the "Justification" field for a beat. This is the part service owners tend to skimp on
- If the UI uses slightly different labels (e.g. "Expiration" vs "Expiry"), match what's actually on screen

---

## Section 7: Exceptions by tag (~3 min)

### Slide: Why tag-based exceptions

**Screenshot placeholder:** `images/07a-tag-scope-diagram.png`. A simple diagram: one exception rule with a tag selector (e.g. `Environment = sandbox`) covering multiple resources.

### Talk track

> The single-resource exception is useful when it's one specific thing. But often what you actually want to say is: *all my sandbox resources are exempt from this production-only policy.* Creating twenty individual exceptions for twenty sandbox buckets would be painful, and you'd miss ones that get created next week.
>
> That's where tag-based exceptions come in. Instead of scoping the exception to a resource ID, you scope it to a tag. Any resource, now or in the future, that carries that tag is covered by the same exception.

### Slide: Creating a tag-scoped exception

**Screenshot placeholder:** `images/07b-exception-tag-scope.png`. Exception dialog with scope set to **Tag** and a tag key/value pair entered, e.g. `Environment = sandbox`.

### Talk track (continued)

> Back on the policy page, click **Add Exception** again. This time, for scope, choose **Tag** (or **Resource Tag**, depending on the UI wording).
>
> Enter the tag key and the tag value. Let's say you're exempting everything tagged `Environment = sandbox`. You can add more than one tag if you need an AND condition, for example `Environment = sandbox` AND `Owner = my-team`. That makes the scope as specific as you need.
>
> Same fields after that: reason, justification, expiry. Save it.
>
> From that moment on, any resource carrying those tags won't trigger this specific policy, including new resources you spin up tomorrow. You set the rule once and it keeps applying.

### Slide: A word on tag hygiene

**Screenshot placeholder:** `images/07c-tag-hygiene.png`. Simple text slide: "Your exceptions are only as good as your tags."

### Talk track (continued)

> One caveat. Tag-based exceptions only work if your resources are actually tagged. If half your sandbox buckets are missing the `Environment` tag, they'll keep firing the alert and you'll be confused about why your exception isn't working.
>
> So, same message as before: tag your resources. Consistent tagging is what makes all of this scale.

### Presenter notes

- If the real UI supports multiple tag pairs only as OR (not AND), correct the talk track when recording
- If the UI uses a tag-prefix match or regex, demonstrate that instead of claiming AND

---

## Section 8: Wrap-up and where to get help (~2 min)

### Slide: Recap

**Screenshot placeholder:** `images/08a-recap.png`. Simple five-point text slide:
1. Log in at your FortiCNAPP console URL
2. Set your notification email in your profile
3. Find your resources in **Compliance**
4. Follow the remediation guidance
5. File an exception (with an expiry) when you can't remediate

### Talk track

> Quick recap. Five things.
>
> One. Log in to the FortiCNAPP console with your organisation's single sign-on.
>
> Two. Check your profile and make sure notifications go to the right mailbox.
>
> Three. In Compliance, filter to your account or click the link from the email to find your resources.
>
> Four. Open a violation, read the remediation, and fix the resource. The next scan picks up the fix automatically, and the emails stop.
>
> Five. When you genuinely can't remediate, file an exception. Scope it to a resource or a tag, write a real justification, and set an expiry. That's the bit that keeps us auditable.

### Slide: Where to go next

**Screenshot placeholder:** `images/08b-contacts.png`. Simple text slide with contacts and links (produced with real contacts at record time):
- FortiCNAPP console URL
- Compliance questions / exception policy: Cyber Security team mailbox
- Can't log in: IT Service Desk
- <a href="https://docs.fortinet.com/product/forticnapp" target="_blank">FortiCNAPP documentation</a>

### Talk track (continued)

> If you can't log in, that's IT. If you've got a question about whether an exception is appropriate, that's the Cyber Security team. And if you want to go deeper on any of this, the FortiCNAPP documentation is linked on the last slide.
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
| 03a | `03a-profile-menu-open.png` | Top-right profile menu expanded |
| 03b | `03b-profile-page.png` | Profile/preferences page with email field |
| 04a | `04a-left-nav-compliance.png` | Left nav with Compliance highlighted |
| 04b | `04b-compliance-dashboard.png` | Compliance overview with frameworks |
| 04c | `04c-framework-detail.png` | Custom framework drill-down |
| 04d | `04d-resource-search.png` | Resource search/filter in action |
| 05a | `05a-violation-detail.png` | Policy/violation detail top half |
| 05b | `05b-affected-resources.png` | Affected resources table |
| 05c | `05c-remediation-steps.png` | Remediation guidance panel |
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
