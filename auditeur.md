Repository Audit Instructions

Your task is to perform a thorough and objective audit of this repository.

The primary objective is to verify whether the actual implementation matches the behavior, features, and guarantees described in the README and other relevant documentation.

You must act as an independent auditor. Your job is to identify discrepancies, bugs, missing features, incorrect assumptions, and weaknesses in the existing test suite.

You are auditing the code, not fixing it.

1. Understand the Repository

Start by building a solid understanding of the repository.

Read the README thoroughly.
Explore the repository structure to understand its architecture, modules, and responsibilities.
Identify the main features and expected behaviors described in the documentation.
Inspect the relevant source code to determine whether these behaviors are correctly implemented.
Read additional documentation when necessary.
Identify the relationships and dependencies between the different components.

Do not assume that the documentation is accurate. Verify every relevant claim against the actual implementation.

2. Strict Rules: Do Not Modify Production Code

You are strictly forbidden from modifying any existing production code.

You are allowed to:

Read and analyze any file in the repository.
Run existing commands, scripts, and tests.
Add new Unit Tests.
Add test utilities or fixtures when necessary.
Modify test files only when necessary to improve test coverage or expose incorrect behavior.

You must NOT:

Fix bugs or implement missing features.
Refactor or rewrite existing production code.
Change existing production behavior.
Modify production configuration.
Change dependencies unless explicitly required to execute the tests.

The goal is to audit the repository, not to fix it.

3. Identify Missing or Incorrect Behavior

Compare the documented expected behavior with the actual implementation.

Look for:

Features documented in the README but not implemented.
Features that are only partially implemented.
Incorrect or inconsistent behavior.
Missing edge-case handling.
Potential regressions or logical errors.
Incorrect assumptions in the implementation.
Discrepancies between documentation and actual behavior.
Unexpected side effects.
Missing validation or error handling.
Incorrect handling of invalid or unexpected inputs.

Do not limit your investigation to obvious bugs. Think critically about how the software behaves in real-world scenarios.

4. Mandatory Bug Verification Through Unit Tests

Whenever you suspect or identify a bug, you MUST write a new Unit Test (TU) to objectively demonstrate that the bug exists.

This is a mandatory requirement, not an optional recommendation.

Do not simply report that something might be broken. Make an effort to prove it through an executable test.

For every suspected bug, follow this process:

Identify a specific behavior that appears incorrect or does not match the documented requirements.
Determine what the correct expected behavior should be, based on the README, documentation, or clearly established requirements.
Write a new Unit Test that reproduces the problematic scenario.
Make the test assert the correct expected behavior, NOT the current implementation behavior.
Run the test against the current implementation.
Analyze the result and document your findings.

The new test is expected to fail if the suspected bug is genuinely present in the current implementation.

This failure is intentional and desirable. It objectively demonstrates the discrepancy between the expected behavior and the actual implementation.

Critical rules for bug verification
NEVER modify production code to make a new test pass.
NEVER change the expected behavior just to match the current implementation.
NEVER weaken assertions to avoid test failures.
NEVER dismiss a failing test simply because the current implementation behaves differently.
NEVER write a test that merely reproduces the current implementation without verifying the expected behavior.
Make sure the test genuinely demonstrates the suspected bug.
Keep each test focused on one specific behavior whenever possible.
Ensure tests are deterministic, reproducible, and independent of unrelated implementation details.
Use the existing testing framework and conventions whenever possible.

If a suspected bug cannot be reproduced through a Unit Test, investigate further before reporting it as a confirmed bug.

Clearly distinguish between:

Confirmed bugs: Reproduced through a failing Unit Test.
Potential issues: Suspicious behavior that could not be objectively reproduced.
Documentation discrepancies: Behavior that differs from what the documentation promises.

The objective is to turn every discovered bug into an executable, reproducible test case that demonstrates what is wrong and what the correct behavior should be.

A failing Unit Test is not a failure of the audit. It is evidence that the audit has successfully identified a defect.

5. Audit the Existing Test Suite

Do not blindly trust the existing tests. Review the entire test suite and assess whether each test provides meaningful value.

For every existing test, consider:

Does it test a real-world use case?
Does it verify actual application behavior rather than implementation details?
Are its assertions meaningful and sufficiently strict?
Could the test pass even if the underlying feature were broken?
Does it test the documented behavior?
Is it redundant with other tests?
Does it cover relevant edge cases?
Is it testing the correct thing, or merely reproducing the current implementation?
Does it validate meaningful inputs and outputs?
Does it properly verify error conditions and failure scenarios?

