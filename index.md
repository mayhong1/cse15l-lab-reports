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

Description: Every line that contains the word "California" inside the 911report/ directory is printed out. This is because egrep prints out all instances of the given pattern; here, I specified the pattern to be "California" and for the command to search inside the 911report/ directory.

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

Descrption: Every line that contains the phrase "NIAAA" in the DraftRecom-PDF.txt file is printed along with the contents of the line. The reasoning behind this is that egrep prints out all instances of a specified pattern, and here I specified the pattern to be "NIAAA" and to look inside DraftRecom-PDF.txt.

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

Description: Every line that contins the phrase "United States" in the ffm.txt file is printed. This is because sed can search for specific patterns and print them out; here, I specified the pattern to be "United States" and to look inside "ffm.txt". The "-n" supresses automatic printing, and the "\p" tells the computer to print out every line that contains "United States".

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

Description: Every line that has the phrase "smoking" in the 1468-6708-3-1.txt file is printed. The command indicates for the computer to search for the phrase "United States" inside "ffm.txt" and print out the lines where the phrase appears.

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

Description: Every line that has the phrase "New York" in chapter-9.txt is printed. awk can print out instances of a pattern: here, "New York" is printed because of the "{ print }". In the command, it is specified to do this with the file chapter-9.txt.

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

Description: Every line that has the phrase "Illinois" in Annual_Fee.txt is printed. awk can print out instances of a pattern: here, "Illinois" is printed because of the "{ print }". In the command, it is specified to do this with the file Annual_Fee.txt.

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

Description: Every line that contains the phrase "lawyer" in Barnes_new_job.txt is printed. fgrep works similarly to grep, printing out instances of a pattern. With this commmand, the pattern to search for is specified as "lawyer" and the file to search in is specified as "Barnes_new_job.txt".

#### fgrep Example 2

Working Directory: ~/OneDrive/Desktop/CSE 15L/LabWeek5/docsearch/technical/plos

Command: `fgrep "nations" journal.pbio.0020001.txt`

Output: 
```
them. There are now examples in which research on priority areas for the developing nations
direction. The extremely high scientific productivity of many developing nations, corrected
to the sciences will be an excellent investment by developing nations in terms of
```

Description: Every line that contains the phrase "nations" in journal.pbio.0020001.txt is printed. fgrep works similarly to grep, printing out instances of a pattern. With this commmand, the pattern to search for is specified as "nations" and the file to search in is specified as "journal.pbio.0020001.txt".

## Sources Cited:
I found all these commmands through ChatGPT. Here is the link to my ChatGPT history, which contains all my inputs to ChatGPT along with ChatGPT's outputs: https://chat.openai.com/share/212f8a1f-8ef5-400f-8ee7-b3dca9615eae
