# Part 1

## Failure Inducing & Non-Failure Inducing Input:

```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
  // this test induces failure
  @Test
  public void testReverseInPlace1() {
    int [] input = {1, 2, 3, 4};
    int [] expected = {4, 3, 2, 1};
    ArrayExamples.reverseInPlace(input);
    assertArrayEquals(expected, input);
  }
  // this test does not induce failure
  @Test
  public void testReverseInPlace() {
    int [] input = {3, 2, 2, 3};
    int [] expected = {3, 2, 2, 3};
    ArrayExamples.reverseInPlace(input);
    assertArrayEquals(expected, input);
  }

}
```

##The symptom:
![screenshot1](screenshot1.png)

## The bug:

### Before Fixing:
![screenshot2](screenshot2.png)

### After Fixing:
![screenshot3](screenshot3.png)

In the before screenshot, the values in the array were being directly modified. Once `i` reached `arr.length/2`, the first half of the array has been modified. So, when you set the values in the second half of the array to the values in the first half of the array, those values are the modified values (not the original values), resulting in the bug. To fix this, you could create a copy of the array. Then, in each iteration of the loop you would set `arr[i]` to `arrCopy[arr.length - 1 - i]`; in this version, the values are the original values because you are setting it to an original version of the array and not a modified version.

# Part 2

## Alternatives to `grep`

### egrep

#### egrep Example 1
Working directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical

Command: `egrep "California" 911report/*`

Output: 
```
911report/chapter-11.txt:                California went on the watch for his like.
911report/chapter-13.4.txt:                chemistry, from California State University, Sacramento. Sufaat did not start on the
911report/chapter-13.4.txt:                reasons for sending Hazmi and Mihdhar to California do not seem especially
911report/chapter-13.4.txt:                explanation for the California destination. The possibility that the two hijackers
911report/chapter-13.4.txt:                addresses-one in the United States ("possibly in California") and one in South
911report/chapter-13.4.txt:                California." Intelligence report, interrogation of KSM, June 15, 2004.
911report/chapter-13.4.txt:                acclimate the hijackers to the United States, particularly San Diego, California."
911report/chapter-13.4.txt:                California, but Atta told him to discontinue this effort. Intelligence report,
911report/chapter-13.4.txt:                his training in California, see FBI report of investigation, interview of Adnan
911report/chapter-13.5.txt:            85. Hazmi and Mihdhar used their true names to obtain California driver's licenses
911report/chapter-3.txt:                California (UNOCAL) to build a pipeline across the country. While there was probably
911report/chapter-5.txt:                became the primary target. For similar reasons, California also became a target for
911report/chapter-5.txt:                headquarters, nuclear power plants, and the tallest buildings in California and the
911report/chapter-5.txt:                such as San Diego and Long Beach, California; brochures for schools; and airline
911report/chapter-6.txt:            One of the 16, Raed Hijazi, had been born in California to Palestinian parents; after
911report/chapter-6.txt:                spending his childhood in the Middle East, he had returned to northern California,
911report/chapter-6.txt:                that Hijazi had lived in California and driven a cab in Boston and that Deek was a
911report/chapter-7.txt:            Why Hazmi and Mihdhar came to California, we do not know for certain. Khalid Sheikh
911report/chapter-7.txt:                Mohammed (KSM), the organizer of the planes operation, explains that California was
911report/chapter-7.txt:                that al Qaeda had any agents in Southern California. We do not credit this
911report/chapter-7.txt:                California, so that they could begin pilot training as soon as possible. KSM claims
911report/chapter-7.txt:                Culver City, one of the most prominent mosques in Southern California.
911report/chapter-7.txt:                fellow inmates at a California prison in September- October 2003 that he had known
911report/chapter-7.txt:                rest of his time in California, until mid-December; he would then leave for Arizona
911report/chapter-7.txt:                Translating between English and Arabic, he assisted them in obtaining California
911report/chapter-7.txt:                of California declined to prosecute him on charges arising out of his alleged
911report/chapter-7.txt:                impression is that soon after arriving in California, Hazmi and Mihdhar sought out
911report/chapter-7.txt:                child arrived, he could stand life in California no longer. In late May and early
911report/chapter-7.txt:                California, and Arizona; and he briefly started at a couple of them before returning
911report/chapter-7.txt:                an English as a second language program in Oakland, California, which he had
911report/chapter-8.txt:                    California in the mid-1990s. A clandestine source said in 1998 that a Bin Ladin
911report/chapter-8.txt:            In June 2000, Mihdhar left California and returned to Yemen. It is possible that if,
```

#### egrep Example 2
Working directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical/government/alcohol_problems

Command: `egrep "NIAAA" DraftRecom-PDF.txt`

Output:
```
Longabaugh commented that an NIAAA effort to conduct research on
Mary Dufour described how NIAAA sets research priorities. To
NIAAA list of priorities. NIAAA has a National Advisory Council
research priorities, she said. Every three to five years, NIAAA
interventions, are on the list. NIAAA is a small institution with
```

### sed

#### sed Example 1

Working Directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical/government/Gen_Account_Office

Command: `sed -n '/United States/p' ffm.txt`

