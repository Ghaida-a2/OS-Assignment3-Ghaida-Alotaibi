# Assignment 3 - Complete Documentation

**Student Name**: [Ghaida Alotaibi]  
**Student ID**: [445052148]  
**Date Submitted**: [Submission Date]

---

## 🎥 VIDEO DEMONSTRATION LINK (REQUIRED)

> **⚠️ IMPORTANT: This section is REQUIRED for grading!**
> 
> Upload your 3-5 minute video to your **PERSONAL Gmail Google Drive** (NOT university email).
> Set sharing to "Anyone with the link can view".
> Test the link in incognito/private mode before submitting.

**Video Link**: [Paste your personal Gmail Google Drive link here]

**Video filename**: `[YourStudentID]_Assignment3_Synchronization.mp4`

**Verification**:
- [ ] Link is accessible (tested in incognito mode)
- [ ] Video is 3-5 minutes long
- [ ] Video shows code walkthrough and commits
- [ ] Video has clear audio
- [ ] Uploaded to PERSONAL Gmail (not @std.psau.edu.sa)

---

## Part 1: Development Log (1 mark)

Document your development process with **minimum 3 entries** showing progression:

### Entry 1 - [April 30, 10:00PM]
**What I implemented**: 
I began by comprehending the assignment specifications and examining the given code. I found shared resources that could result in a race issue, including counters and executionLog.
**Challenges encountered**: 
In a multithreaded setting, it was challenging to completely comprehend where racial circumstances could arise.
**How I solved it**: 
I went over the textbook's synchronization ideas and observed how several threads might access common variables.
**Testing approach**: 
I saw behavior by running the program without synchronization.
**Time spent**: 
30 min
---

### Entry 2 - [April 30, 10:30]
**What I implemented**: 
To safeguard shared counters (contextSwitchCount, completedProcessCount, totalWaitingTime), I built ReentrantLock.
**Challenges encountered**: 
Making sure locks are always released in order to prevent deadlocks
**How I solved it**: 
To ensure unlocking, I employed try-finally blocks.
**Testing approach**: 
To make sure counters update appropriately, several runs were tested.
**Time spent**: 
30 min
---

### Entry 3 - [April 30, 11:00]
**What I implemented**: 
I used the same lock to add synchronization to executionLog.
**Challenges encountered**: 
recognizing the reasons ArrayList is not thread-safe.
**How I solved it**: 
investigated concurrent collections and determined that locking was necessary.
**Testing approach**: 
ConcurrentModificationException was examined.
**Time spent**: 
30 min
---

### Entry 4 - [April 30, 11:30]
**What I implemented**: 
To manage CPU access, I put in place a semaphore.
**Challenges encountered**: 
knowing when to use the semaphore and when to release it.
**How I solved it**: 
placed release() in the end block and acquire() at the beginning.
**Testing approach**: 
made ensuring that only one process was running at a time and adhered to the execution order.
**Time spent**: 
30 min
---

### Entry 5 - [May 1, 12:00 AM]
**What I implemented**: 
final testing and preparation of the documentation.
**Challenges encountered**: 
maintaining uniformity throughout several runs.
**How I solved it**: 
ran the program several times and confirmed the outcomes.
**Testing approach**: 
executed several times and compared the results.
**Time spent**: 
1 hour
---

## Part 2: Technical Questions (1 mark)

### Question 1: Race Conditions
**Q**: Identify and explain TWO race conditions in the original code. For each:
- What shared resource is affected?
- Why is concurrent access a problem?
- What incorrect behavior could occur?

**Your Answer**:

[The original code contains two race situations. Initially, threads share and increment the contextSwitchCount variable without synchronization. Inaccurate counts could result from many threads reading the same value and overwriting each other's updates. 
Second, several threads concurrently access the executionLog ArrayList. Concurrent updates could lead to incorrect data or runtime problems like ConcurrentModificationException since ArrayList is not thread-safe. These problems arise when shared resources are not protected by mutual exclusion.]

---

### Question 2: Locks vs Semaphores
**Q**: Explain the difference between ReentrantLock and Semaphore. Where did you use each in your code and why?

**Your Answer**:

