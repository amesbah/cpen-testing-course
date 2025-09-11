# Assignment 1: Defects4J Bug Analysis and Understanding

## Overview

Students will conduct a comprehensive analysis of a real bug from the Defects4J dataset, focusing on how the bug manifests and how it was exposed by the triggering test case included in the benchmark.

## Learning Objectives

- Understand how real bugs manifest in production codebases
- Analyze the relationship between test coverage and bug detection
- Investigate root causes of testing failures in real-world scenarios
- Develop skills in systematic bug analysis and testing gap assessment

## Assignment Structure

### Setup and Bug Assignment

**Group Assignment**: Each group receives 3 randomly assigned bugs from different Defects4J projects.

**Assignment Distribution**: Each group will be given a private GitHub repository with the assigned bug ids. 

**Prerequisites**: Defects4J's repository is https://github.com/rjust/defects4j, Please complete Defects4J setup following its `README.md` before beginning analysis.

### Bug Understanding and Reproduction

#### Step 1: Environment Setup and Checkout

**Important**: Before starting, ensure you have completed the Defects4J setup, including:
- Java 11 installation
- Defects4J framework installation
- Timezone configuration (`export TZ=America/Los_Angeles`)

**Checkout Process for Each Bug**:
```bash
# Create organized workspace
mkdir -p ~/defects4j-workspace/assignment1
cd ~/defects4j-workspace/assignment1

# Example: Group 1 checking out their first bug (Commons-Lang #15)
defects4j checkout -p Lang -v 15b -w Lang-15-buggy

# Navigate to project and compile
cd Lang-15-buggy
defects4j compile

# Run the failing test(s)
defects4j test
```

#### Step 2: Bug Manifestation Analysis

**Required Documentation** (for each of your 3 assigned bugs):

1. **Failing Test Evidence**:
   - Which specific test(s) fail?
   - What do the failure messages tell us?
   - Are the failing tests unit tests, integration tests, or system tests?
   - What specific inputs or configurations trigger the failure?

2. **Bug Understanding**:
   - What is the expected behavior vs. actual behavior?
   - Under what conditions does the bug manifest? 
   - why didn’t the rest of the test suite reveal it earlier?
   - What are the symptoms visible to end users?

**Multi-Bug Analysis Strategy**:
- Complete initial analysis for all 3 bugs
- Compare bug types and manifestation patterns
- Pick one primary bug (most educational) for the deep-dive in Step 3

#### Step 3: Root Cause Investigation (deep-dive on the primary bug)

**Required Analysis**: Provide concrete code-level evidence.

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

## Deliverables

### Written Report

**Section 1: Multi-Bug Overview** 
- Brief analysis of all 3 assigned bugs
- Bug type classification and comparison
- Rationale for selecting primary bug for deep analysis

**Section 2: Primary Bug Analysis** 
- Detailed bug description and manifestation
- Root cause analysis with code evidence
- Bug classification and severity assessment

### Code Deliverables
- Organized workspace with all 3 bug checkouts
- Any helper scripts you used to reproduce/inspect (if any)

### Lab demonstration (5 minutes)
- Brief overview of all 3 bugs
- Detailed analysis of primary bug: show fault location and reasoning
- Q&A

## Evaluation Criteria (5 points total)

### Defects4J SetUp (1 point)
- **All 3 bugs checked out and reproducible (compile + test)**

### Multi-Bug Analysis and Primary Bug Selection (2 points)
- **Quality of initial analysis across all 3 bugs**
- **Appropriate selection and justification of primary bug**
- **Cross-bug comparison and pattern identification**

### Primary Bug Understanding and Analysis (2 points)
- **Accurate fault localization and root cause identification**
- **Depth of code analysis and evidence**
- **Clear explanation of why other tests missed it and how to prevent it**


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

## Additional Resources

- **Defects4J Documentation**: https://github.com/rjust/defects4j
- **Course Forum**: Piazza for technical questions and clarifications

## Academic Integrity

- **Collaboration**: You may collaborate freely within your assigned group
- **External Help**: You may seek help understanding tools and techniques, but all analysis must be your own
- **AI Tools**: If you use AI tools for background research or coding assistance, you must clearly document and attribute their use
- **Attribution**: All sources, including AI assistance, must be properly cited in your report
- **Original Work**: Your analysis, insights, and conclusions must be original and based on your own investigation

This multi-bug approach helps you develop pattern recognition skills and systematic analysis capabilities that are essential for professional software testing and debugging.
