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

2. Business issues

3. Roles and Responsiblities

4. Test Deliverables

5. Test automation and tools

6. Testing metrics

7. Risks and mitigation

8. Defect Reporting

9. Change and configuration
