+++
date = '2025-05-26T20:19:54-05:00'
draft = false
title = 'Algorithms and Data Structures'
featured_image = "/images/Coding.jpg"
+++

This is the second improvement project that I have chosen to showcase as part of my Computer Scence Capstone Class.

I have chosen to improve the code for the animal shelters application which utilizes python in order to perform CRUD operations as well as search and filters on content within a database. This application was developed in my CS-340 Client/Server Development class. This provides an excellent framework to implement improved code structure, improved portability of code methods, and enhanced optimization.

I completed a code review prior to implementing improvements to the project. The link to this code review is provided here:
https://youtu.be/ULIRyS-XVs4

This is the original form of my Weight Tracker Application:
[Download the file](https://benjamin-sturgeon.github.io/projects/Animal_Shelter_Application_Original.zip)

This is the improved version:
[Download the file](https://benjamin-sturgeon.github.io/projects/Animal_Shelter_Application_Improved.zip)

This is the Code Review Script that I used for my Analysis:

1.  **Category Two: Algorithms and Data Structures**

    1.  Provide a clear, complete description of existing code
        **functionality.**

        1.  What does the code do?

            - This application provides an organized view of the
              contents of a database which stores various details about
              pets in an Animal Shelter. Information is displayed on
              easy to view charts with options to filter results. CRUD
              operations are provided in order to add or remove database
              contents and complete the necessary MongoDB queries to
              filter results.

        2.  Focus on the features and functions of the existing code.

            - The features provided in this application are:

              - Animal Shelter Pet Information Storage

              - Presentation of Information from the Database

              - An Interactable UI to set presentation style and
                contents

              - CRUD operations on database contents

              - Changeable filters to show specific Animals and traits

              - Information presented in Charts

    2.  **Analyze** existing code using relevant code review criteria to
        support clearly stated findings.

        1.  Use the checklist to review the code critically. This review
            might highlight weaknesses, such as not following secure
            coding best practices, having no error handling, code not
            being efficient, code that needs debugging, and so on. Not
            all the items on the checklist will be applicable, so review
            the ones that are applicable to your artifact.

            - Here’s a structured code review based on the **CS 499 Code
              Review Checklist**:

            - **Structure**

            - The code is well-structured and conforms to standard
              Dash practices.

            - Some FIX ME comments indicate unfinished
              implementations (e.g., Grazioso Salvare logo).

            - Several instances of pd.Dataframe.from\_records should
              be corrected to pd.DataFrame.from\_records.

            - The filter logic contains {"or": \[...\]}—should be
              {"$or": \[...\]} for valid MongoDB syntax.

            - Efficient use of reusable components such as DataTable
              and Map widgets.

            - **Documentation**

            - Code has inline comments explaining functionality.

            - Some comments indicate planned updates but are not yet
              implemented.

            - Commenting style is consistent and maintainable.

            - **Variables**

            - Meaningful variable names enhance readability (e.g.,
              username, password, df).

            - Hardcoded credentials ("aacuser" and "SNHU1234") should
              be replaced with environment variables.

            - Correct type consistency in assignments.

            - **Arithmetic Operations**

            - No floating-point equality checks detected.

            - No risky additions/subtractions with drastically
              different magnitudes.

            - **Loops and Branches**

            - Loop structures are simple and correct.

            - df.drop(columns=\['\_id'\], inplace=True) appears
              multiple times—could be moved to a function to avoid
              redundancy.

            - Case statements (if filter\_type == 'Water' etc.) are
              missing explicit else handling to confirm valid defaults.

            - **Defensive Programming**

            - Missing checks for file existence before reading
              (open(image\_filename, 'rb') could fail).

            - MongoDB queries correctly structured (except $or
              issue).

            - No explicit error handling for database connections.

        2.  Target areas for improvement such as structure, logic,
            efficiency, functionality, security, testing, commenting,
            and documenting.

            - **Suggestions for Improvement**

            - Move repeated DataFrame transformation
              (df.drop(columns=\['\_id'\])) to a helper function.

            - Secure credentials with environment variables instead of
              hardcoded values.

            - Ensure logo file handling accounts for potential missing
              files.

            - Fix incorrect MongoDB syntax ({"or": \[...\]} → {"$or":
              \[...\]}).

            - Clean up FIX ME comments by completing pending tasks.

            - Overall, great structure—just a few fixes needed!

    3.  Explain practical **enhancements** aligned with analysis
        findings in a clear and organized manner.

        1.  Say what you plan to do in your enhancement. What specific
            skills will you demonstrate, and which of the five course
            outcomes will your enhancements support?

            - I will improve this application in a few key areas. First,
              I will restructure code by creating designated filter
              helper methods for each filter operation utilized within
              the code. This will improve the portability and will more
              closely align with object-oriented programming methods.

            - I will also optimize the application by implementing a
              dictionary-based filtration system which can be accessed
              by any of the filter methods. This will be much more
              efficient than utilizing separate filtered code present in
              every method. This will also make it much easier to change
              and upgrade filter functions.

            - In addition to this, comments will be cleaned up to
              eliminate FIX ME sections and provide clear and concise
              information.

            - Hardcoded content will be converted into specific
              variables to allow for easy manipulation.

            - File handling will be improved to account for failures to
              read or write.

            - Syntax Errors will be corrected to ensure that the program
              behaves as expected.

            - The specific skills highlighted in this enhancement
              showcase my ability to improve code usability and
              portability, which are critical when developing code
              intended to be analyzed by others or used in a team
              setting. This will also highlight my understanding of how
              to improve search and filtration of data within a
              database.

            - The enhancements that I implement on this artifact best
              align with course outcomes three and four. I will design
              and evaluate a computing solution which follows the best
              computer science practices and standards set forth in
              object-oriented programming. This also demonstrates
              increased value by making the program more efficient and
              easier to use while also aligning with industry standards
              of code portability and reusability.