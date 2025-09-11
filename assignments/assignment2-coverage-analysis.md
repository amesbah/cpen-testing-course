# Assignment 2: Code Coverage and Test generation

### Part 1: Test Coverage Analysis

#### Step 1: Coverage Measurement

**Run Coverage Analysis**:
```bash
# Generate coverage report for your selected primary bug
defects4j coverage

# For specific test classes (optional)
defects4j coverage -t <TEST_CLASS>

# Export coverage data for analysis
defects4j export -p dir.bin.classes
defects4j export -p dir.bin.tests

# Use gradle/maven with JaCoCo plugin for detailed reports
```

**Important**: Focus detailed coverage analysis on your chosen primary bug, but collect basic coverage data for all 3 bugs for comparative analysis.

**Required Measurements**:

1. **Overall Coverage Metrics**:
   - Statement coverage percentage
   - Branch coverage percentage
   - Method coverage percentage

2. **Bug-Specific Coverage**:
   - Is the buggy code covered by any tests?
   - If covered, which tests execute the buggy code?
   - If not covered, why is this code path missed?

3. **Coverage Analysis**:
   - What is the coverage of the file/class containing the bug?
   - Are there systematic gaps in test coverage?
   - How does coverage correlate with bug location?

#### Step 2: Test Suite Investigation

**Test Suite Analysis**:

1. **Existing Test Structure**:
   - How many tests exist for the buggy component?
   - What testing approaches are used (unit, integration, boundary testing)?
   - Are there any tests that almost catch the bug?

2. **Test Design Assessment**:
   - Do existing tests cover the input space adequately?
   - Are boundary conditions tested?
   - Are negative test cases (error conditions) tested?
   - What testing patterns/frameworks are used?

3. **Gap Identification**:
   - What specific test cases are missing?
   - Why weren't these test cases written originally?
   - What assumptions did the original developers make?

### Part 2: Testing Gap Analysis and Recommendations (Week 2)

#### Step 1: Root Cause of Testing Failure

**Analysis Questions to Address**:

1. **Why Was the Bug Missed?**
   - Was it a coverage gap (code not executed by tests)?
   - Was it an oracle problem (code executed but wrong behavior not detected)?
   - Was it an input space problem (right code, wrong test inputs)?
   - Was it a test design problem (inappropriate testing strategy)?

2. **Testing Methodology Analysis**:
   - What testing approach would have caught this bug?
   - Were the original developers following good testing practices?
   - What were the likely time/resource constraints affecting testing?

3. **Systematic vs. Random Failure**:
   - Is this an isolated oversight or part of a systematic testing weakness?
   - Are there similar untested scenarios in the codebase?

#### Step 2: Proposed Testing Improvements

**Design Specific Test Cases**:

1. **Bug-Catching Test**:
   - Write a specific test case that would have caught this bug
   - Demonstrate that your test fails on the buggy version
   - Verify that your test passes on the fixed version
   - **Testing with Fixed Version**:
     ```bash
     # Checkout the fixed version to validate your test
     defects4j checkout -p <PROJECT> -v <BUG_ID>f -w <PROJECT>-<BUG_ID>-fixed
     cd <PROJECT>-<BUG_ID>-fixed
     defects4j compile
     # Run your new test here
     ```

2. **Comprehensive Test Enhancement**:
   - Propose additional test cases for similar scenarios
   - Design tests that would catch related bugs
   - Consider boundary conditions and edge cases

3. **Testing Strategy Recommendations**:
   - What changes to the overall testing approach would prevent similar bugs?
   - What tools or techniques could improve test effectiveness?
   - How should the test suite be restructured or enhanced?
