# Weblate---Bug-writeup

# Weblate---Bug-writeup
🔐 Reset Password Cookie Gone Rogue: How I Almost Took Over Accounts (Legally!)

A story of cookies, redirects, and the dangers of “just one more click.”

TL;DR

Some innocent-looking password reset links can turn into your account’s worst nightmare. In this writeup, we’ll explore a combination of:

Wrong redirections

Persistent cookies

Login confusion

…that, if combined, could allow an account takeover.

Don’t worry: I’m not a hacker, just a curious security enthusiast documenting a bug responsibly.

🕵️ The Bug Story

Imagine this:

You forget your password (it happens).

You request a reset link.

You click the link… and everything seems normal.

But then, you close the tab… and click the link again.

Suddenly, instead of going back to the reset page, you land on:

https://hosted.weblate.org/accounts/login


…and you see the cryptic error:

{F1030242}


🤯 Oops. Something went wrong.

This is issue #1: misbehaving redirect.

<img width="690" height="164" alt="image" src="https://github.com/user-attachments/assets/38bffd06-3246-4a27-afda-5d2bbc23e2eb" />


Issue #2: Password Amnesia

<img width="1067" height="374" alt="image" src="https://github.com/user-attachments/assets/0e420a0f-de4d-4d3b-ac54-f13e8735e344" />


After this chaos, even your current password refuses to work:

{F1030244}


Logic fail: your password didn’t actually change, but the system acts like it did.
Impact: the user is effectively locked out temporarily, setting the stage for confusion… and account takeover.

Issue #3: Cookie Monster

<img width="1272" height="346" alt="image" src="https://github.com/user-attachments/assets/699213c8-1499-413d-b838-7312f2284b8b" />


The most dangerous part? Cookies. 🍪

After clicking the reset link, a cookie is stored in the browser and sticks around for hours.
Now imagine this on a shared computer.

Someone else goes to the “Forgot Password” page.

They click reset.

Boom: they can hijack your account thanks to that stubborn cookie.

💡 Remediation: Reduce cookie lifespan, always redirect to the reset page, and maybe… don’t leave your cookies lying around like chocolate chips in a toddler’s backpack.

🧪 How I Discovered This

Requested a password reset link.

Clicked it, closed the tab, clicked it again.

Observed the weird redirect.

Tried logging in with current password → rejected.

Checked cookies → aha! Persistent reset cookie.

🔧 Technical Recommendations

Always redirect to the password reset page, no matter how many times the link is clicked.

Reduce cookie lifespan to minimize account takeover risk.

Optional: Consider one-time tokens for reset links so they can’t be reused maliciously.

⚠️ The Impact

Users on shared computers are at risk.

Hackers could legally hijack accounts if someone leaves their reset link open.

A combination of bad redirects + persistent cookies = account takeover fiesta. 🎉

🥳 Fun Takeaways

Cookies are sweet… until they’re dangerous.

Reset links are like fire: handle with care.

Always double-check redirects, or your users might end up in a digital Bermuda Triangle.

✅ Responsible Disclosure

I reported this bug through the HackerOne bug bounty program, and the team at Weblate was awesome—they fixed it promptly. The vulnerability was responsibly disclosed, and now users are safer! 🎉

Bonus

If you’re reading this and you work in Europe or France — 👋 Hi! I’m a student exploring cybersecurity. Looking for internships in:

🧩 Pen Testing

🛡️ SOC Analysis

🧠 GRC

🔐 IAM

Or anything related to security which you think i would be a perfect fit

Let’s make security fun, ethical, and human again. 💙 feel free to email me : keshorpuresoul@gmail.com #CyberSecurity #BugBounty #PenTesting #EthicalHacking #Internship #France #CyberTalent #InfoSec #AppSec #SecurityResearch #BugHunter #InDrive #EthicalHacker #SecurityAwareness