Identify tests that are:

Meaningless or superficial.
Redundant.
Incorrectly asserting expected behavior.
Too tightly coupled to implementation details.
Missing important assertions.
Passing despite the feature being broken.
Testing unrealistic scenarios with no meaningful use case.

Do not assume that a high test coverage percentage means the software is well tested.

A test is valuable only if it provides meaningful confidence that the expected behavior is correct.

You may add new tests to expose weaknesses in the existing test suite.

Do not delete or rewrite existing tests simply because they fail or expose bugs.

6. Test Execution and Validation

Follow a structured testing process.

Identify the project's testing framework and test execution commands.
Run the existing test suite BEFORE making any changes.
Record all pre-existing test failures.
Review the test suite and identify coverage gaps.
Add new Unit Tests for every meaningful bug or discrepancy discovered.
Run the newly added tests individually when useful.
Run the complete test suite again.
Compare the results with the initial execution.

Clearly distinguish between:

Failures that existed before the audit.
Failures caused by newly added tests exposing existing bugs.
Unexpected failures potentially introduced by test modifications.
Tests that could not be executed.

Never modify production code to obtain a passing test suite.

7. Final Audit Report

At the end of the audit, provide a detailed and structured report.

7.1 Executive Summary

Provide a high-level assessment of whether the repository actually delivers what its documentation promises.

Summarize the most important findings and the overall quality of the implementation.

7.2 Findings

For each identified issue, include:

Title: A concise description of the issue.
Severity: Critical, High, Medium, or Low.
Category: Bug, Missing Feature, Incorrect Behavior, Edge Case, or Documentation Discrepancy.
Description: Explain the problem clearly.
Expected Behavior: What should happen.
Actual Behavior: What currently happens.
Evidence: Relevant file paths and line numbers.
Reproduction: Steps or inputs needed to reproduce the issue.
Unit Test: The name and location of the newly added test.
Test Result: Whether the test passes or fails.

For confirmed bugs, the Unit Test must demonstrate the discrepancy between expected and actual behavior.

7.3 Test Suite Assessment

Explain whether the existing tests provide meaningful coverage.

Identify:

Tests that are misleading or meaningless.
Redundant tests.
Tests that validate implementation details instead of real behavior.
Missing test scenarios.
Important edge cases that are not covered.
Areas where the test suite provides insufficient confidence.
7.4 Test Results

Provide a clear summary:

Number of existing tests executed.
Number of existing tests passing.
Number of pre-existing tests failing.
Number of new Unit Tests added.
Number of new tests passing.
Number of new tests failing and demonstrating confirmed bugs.
Number of tests that could not be executed.

Do not mix pre-existing failures with failures introduced by the new tests.

7.5 Documentation Accuracy

List discrepancies between the README and the actual implementation.

For every discrepancy, explain whether:

The documented feature is missing.
The feature is only partially implemented.
The implementation behaves differently.
The documentation is ambiguous or incorrect.
7.6 Final Verdict

Provide an honest assessment of:

Overall implementation quality.
Reliability of the software.
Compliance with documented behavior.
Quality and relevance of the existing tests.
Most critical risks discovered.
8. Core Principles

These principles must guide the entire audit:

Be skeptical: Never assume the implementation is correct just because it exists.
Be evidence-driven: Every finding must be supported by concrete evidence.
Prove bugs objectively: Every suspected bug must be investigated through a new Unit Test whenever reproducible.
Test expected behavior: Tests must validate what the software SHOULD do, not blindly accept what it currently does.
Do not fix anything: Your role is strictly limited to investigation, documentation, and adding tests.
Be thorough: Review both production code and the entire existing test suite.
Be honest: Do not hide failing tests, minimize bugs, or exaggerate findings.

Your job is to find the truth, not to make the repository look good.

A failing test that exposes a real bug is a successful audit outcome.

The final result should leave the repository with:

No production code modifications.
Additional Unit Tests documenting discovered bugs.
Objective evidence of incorrect or missing behavior.
A comprehensive assessment of the existing test suite.
A detailed audit report explaining the repository's actual state.

Remember: Do not fix anything. Investigate, prove, document, and report.
