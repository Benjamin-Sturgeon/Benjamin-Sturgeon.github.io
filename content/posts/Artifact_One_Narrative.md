+++
date = '2025-05-26T20:10:41-05:00'
draft = false
title = 'Artifact One Narrative'
featured_image = "/images/avatar4.jpg"
+++

**Artifact One: Weight Tracking Application**

1.  **Briefly describe the artifact. What is it? When was it created?**

The *Weight Tracking Application* is a mobile-based Android solution designed to assist users in monitoring their weight progress through interactive features, intuitive design, and goal-driven notifications. Created as part of my coursework in 2025, the initial version implemented basic logging and visualization capabilities. Enhancements brought refined user interface elements, responsive layouts, and meaningful real-time engagement, transforming the app into a more complete, user-centric experience.

1.  **Justify the inclusion of the artifact in your ePortfolio. Why did you select this item?**

This artifact reflects my ability to build and iteratively improve a mobile application through full-stack and user-centered principles. Specific components that showcase my development strengths include:

- **UI/UX Design with Material Principles:** I integrated gradient backgrounds, updated typography, and floating action buttons (FAB) to modernize the app’s appearance:

```xml
<com.google.android.material.floatingactionbutton.FloatingActionButton
    android:id="@+id/fabAddWeight"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginEnd="16dp"
    android:layout_marginBottom="16dp"
    app:layout_anchor="@id/weightListView"
    app:srcCompat="@drawable/ic_add"
    android:backgroundTint="@color/colorAccent"/>
```

- **Database Handling & Account Cleanup:** I implemented a secure delete-account feature that removes user data and associated weight entries:

```java
public void deleteUserAccount(String userId) {
    FirebaseDatabase db = FirebaseDatabase.getInstance();
    DatabaseReference userRef = db.getReference("users").child(userId);
    DatabaseReference weightsRef = db.getReference("weights").child(userId);
    weightsRef.removeValue(); // Deletes weight logs
    userRef.removeValue();    // Deletes user credentials
}
```

- **Event-Based Notifications:** I added popup and SMS alerts when users reach their target goals, using conditional logic:

```java
if (newWeight <= goalWeight) {
    showPopup("🎯 You've reached your goal of " + goalWeight + " lbs!");
    sendSMS(userPhone, "Congrats on hitting your weight goal!");
}
```

- **Code Modularity and Readability:** Repetitive logic was abstracted into helper methods for maintainability:

```java
private boolean isValidWeightInput(String weightInput) {
    return weightInput != null && !weightInput.isEmpty() && weightInput.matches("\\d{2,3}");
}
```

These enhancements collectively improved app usability, engagement, and structural integrity, making the artifact both aesthetically pleasing and functionally sound.

1.  **Did you meet the course outcomes you planned to meet?**

Yes. This project aligns with the following course outcomes:

- **Collaborative Environments:** UX decisions were driven by iterative testing and feedback interpretation.
- **Professional Communication:** Codebase includes detailed JavaDoc-style comments and logical naming conventions.
- **Computing Solutions Evaluation:** I implemented structured validation logic to process and visualize user data efficiently.
- **Engineering Practices:** Used RecyclerView and ConstraintLayout components for scalable list rendering and adaptive layout behavior.
- **Security Mindset:** Developed defensive null checks and validation strategies to prevent crashes and unauthorized data access.

1.  **Reflect on the process of enhancing and modifying the artifact.**

Several significant challenges strengthened my abilities throughout this project:

- **ConstraintLayout Design:** Adjusting UI responsiveness across screen sizes was achieved through careful anchoring and testing:

```xml
app:layout_constraintTop_toTopOf="parent"
app:layout_constraintStart_toStartOf="parent"
app:layout_constraintEnd_toEndOf="parent"
```

- **Notification Logic Bug:** An oversight in the notification handler failed to trigger alerts for edited entries. I corrected this by checking value updates against the goal:

```java
if (previousWeight > goalWeight && newWeight <= goalWeight) {
    triggerGoalReachedAlert();
}
```

- **Deletion Cascade Issues:** I discovered that weight entries weren't cleared when deleting a user. The solution was to explicitly call both user and subcollection references.

This process significantly expanded my understanding of mobile UI responsiveness, backend integrity, and user-centered alerting systems. It stands as a well-rounded example of applying classroom theory to practical, real-world software design.