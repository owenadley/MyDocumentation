********************************
Testing
********************************

Test Methodologies/ Approach
==============================
White Box Testing
-----------------------------
Testing for the internals of a program or piece of software. In White Box testing, the tester is aware of the internal structure of the program and can excercise various inputs which will touch on different parts on the code.
Things like statment, function and branch coverage are targeted in white box testing to ensure all possible outcomes are covered and well tested. White Box testing is testing as a developer.

Black Box Testing
-----------------------------
Black Box testing is where the tester has zero knowledge of the internal structure or code of the program. The tester is only aware of what the program should do, but not how it does it. Black box testing is testing as a user.

Grey Box Testing
-----------------------------
Grey Box Testing is a combination of White and Black Box testing. The user has access to view the internal structure and the code within the program to design their test cases. However, the test is run from a Black Box or User level.
Grey Box testing is testing as a user, within internal knowledge of the code.

Testing Levels/ Types
==============================
Unit Testing
-----------------------------
Testing that covers and verifies a specific section of code, usually at the function level. In OO, this is usally a class. 
This is usually done by developers and falls into the White Box style of testing.

Integration Testing
-----------------------------
Testing that is done on software which is interfacing with other software, components, libraries, systems, etc.
The goal is to determine issues or bugs that arise when two programs interact with eachother is various manners.

System Testing
-----------------------------
Testing to cover and verify a full system to ensure it meets its requirements.

Acceptance Testing
-----------------------------
Testing which commonly falls towards the end of the testing and verifies the functionality works as designed, usually from a users perspective.
The goal is to ensure that both software and business requirements are met and the software is 'acceptable' for delivery.

Other types of testing
-----------------------------
Regression Testing
^^^^^^^^^^^^^^^^^^^^^^^
Testing done after a large code change or bug fix. The goal is to verify that the bug has been fixed and that the fix did not cause any other problems.

A/B Testing
^^^^^^^^^^^^^^^^^^^^^^^
Testing to verify whether a new change is better or worse than the previous version. This is commonly done from a UI perspective.

Performance Testing
^^^^^^^^^^^^^^^^^^^^^^^
Testing to verify that the system supports the performance requirements which were defined in the SRS.

Usability Testing
^^^^^^^^^^^^^^^^^^^^^^^
Testing to determine how well and easy the UI is to use. It should verify that the ease of use is in line with the pre-determined goal of usability.

Accessibility Testing
^^^^^^^^^^^^^^^^^^^^^^^
Testing to ensure that the system is compliant with various accessibility standards such as WAI-ARIA

Security Testing
^^^^^^^^^^^^^^^^^^^^^^^
Testing for integrity, confidentiality, etc within a system.

Test Strategy
==============================
A test strategy indicates how the objectives defined in the test plan will be accomplished.

Example Agile Test Strategy
-----------------------------

1. Scope and objectives

    The scope of this testing strategy includes determining how we will achieve the testing objectives indicated in the Test Plan.
    This includes who within the project will be responsible for what, the technologies that will be used for testing, bug tracking, deliverables and risk mitigation.


2. Business issues

    Various problems from 

3. Roles and Responsiblities

    All members of the project will be involved in testing process and help contribute our testing goals.
    On a biweekly scrum basis, new feature tickets will be created and assigned along with testing tickets which will be assigned for test cases (determined by new functionalities).

    QA testers will be implementing automated and manual test cases for the project. 

4. Test Deliverables

    On a biweekly basis, we need to ensure that each QA member has completed their assigned test cases and that 100% code coverage has been achieved.
    This will allow for continous testing on new features as they are rolled out on a biweekly basis.


5. Test automation and tools

    For White Box style testing we will be using the Java testing framework Mockito
    For Black Box and UI style testing we will be using Selenium Web Driver

    All tests will be ran when the project build runs through Travis CI. The goal is to maintain a pass percentage of 100%. If a test case fails, it takes immedeiate
    priority over other tickets and should be fixed as soon as possible.

    All bug and test cases will be created in JIRA and the ticket will be assigned to the designated tester. The tester can use this software
    to indicate the status of the test case and will be responsible for marking it as complete once it is passing.

6. Testing metrics

    Testing metrics will be gathered from both Travis CI along with JIRA.
    Metrics from JIRA can be used to determine how many test cases and completed vs not completed, how many test cases have been done by each team member
    How long it took to implement specific tests, along with how many tests have been completed based on feature.
    Metrics from Travis CI will indicate how often builds are passing or failing based on tests, when a new test causes a break in the system
    and the average rate of pass or fail for all test cases.

7. Risks and mitigation

    Determining risks is something that all members of the project will engage in. Every person is responsible for reporting any risks or possible mitiagation
    plans for exising risks. Risks will be indicated as JIRA tickets and the test cases associated with the risk will be bumbped to maximum priority.
    The project manager will get a notification for every new risk introduced through JIRA and will ultimately have the final call of how to approach it.
    Often this solution will be getting all hands on deck to solve the problem as fast as possible.

8. Defect Reporting

    Defect reporting will follow a similar pattern as risk mitigation. Everybody on the team is responsible for reporting defects
    which have been found in the system. These are often discovered during test cases, that a functionality does not work as expected.
    A defect ticket will be created in JIRA and will be either picked up by an assigned developer or it will be assigned in the next scrum meeting.
    Developers are responsible for fixing these defects, marking the defect as fixed on the JIRA ticket and then the QA team is responsible for Testing
    the new implementation.

9. Change and configuration

    Change and configuration will all be processed through GitHub. Pull requests will be made by team members and code will be reviewed by another developers
    before being comitted. The build should run atleast once a day (or night) to verify that new commits are working as intended and any build failures will be resolved
    the next working day by the QA team.
