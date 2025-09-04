Defects4j (Java 11) assignments


1. Bug understanding
  3 bugs unique for each group
    at least one multi-hunk
2. Coverage analysis (line, branch)
3. Test generation (create / generate more test cases to cover the gaps, both manually and with AI)
4. Mutation analysis for that class and its test cases 
5. Program analysis: CFG generation, write code to get slices
  Use https://github.com/IBM/tree-sitter-codeviews to get the CFG, DFG
  Parse the json files of CFG and DFG and create slices for the buggy statement
6. Fix the bug: 
  a. manually
  b. using AI (with just code)
  c. using AI with slices in the prompt
  d. compare with developer's fix