[By limiting the number of threads that can access a crucial portion at once, ReentrantLock ensures mutual exclusion. It was employed in this assignment to safeguard the execution log and shared counters. Semaphore, on the other hand, restricts access to a finite resource by granting a set number of permits. To simulate CPU access and make sure that only one process runs at a time, I utilized a binary semaphore with one permit. Semaphores regulate resource access, whereas locks safeguard data consistency.]

---

### Question 3: Deadlock Prevention
**Q**: What is deadlock? Explain TWO prevention techniques and what you did to prevent deadlocks in your code.

**Your Answer**:

[When several threads are stalled indefinitely while waiting for resources held by others, this is known as a deadlock. Using try-finally blocks to guarantee that locks are always released is one preventative strategy. Keeping a constant lock acquisition sequence or avoiding nested locks are two other strategies. In order to guarantee that resources are always released and avoid deadlocks, I implemented try-finally blocks for both locks and semaphores in my code..]

---

### Question 4: Lock Granularity Design Decision 
**Q**: For Task 1 (protecting the three counters), explain your lock design choice:
- Did you use ONE lock for all three counters (coarse-grained) OR separate locks for each counter (fine-grained)?
- Explain WHY you made this choice
- What are the trade-offs between the two approaches?
- Given that the three counters are independent, which approach provides better concurrency and why?

**Your Answer**:

[I employed a coarse-grained locking strategy by using a single lock for each of the three counters. This guarantees consistency across related modifications and streamlines implementation. But because only one thread can update any counter at a time, it lowers concurrency. Because independent variables can be accessed concurrently, fine-grained locking, in which each counter has its own lock, would enable increased concurrency. Fine-grained locking works better because the counters are independent, but I went with coarse-grained locking for accuracy and simplicity..]

---

## Part 3: Synchronization Analysis (1 mark)

### Critical Section #1: Counter Variables

**Which variables**: 

**Why they need protection**: 

**Synchronization mechanism used**: 

**Code snippet**:
```java
// Paste your implementation here
```

**Justification**: 

---

### Critical Section #2: Execution Log

**What resource**: 

**Why it needs protection**: 

**Synchronization mechanism used**: 

**Code snippet**:
```java
// Paste your implementation here
```

**Justification**: 

---

### Critical Section #3: CPU Semaphore

**Purpose of semaphore**: 

**Number of permits and why**: 

**Where implemented**: 

**Code snippet**:
```java
// Paste your implementation here
```

**Effect on program behavior**: 

---

## Part 4: Testing and Verification (2 marks)

### Test 1: Consistency Check
**What I tested**: Running program multiple times to verify consistent results

**Testing procedure**: 
```bash
# Commands used (run the program at least 5 times)
```

**Results**: 
(Show that running multiple times produces consistent, correct results)

**Why synchronization is necessary**: 
(Explain what race conditions COULD occur without synchronization, even if you didn't observe them. Explain which shared resources need protection and why.)

**Conclusion**: 

---

### Test 2: Exception Testing
**What I tested**: Checking for ConcurrentModificationException

**Testing procedure**: 

**Results**: 

**What this proves**: 

---

### Test 3: Correctness Verification
**What I tested**: Verifying correct final values (total burst time, context switches, etc.)

**Expected values**: 

**Actual values**: 

**Analysis**: 

---

### Test 4: Different Scenarios
**Scenario tested**: [e.g., different time quantum, more processes, etc.]

**Purpose**: 

**Results**: 

**What I learned**: 

---

## Part 5: Reflection and Learning

### What I learned about synchronization:

[6-8 sentences about key concepts, challenges, insights]

---

### Real-world applications:

Give TWO examples where synchronization is critical:

**Example 1**: 

**Example 2**: 

---

### How I would explain synchronization to others:

[Explain to someone who just finished Assignment 1 - use simple terms and analogies]

---

## Part 6: GitHub Repository Information

**Repository URL**: 

**Number of commits**: 

**Commit messages**: 
1. 
2. 
3. 
4. 

---

## Summary

**Total time spent on assignment**: 

**Key takeaways**: 
1. 
2. 
3. 

**Most challenging aspect**: 

**What I'm most proud of**: 

---

**End of Documentation**
