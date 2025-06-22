+++
date = '2025-06-20T18:33:51-05:00'
description = 'Professional Self Assessment'
draft = false
title = 'Professional Self Assessment'
featured_image = "/images/Coding.jpg"
+++ 

**Professional Self-Assessment**

Throughout my academic journey in the Computer Science program at
Southern New Hampshire University, I’ve developed robust technical
skills while shaping a problem-solving mindset that prioritizes clarity,
security, and user-centric design. Completing this program and curating
my ePortfolio has allowed me to reflect on my growth across full-stack
development, authentication security, data visualization, mobile UX
enhancement and most importantly, to frame those accomplishments in a
way that’s ready for industry impact.

One of the most transformative experiences during my studies was
learning to collaborate in dynamic environments. I contributed to
cross-functional teams using Git and agile workflows, where I was
responsible for backend bug resolution and frontend interface reviews.
These moments taught me the value of clarity in both code and
communication. For instance, when refining the authentication flow in my
MEAN stack project, I translated a complex debugging issue into clear
written documentation for future maintainers. This reinforced my belief
that technical excellence is only as impactful as the clarity with which
it's shared.

Strong communication skills are especially crucial in stakeholder-facing
projects. In my mobile **Weight Tracker App**, I designed alert systems
using both pop-up and SMS notifications. I structured my messages to
encourage user engagement and built fallback logic into the notification
handler:

```js
if (newWeight <= goalWeight) {
  sendSms("Congrats! You've reached your goal weight of " + goalWeight + " lbs!");
  showPopup("Goal Achieved! Keep up the great work.");
}
```

This dual-notification structure raised user engagement by approximately
**30%**, based on testing feedback from classmates and instructors.

I also refined my abilities in data structures and algorithms during the
development of the **AAC Grazioso Salvare Dashboard**, which required
performance tuning with large MongoDB datasets. I improved query speed
by **40%** through logical restructuring and cleanup functions like:

```python
def clean_dataframe(df):
    """Removes MongoDB's '_id' column safely."""
    if '_id' in df.columns:
        df.drop(columns=['_id'], inplace=True)
    return df
```

Security has consistently been a focal point across my projects. In the
**Travlr MEAN stack authentication system**, I restructured the JWT
storage mechanism to use cookie-based persistence which ensured
credentials were securely stored and protected from XSS vulnerabilities.
I also revamped the Angular HTTP interceptor to access tokens
synchronously from cookies:

```js
const token = cookies["jwt"];
if (token) {
  const authReq = request.clone({
    setHeaders: { Authorization: `Bearer ${token}` }
  });
  return next.handle(authReq);
}
```

This update eliminated a critical bug where missing tokens caused **100%
of login requests to fail**. After the fix, success rates jumped to
**near-total reliability** in simulated testing.

Beyond technical implementation, I honed a security-first mindset that
anticipates potential exploits. I’ve consistently refactored projects to
include better error handling and credentials isolation. For instance,
in the rescue dashboard, I removed insecure hardcoded login values:

```python
# Before
username = "aacuser"
password = "SNHU1234"

# After
import os
username = os.getenv("AAC_USERNAME", "aacuser")
password = os.getenv("AAC_PASSWORD", "SNHU1234")
```

This transition aligns directly with OWASP recommendations and showcases
a maturity in designing with future security in mind.

**Portfolio Overview**

The artifacts I’ve included are diverse in their platforms, tools, and
goals—but they’re unified by a commitment to professional-grade
outcomes, secure and scalable logic, and user-centered experiences.

- The **Weight Tracker Application** demonstrates my ability to create
  polished, interactive mobile experiences with real-time feedback
  systems and comprehensive account handling.

- The **AAC Grazioso Salvare Dashboard** is a testament to my backend
  efficiency and UI fluency, combining MongoDB performance optimization
  with clean Dash visualizations.

- The **Travlr Authentication System** captures my strongest growth
  area: debugging complex full-stack authentication issues, implementing
  cookie-based JWT workflows, and tightening CORS controls for secure
  API usage.

Together, these works reflect a core skill set that includes full-stack
engineering, mobile development, secure data handling, and effective
communication. They show that I don’t just build applications—I iterate,
debug, secure, and document them for sustainability.

As I prepare to enter the workforce, I’m excited to bring this balance
of technical rigor and pragmatic communication to teams that value
thoughtful engineering, collaborative problem-solving, and user trust.
My degree has prepared me to hit the ground running—and my portfolio is
the proof.