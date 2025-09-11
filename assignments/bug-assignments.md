# Assignment 1: Defects4J Bug Assignments by Group

## Group Bug Assignments

Each group of 2 students has been randomly assigned 3 bugs from different Defects4J projects. Groups should analyze all 3 bugs.

### Group 1
- **Bug 1**: _Commons-Lang #15_
- **Bug 2**: Math #42
- **Bug 3**: _Gson #8_

### Group 2
- **Bug 1**: Chart #11
- **Bug 2**: Time #19
- **Bug 3**: _Closure #74_ 

### Group 3
- **Bug 1**: _Mockito #25_
- **Bug 2**: _Cli #7_
- **Bug 3**: Collections #4

### Group 4
- **Bug 1**: Codec #18
- **Bug 2**: Commons-Lang #33
- **Bug 3**: _JacksonCore #12_

### Group 5
- **Bug 1**: _Math #35_
- **Bug 2**: Compress #21
- **Bug 3**: _Gson #14_

### Group 6
- **Bug 1**: Csv #9
- **Bug 2**: Chart #26
- **Bug 3**: _Time #12_

### Group 7
- **Bug 1**: JacksonDatabind #45
- **Bug 2**: Jsoup #13
- **Bug 3**: _Commons-Lang #41_

### Group 8
- **Bug 1**: _Closure #89_
- **Bug 2**: _Mockito #17_
- **Bug 3**: Math #58

### Group 9
- **Bug 1**: _Collections #25_
- **Bug 2**: JacksonXml #3
- **Bug 3**: Cli #15

### Group 10
- **Bug 1**: _Codec #11_
- **Bug 2**: _Compress #35_
- **Bug 3**: Chart #9

### Group 11
- **Bug 1**: Gson #16
- **Bug 2**: _JxPath #7_
- **Bug 3**: _Time #26_

### Group 12
- **Bug 1**: _Math #71_
- **Bug 2**: Csv #14
- **Bug 3**: Jsoup #89

### Group 13
- **Bug 1**: _Commons-Lang #62_
- **Bug 2**: JacksonCore #26
- **Bug 3**: Mockito #33

### Group 14
- **Bug 1**: Closure #107
- **Bug 2**: Collections #28
- **Bug 3**: _Compress #47_

### Group 15
- **Bug 1**: _Chart #21_
- **Bug 2**: _JacksonDatabind #78_
- **Bug 3**: Codec #17

### Group 16
- **Bug 1**: Time #4
- **Bug 2**: Cli #29
- **Bug 3**: _Math #86_

### Group 17 (backup)
- **Bug 1**: Gson #12
- **Bug 2**: JxPath #14
- **Bug 3**: _Csv #8_

### Group 18 (backup)
- **Bug 1**: _Jsoup #52_
- **Bug 2**: _Commons-Lang #27_
- **Bug 3**: _JacksonXml #6_

### Group 19 (backup)
- **Bug 1**: Collections #21
- **Bug 2**: _Compress #29_
- **Bug 3**: _Closure #115_

## Assignment Instructions

### For Each Assigned Bug:

1. **Checkout Command**:
   ```bash
   defects4j checkout -p <PROJECT> -v <BUG_ID>b -w /path/to/<PROJECT>-<BUG_ID>
   ```

2. **Example for Group 1, Bug 1**:
   ```bash
   defects4j checkout -p Lang -v 15b -w /path/to/Lang-15
   ```

### Project Name Mappings:
- **Commons-Lang** → `Lang`
- **Commons-Math** → `Math` 
- **Chart** → `Chart`
- **Time** → `Time`
- **Closure** → `Closure`
- **Mockito** → `Mockito`
- **Cli** → `Cli`
- **Collections** → `Collections`
- **Codec** → `Codec`
- **Compress** → `Compress`
- **Csv** → `Csv`
- **JacksonCore** → `JacksonCore`
- **JacksonDatabind** → `JacksonDatabind`
- **JacksonXml** → `JacksonXml`
- **Jsoup** → `Jsoup`
- **JxPath** → `JxPath`
- **Gson** → `Gson`
