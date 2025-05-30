+++
date = '2025-05-26T20:19:54-05:00'
draft = false
title = 'Software Engineering And Design'
featured_image = "/images/Software.png"
+++

This is the first improvement project that I have chosen to showcase as part of my Computer Scence Capstone Class.

The artifact that I have chosen for this category is my Weight Tracking application that I developed in my CS 360 Mobile Architecture and Programming class. I have chosen this because it provides an excellent opportunity to showcase my understanding of application development and how to make changes based on the visual needs of users.

I completed a code review prior to implementing improvements to the project. The link to this code review is provided here:
https://youtu.be/ULIRyS-XVs4

This is the original form of my Weight Tracker Application:
[Download the file](https://benjamin-sturgeon.github.io/projects/CS-360WeightTrackerOriginal.zip)

This is the improved version:
[Download the file](https://benjamin-sturgeon.github.io/projects/CS-360WeightTrackerImproved.zip)

This is the Code Review Script that I used for my Analysis:

1.  **Category One: Software Design and Engineering**

    1.  Provide a clear, complete description of existing code
        **functionality**.

        1.  What does the code do?

            - The first artifact that I will be improving is a Weight
              Tracking Application. This simple Java application is
              designed to run on Android OS and provides users with a
              way to track their weight. They can also set their goal
              weight and opt in to receive a text notification once
              their goal weight is reached. User accounts are created
              during the initial login screen of the application. Data
              is kept locally on the device via a MongoDB schema.

        2.  Focus on the features and functions of the existing code.

            - User Account Creation and Authentication

            - Weight Recording in pounds and the date of recording

            - Presentation of the weights in a convenient list

            - Addition and Removal of weights from the list

            - Text Notifications

            - Goal Weight Set

    2.  **Analyze** existing code using relevant code review criteria to
        support clearly stated findings. **Analysis is completed on Main
        Activity and the relevant SMS Dialog Fragment in order to focus
        on the scope of the specific planned improvements**

        1.  Use the checklist to review the code critically. This review
            might highlight weaknesses, such as not following secure
            coding best practices, having no error handling, code not
            being efficient, code that needs debugging, and so on. Not
            all the items on the checklist will be applicable, so review
            the ones that are applicable to your artifact.

            - Thanks for providing the checklist! Here's my structured
              code review based on the criteria:

> **MAIN ACTIVITY**

- **Structure**

    - The code generally follows good structuring principles, using clear
    class definitions and modularization.

    - The implementation aligns with its intended functionality.

    - No evident coding standards violations, but ensuring consistency in
    commenting conventions would be useful.

    - No unnecessary procedures or unreachable code detected.

    - Reusable components, such as utility functions for validation, could
    improve readability and maintainability.

    - No explicit magic number constants, but using constant variables for
    fixed values (e.g., SEND\_SMS\_REQUEST\_CODE) enhances clarity.

    - No excessive complexity detected, but certain methods such as
    validation functions could be refined for readability.

- **Documentation**

    - While some methods are sufficiently documented, improving inline
    comments would enhance maintainability.

    - Some comments appear redundant—ensuring they contribute to
    understanding the code rather than repeating it would improve clarity.

- **Variables**

    - Meaningful variable names are used.

    - Explicit type definitions are maintained.

    - No apparent redundant or unused variables.

- **Arithmetic Operations**

    - No floating-point equality checks detected.

    - No evident risk of rounding errors in numerical operations.

    - Division operations are not present, so checking for zero divisors is
    not necessary.

- **Loops and Branches**

    - All loops appear correct and properly nested.

    - Default conditions are used where needed.

    - Logical flow is maintained within the IF-ELSE constructs.

    - Loop termination is clear, though ensuring rigorous testing of edge
    cases is recommended.

- **Defensive Programming**

    - User input validation is integrated but could be strengthened by
    checking for possible injection attacks.

    - Error-handling mechanisms for database interactions are minimal—adding
    exception handling would enhance reliability.

    - Permissions checks are correctly implemented, ensuring SMS-related
    permissions are verified before proceeding.

> **SMS DIALOG FRAGMENT**

- **Structure**

    - The code correctly implements the expected design, defining a
    **DialogFragment** for SMS permission requests.

    - It follows Android coding conventions and uses appropriate class
    structures.

    - The SMSPermissionDialogMessagePrompt class is modular and does not
    contain unnecessary procedures or unreachable code.

    - There are no redundant test routines or stubs.

    - No evident use of magic numbers, as all constants are sourced from
    resources (R.string values).

    - No excessive complexity detected—the code is relatively simple and
    well-structured.

- **Documentation**

    - The code lacks inline comments. Adding brief, meaningful comments for
    method purpose and key logic points would improve maintainability.

    - There’s no misleading documentation, but further explanations of
    behavior (especially around permission handling) would be useful.

- **Variables**

    - Variables are well-defined with clear names.

    - No redundant or unused variables detected.

- **Arithmetic Operations**

    - No arithmetic operations are present, so floating-point comparisons,
    rounding errors, and zero divisors are not relevant.

- **Loops and Branches**

    - No loops are present in this code snippet.

    - The IF-ELSE structure inside setPositiveButton and setNegativeButton
    is well-implemented.

    - Logic flows correctly without any missing conditions.

- **Defensive Programming**

    - The code correctly checks for user interaction using the
    DialogInterface.OnClickListener.

    - However, there is **no null check** for mListener before invoking
    onSMSPermissionDialogMessagePrompt(true/false). If the fragment is
    attached incorrectly or the context is mismanaged, this could lead to
    a NullPointerException.

    - The usage of TextView padding is hardcoded
    (textView.setPadding(30,10,30,10);). Consider using **resource
    values** to maintain consistency across different device screens.

    - No external device access or memory allocation issues are present.

1.  Target areas for improvement such as structure, logic, efficiency,
    functionality, security, testing, commenting, and documenting.

> **MAIN ACTIVITY**

- **Suggested Improvements**

    - **Enhance Error Handling:** Introduce exception handling in database
    access methods to avoid application crashes.

    - **Improve Reusability:** Create separate utility functions for
    validation logic rather than keeping them within MainActivity.

    - **Strengthen Security:** Consider salting and hashing user passwords
    at the validation stage instead of relying on retrieval functions.

    - **Improve Commenting:** Ensure comments provide meaningful
    explanations rather than redundant clarifications.

> **SMS DIALOG FRAGMENT**

- **Suggested Improvements**

    - **Add Null Checks** for mListener to prevent runtime crashes due to
    unexpected fragment attachment failures.

    - **Improve Documentation** by adding concise comments that explain the
    purpose of each method.

    - **Use Resource Values** for TextView padding instead of hardcoded
    values.

    - **Refactor Listener Assignment**—consider safer handling during the
    onAttach lifecycle to avoid unexpected failures.

1.  Explain practical **enhancements** aligned with analysis findings in
    a clear and organized manner.

    -  Say what you plan to do in your enhancement. What specific
        skills will you demonstrate, and which of the five course
        outcomes will your enhancements support?

        - I will specifically convert the SMS notification system to a
          dialogue which users can designate as Push Notifications, SMS
          Notifications, none, or both. This will greatly enhance the
          notification capabilities of the application. This enhancement
          will demonstrate my capabilities in developing and altering
          notification systems within a mobile application. I will also
          be creating the visual enhancements necessary for push
          notifications which will demonstrate my understanding of UI
          enhancement. The outcomes that this enhancement will
          demonstrate are two and three. This will demonstrate my
          ability to design, develop, and deliver visual and written
          communications which are well adapted to the intended
          audience. Push notifications are an excellent way to present
          information in a mobile environment and giving users the
          ability to choose represents evaluation of computing solutions
          which solve the problem of knowing when a goal weight has been
          reached.

<!-- -->