Output:
```
David M. Walker Comptroller General Of the United States
United States in Congress assembled,
SEC. 1. Section 5702 of title 5, United States Code, is amended
services procured by the United States or accepted pursuant to
SEC. 2. Section 404 of title 37, United States Code, is amended
5, United States Code (Per diem, employees traveling on official
37, United States Code (Travel and Transportation Allowances). This
```

#### sed Example 2

Working Directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical/biomed

Command: `sed -n '/smoking/p' 1468-6708-3-1.txt`

Output:
```
non-smoking older adults have investigated the association
include age, gender, smoking (never or former), history
squared, race, and smoking history (former or never), and
income and education, as well as age and former smoking,
for age, race, and previous smoking (columns 1 and 3), and
and smoking, averaged 6.0 years for women with a baseline
race, and former smoking. As mentioned above, the group
```

### awk

#### awk Example 1

Working Directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical/911report

Command: `awk '/New York/ { print }' chapter-9.txt`

Output:
```
The World Trade Center (WTC) complex was built for the Port Authority of New York and
New York City and America.
of America, New York City and specifically the World Trade Center had been the
to be impassable. Rescue efforts by the Fire Department of New York (FDNY) were
evacuated from the roof of the South Tower by New York Police Department (NYPD)
On 9/11, the principal first responders were from the Fire Department of New York,
the New York Police Department, the Port Authority Police Department (PAPD), and the
The New York Police Department.
The Fire Department of New York.
Between 1998 and 2000, fewer people died from fires in New York City than in any
the NYPD-and other data. A second purpose of the OEM was to improve New York City's
Emergencies in the City of New York." Its purpose was to eliminate "potential
Within minutes, New York City's 911 system was flooded with eyewitness accounts of
In the 17-minute period between 8:46 and 9:03 A.M. on September 11, New York City and
the Port Authority of New York and New Jersey had mobilized the largest rescue
New York City back on its feet.
the far more difficult task in New York. There was a single incident, and it was not
It is a fair inference, given the differing situations in New York City and Northern
the attacks on 9/11 was necessarily improvised. In New York, the FDNY, NYPD, the
and Control of Emergencies in the City of New York." The directive designated, for
the possibility of imminent additional terrorist attacks throughout New York City.
If New York and other major cities are to be prepared for future terrorist attacks,
In May 2004, New York City adopted an emergency response plan that expressly
```

#### awk Example 2

Working Directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical/government/media

Command: `awk '/Illinois/ { print }' Annual_Fee.txt `

Output: 
```
The Illinois Supreme Court on Friday hiked attorney registration
Trust Fund of Illinois, which disburses monies to legal aid
a commitment by the full court, and by attorneys in Illinois, to
There are now more than 57,000 active attorneys in Illinois.
Illinois State Bar Association and chair of the Lawyers Trust Fund,
their ability, thereby assisting the citizens of Illinois," Sheila
additional resources for such programs in Illinois through
LAP to establish offices in central and southern Illinois and
```

### fgrep

#### fgrep Example 1

Working Directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical/government/media

Command: `fgrep "lawyer" Barnes_new_job.txt` 

Output:
```
(unpaid) lawyer at the Atlanta Legal Aid Society.
lawyer for every 10,500 eligible poor people.
state's ethical rules include language indicating lawyers'
percent of the state's 23,598 active lawyers reported meeting the
people are served by only 24 percent of the state's lawyers.
counsel. Why? Because competent lawyers in the corporate practice
```

#### fgrep Example 2

Working Directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical/plos

Command: `fgrep "nations" journal.pbio.0020001.txt`

Output: 
```
them. There are now examples in which research on priority areas for the developing nations
direction. The extremely high scientific productivity of many developing nations, corrected
to the sciences will be an excellent investment by developing nations in terms of
```

## Sources Cited:
I found all these commmands through ChatGPT.

Here was more prompt: What are 4 commands that do the same thing as grep, and how do you use them?

Here was ChatGPT's answer: 
Sure, here are four commands that can perform similar tasks as `grep`, along with how to use them:

1. **egrep**:
   - Usage: `egrep [options] pattern [files]`
   - Example: `egrep "pattern" file.txt`
   - Explanation: `egrep` is similar to `grep`, but it supports extended regular expressions without needing to escape certain characters. You can use it to search for a pattern in one or more files.

2. **ack**:
   - Usage: `ack [options] pattern [files or directories]`
   - Example: `ack "pattern" file.txt`
   - Explanation: `ack` is a tool designed for programmers to search through code. It automatically ignores commonly ignored files and directories (like version control metadata), and highlights search results. It's particularly useful when searching through large codebases.

3. **ag (The Silver Searcher)**:
   - Usage: `ag [options] pattern [path]`
   - Example: `ag "pattern" file.txt`
   - Explanation: `ag` is a fast search tool optimized for codebases. It's written in C and is faster than both `grep` and `ack`. It ignores files and directories that are typically not relevant in programming projects, such as version control directories.

4. **rg (ripgrep)**:
   - Usage: `rg [options] pattern [path]`
   - Example: `rg "pattern" file.txt`
   - Explanation: `rg` is another fast search tool, written in Rust. It's designed to be faster than both `grep` and `ag`. It's particularly useful for searching through large codebases quickly and efficiently.

These commands work similarly to `grep` but may have different features or optimizations suited for specific tasks or environments.
