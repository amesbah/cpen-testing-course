Defects4j (Java 11) assignments


1. Bug understanding
  3 bugs unique for each group
    at least one multi-hunk
2. Coverage analysis (line, branch)， test generation (create / generate more test cases to cover the gaps, both manually and with AI)
3. Mutation analysis for that class and its test cases 
4. Program analysis: CFG generation, write code to get slices
  Use https://github.com/IBM/tree-sitter-codeviews to get the CFG, DFG
  Parse the json files of CFG and DFG and create slices for the buggy statement
5. Fix the bug: 
  a. manually
  b. using AI (with just code)
  c. using AI with slices in the prompt
  d. compare with developer's fix
