# Assignment 1: Defects4J Bug Analysis and Testing Gap Investigation

## Overview

Students will conduct a comprehensive analysis of a real bug from the Defects4J dataset, investigating why the bug was not caught by the original test suite and what testing approaches could have detected it.

## Learning Objectives

- Understand how real bugs manifest in production codebases
- Analyze the relationship between test coverage and bug detection
- Investigate root causes of testing failures in real-world scenarios
- Develop skills in systematic bug analysis and testing gap assessment

## Assignment Structure

### Setup and Bug Assignment

**Group Assignment**: Each group of 2 students receives 3 randomly assigned bugs from different Defects4J projects.

**Assignment Distribution**: See `bug-assignments.md` for complete group assignments (Groups 1-19).

**Sample Group Assignment (Group 1)**:
- **Bug 1**: Commons-Lang #15
- **Bug 2**: Math #42
- **Bug 3**: Gson #8

**Available Projects**: Commons-Lang, Commons-Math, Gson, Chart, Time, Closure, Mockito, Cli, Codec, Collections, Compress, Csv, JacksonCore, JacksonDatabind, JacksonXml, Jsoup, JxPath

**Prerequisites**: Complete Defects4J setup following `defects4j-setup.md` before beginning analysis.

### Part 1: Bug Understanding and Reproduction (Week 1)

#### Step 1: Environment Setup and Checkout

**Important**: Before starting, ensure you have completed the Defects4J setup from `defects4j-setup.md`, including:
- Java 11 installation
- Defects4J framework installation
- Timezone configuration (`export TZ=America/Los_Angeles`)

**Checkout Process for Each Bug**:
```bash
# Create organized workspace
mkdir ~/defects4j-workspace/assignment1
cd ~/defects4j-workspace/assignment1

# Example: Group 1 checking out their first bug (Commons-Lang #15)
defects4j checkout -p Lang -v 15b -w Lang-15-buggy

# Navigate to project and compile
cd Lang-15-buggy
defects4j compile

# Run the failing test(s)
defects4j test
```

**Project Name Mappings** (use these for checkout commands):
- Commons-Lang → `Lang`
- Commons-Math → `Math`
- Chart → `Chart`
- Time → `Time`
- All other mappings found in `bug-assignments.md`

#### Step 2: Bug Manifestation Analysis

**Required Documentation** (for each of your 3 assigned bugs):

1. **Bug Description**:
   - What is the expected behavior vs. actual behavior?
   - Under what conditions does the bug manifest?
   - What are the symptoms visible to end users?

2. **Failing Test Analysis**:
   - Which specific test(s) fail?
   - What do the failure messages tell us?
   - Are the failing tests unit tests, integration tests, or system tests?

3. **Bug Reproduction**:
   - Document the exact steps to reproduce the bug
   - Create a minimal example that demonstrates the bug
   - Identify the specific inputs that trigger the bug

**Multi-Bug Analysis Strategy**:
- Complete initial analysis for all 3 bugs in Week 1
- Compare bug types and manifestation patterns
- Select the most educational bug for deep dive analysis in Week 2

#### Step 3: Root Cause Investigation

**Required Analysis**:

1. **Code Investigation**:
   - Identify the exact line(s) of code where the bug occurs
   - Trace the execution path that leads to the bug
   - Understand the logic error or incorrect assumption

2. **Context Analysis**:
   - What is the purpose of the buggy code within the larger system?
   - What were the developers likely trying to accomplish?
   - Are there any comments or documentation that reveal intent?

3. **Bug Classification**:
   - What type of bug is this? (logic error, boundary condition, null pointer, etc.)
   - Is this an edge case or a fundamental flaw?
   - How severe would this bug be in production?

### Part 2: Test Coverage Analysis (Week 2)

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

### Part 3: Testing Gap Analysis and Recommendations (Week 2)

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

## Deliverables

### Written Report (10-13 pages)

**Section 1: Multi-Bug Overview** (2-3 pages)
- Brief analysis of all 3 assigned bugs
- Bug type classification and comparison
- Rationale for selecting primary bug for deep analysis

