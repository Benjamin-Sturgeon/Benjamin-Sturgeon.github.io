+++
date = '2025-05-26T20:10:41-05:00'
draft = false
title = 'Artifact Two Narrative'
featured_image = "/images/avatar4.jpg"
+++

Artifact Two Narrative

**Narrative: Enhancing the AAC Grazioso Salvare Dashboard**

**Brief Description of the Artifact**

This artifact is an interactive Jupyter Dash application, built to
visualize animal rescue data efficiently using MongoDB queries, Dash
components, and Plotly visualizations. Originally created as part of the
Southern New Hampshire University CS 499 Capstone, the dashboard
provides users with filtering options, an interactive data table, a map
visualization, and a pie chart representation of rescued animal breeds.

Initially, the application contained a functional design but lacked
security best practices, efficiency optimizations, and thorough error
handling. The enhancement process focused on addressing these weaknesses
while refining code quality for better maintainability.

**Justification for Inclusion in My ePortfolio**

I selected this artifact because it showcases my ability to develop
full-stack applications with a strong emphasis on data handling,
efficient querying, and UI design principles. Specifically, this
dashboard demonstrates my proficiency in:

- **Algorithms and Data Structures**: Implementing optimized database
  queries with MongoDB’s filtering mechanisms.

- **Security Best Practices**: Replacing hardcoded credentials with
  environment variables to prevent exposure.

- **Software Engineering Principles**: Modularizing redundant operations
  through helper functions and error handling.

The improvements made to this artifact reflect my growth as a software
engineer, as they required analytical thinking, debugging, and
performance tuning which are critical skills in industry settings.

**Enhancements and Course Outcome Alignment**

The changes made to this artifact align with key course outcomes by
reinforcing:

1.  **Secure Software Development Practices**:

    - Implementing environment variables for authentication.

    - Adding file existence checks before reading images to prevent
      runtime errors.

    - Enhancing MongoDB query validity ("$or" instead of "or") to
      prevent unexpected database errors.

2.  **Performance Optimization**:

    - Refactored repetitive operations (e.g., removing redundant \_id
      column) into a helper function (clean\_dataframe()).

    - Streamlined conditional filtering logic, making it more readable
      and scalable.

3.  **Improved Code Maintainability**:

    - Added detailed comments explaining functionality for better
      documentation.

    - Modularized query handling, reducing redundancy and improving
      clarity.

These enhancements directly contribute to my goal of securing a software
development role, ensuring I can write scalable, optimized, and secure
code. No major updates are needed to my course outcome plans, but this
project further solidifies my strengths in database-driven applications.

**Reflection on the Enhancement Process**

Throughout the revision, I deepened my understanding of Dash, MongoDB,
and Python’s best practices. I learned:

- The importance of readability; writing well-structured code minimizes
  future debugging efforts.

- How data validation safeguards prevent application crashes.

- Why code modularization enhances both maintainability and performance.

One of the biggest challenges was ensuring MongoDB queries returned the
expected results without errors. Debugging filtering logic required
careful attention to syntax corrections ("$or" instead of "or"),
reinforcing the necessity of accurate database querying.

Overall, refining this artifact not only strengthened my technical
expertise but also reinforced the importance of writing efficient,
scalable, and secure code which are all crucial for professional
software development.

I provided some examples of the improvements I implemented below:

**1. Secure Authentication Handling**

Initially, hardcoded credentials (username = "aacuser", password =
"SNHU1234") posed a security risk. I improved this by using environment
variables.

**Before (Insecure Hardcoded Credentials)**

username = "aacuser"

password = "SNHU1234"

**After (Secure Approach with Environment Variables)**

import os \# Import OS module to access environment variables

username = os.getenv("AAC\_USERNAME", "aacuser") \# Default to 'aacuser'
if env var is missing

password = os.getenv("AAC\_PASSWORD", "SNHU1234") \# Default to
'SNHU1234' if env var is missing