**Section 2: Primary Bug Analysis** (4-5 pages)
- Detailed bug description and manifestation
- Root cause analysis with code evidence
- Bug classification and severity assessment

**Section 3: Coverage and Test Analysis** (3-4 pages)
- Coverage measurement results and analysis
- Test suite structure and design assessment
- Gap identification and testing failure analysis

**Section 4: Recommendations and Insights** (2-3 pages)
- Specific test cases that would catch the primary bug
- Broader testing strategy improvements
- Cross-bug patterns and lessons learned

### Code Deliverables
- Minimal bug reproduction examples for all 3 bugs
- Proposed test cases for primary bug (implemented and validated)
- Coverage analysis scripts/reports for primary bug
- Organized workspace with all 3 bug checkouts

### Presentation (15 minutes)
- Brief overview of all 3 bugs (3 minutes)
- Detailed analysis of primary bug with live demonstration (8 minutes)
- Coverage analysis results and testing insights (4 minutes)
- Q&A and cross-bug pattern discussion

## Evaluation Criteria (100 points)

### Multi-Bug Analysis and Primary Bug Selection (25 points)
- **Quality of initial analysis across all 3 bugs** (10 points)
- **Appropriate selection and justification of primary bug** (5 points)
- **Cross-bug comparison and pattern identification** (10 points)

### Primary Bug Understanding and Analysis (35 points)
- **Accuracy of root cause identification** (15 points)
- **Depth of code analysis and evidence** (12 points)  
- **Quality of bug reproduction and demonstration** (8 points)

### Coverage and Test Analysis (25 points)
- **Correctness of coverage measurements** (8 points)
- **Quality of test suite analysis** (12 points)
- **Insight into why the bug was missed** (5 points)

### Testing Recommendations and Communication (15 points)
- **Effectiveness of proposed test cases** (8 points)
- **Quality of testing strategy recommendations** (4 points)
- **Clarity of presentation and communication** (3 points)

## Tips for Success

1. **Start with the failing test** - understand what it's trying to verify
2. **Use debugging tools** - step through code execution to understand flow
3. **Read project documentation** - understand the intended behavior
4. **Compare buggy vs. fixed versions** - see exactly what changed
5. **Think like the original developer** - what assumptions might they have made?
6. **Focus on prevention** - what testing approach prevents this category of bugs?
7. **Document your process** - keep detailed notes of your investigation steps
8. **Validate everything** - ensure proposed test cases actually work as expected
9. **Start early** - setup can take time, and real bugs are complex to analyze
10. **Ask for help** - use office hours and Piazza for technical difficulties

## Timeline

- **Week 1**: 
  - Complete Defects4J setup following `defects4j-setup.md`
  - Checkout and analyze all 3 assigned bugs 
  - Select primary bug for deep dive analysis
  - Complete root cause investigation for primary bug

- **Week 2**: 
  - Detailed coverage analysis and test investigation for primary bug
  - Develop and validate proposed test cases
  - Write comprehensive report
  - Prepare presentation with live demonstration

- **End of Week 2**: Report submission and presentations

## Additional Resources

- **Setup Guide**: `defects4j-setup.md` - Complete before starting
- **Bug Assignments**: `bug-assignments.md` - Your group's specific bugs  
- **Defects4J Documentation**: https://github.com/rjust/defects4j
- **Course Forum**: Piazza for technical questions and clarifications

## Academic Integrity

- **Collaboration**: You may collaborate freely within your assigned group
- **External Help**: You may seek help understanding tools and techniques, but all analysis must be your own
- **AI Tools**: If you use AI tools for background research or coding assistance, you must clearly document and attribute their use
- **Attribution**: All sources, including AI assistance, must be properly cited in your report
- **Original Work**: Your analysis, insights, and conclusions must be original and based on your own investigation

This multi-bug approach helps you develop pattern recognition skills and systematic analysis capabilities that are essential for professional software testing and debugging.