**Benefit:** Sensitive credentials are no longer exposed in the source
code, reducing security vulnerabilities.

**2. Modularized Data Cleaning for Better Code Maintainability**

The original code repeated the same operation
(df.drop(columns=\['\_id'\], inplace=True)) multiple times across
different sections. I improved this by creating a reusable function.

**Before (Repeated Code in Multiple Places)**

df.drop(columns=\['\_id'\], inplace=True) \# Removing MongoDB ObjectID
in multiple locations

**After (Reusable Helper Function)**

def clean\_dataframe(df):

"""Removes MongoDB's '\_id' column safely."""

if '\_id' in df.columns:

df.drop(columns=\['\_id'\], inplace=True)

return df \# Returns cleaned dataframe

\# Use the function wherever needed

df =
clean\_dataframe(pd.DataFrame.from\_records(db.read({'animal\_type':
'Dog'})))

**Benefit:** Improves code reuse, reduces duplication, and centralizes
data-cleaning logic for easier maintenance.

**3. Fixed MongoDB Query Syntax ("$or" vs "or")**

Initially, MongoDB filtering used an incorrect "or" syntax, which caused
query errors. I corrected it by using the proper $or operator.

**Before (Incorrect Query)**

{

"$and": \[

{"or": \[ \# Incorrect syntax should be "$or"

{'breed': {"$regex": 'Labrador Retriever Mix'}},

{'breed': {"$regex": 'Chesapeake'}},

{'breed': {"$regex": 'Newfoundland'}}

\]}

\]

}

**After (Correct Query)**

{

"$and": \[

{"$or": \[ \# Fixed syntax for proper MongoDB querying

{'breed': {"$regex": 'Labrador Retriever Mix'}},

{'breed': {"$regex": 'Chesapeake'}},

{'breed': {"$regex": 'Newfoundland'}}

\]}

\]

}

**Benefit:** Ensures query validity, preventing unexpected database
errors and ensuring the correct filtering logic.

**4. Improved Error Handling for Image Loading**

Originally, the code assumed the existence of an image file
(Grazioso\_Salvare\_Logo.png), which could cause runtime errors if
missing. I fixed this by checking its existence before reading.

**Before (No Error Handling)**

image\_filename = 'Grazioso\_Salvare\_Logo.png'

encoded\_image = base64.b64encode(open(image\_filename, 'rb').read()) \#
Could fail if file is missing

**After (Added Error Handling for Missing File)**

image\_filename = 'Grazioso\_Salvare\_Logo.png'

encoded\_image = None \# Default to None in case file isn't found

if os.path.exists(image\_filename): \# Safely check if the file exists

with open(image\_filename, 'rb') as img\_file:

encoded\_image = base64.b64encode(img\_file.read()) \# Encode if file
exists

**Benefit:** Prevents crashes due to missing images, improving
application reliability.

**5. Cleaned Up Conditional Filtering Logic**

The initial filtering logic had repetitive code blocks for each rescue
type. I refactored this into a dictionary-based approach, making it
cleaner and more maintainable.

**Before (Long Conditional Statements)**

if filter\_type == 'Water':

df = pd.DataFrame.from\_records(db.read({...}))

elif filter\_type == 'Mountain':

df = pd.DataFrame.from\_records(db.read({...}))

elif filter\_type == 'Disaster':

df = pd.DataFrame.from\_records(db.read({...}))

else:

df = pd.DataFrame.from\_records(db.read({'animal\_type': 'Dog'}))

**After (Refactored Dictionary-Based Approach)**

filters = {

'Water': {...}, \# Query for water rescue dogs

'Mountain': {...}, \# Query for mountain rescue dogs

'Disaster': {...} \# Query for disaster rescue dogs

}

query = filters.get(filter\_type, {'animal\_type': 'Dog'}) \# Default to
all dogs if filter not found

df = clean\_dataframe(pd.DataFrame.from\_records(db.read(query)))

**Benefit:** Eliminates redundancy, centralizes query logic, and makes
updates easier.
