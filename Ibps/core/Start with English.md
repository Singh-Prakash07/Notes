+Phase 1 (Days 1-15): Core Grammar Mechanics (The "Syntax" of English)
+ Phase 2 (Days 16-30): Sentence-Level Application (Error Spotting, Fillers, Phrase Replacement)
+ Phase 3 (Days 31-45): Paragraph & Context (Cloze Test, Para Jumbles, Reading Comprehension)
+ Phase 4 (Days 46-60): Speed Drills & Full-Section Mocks

## Day -1 
### Subject-Verb Agreement
If the subject is singular, the verb must be singular. If the subject is plural, the verb must be plural, but sometimes the true subject hide behind filler phrases to trick you.
#### Rule-1. The "Accompaniment" Trap
   + When subjects are joined by phrases like as well as, along with, together with, in addition to, or besides, the verb always agrees with the first subject. The rest is just a modifier
   + The cluster manager, as well as the worker nodes, is going offline. (The verb "is" agrees with the primary subject, "manager").

#### Rule-2. "Neither/Nor" and "Either/Or" (The Proximity Rule)
  + When two subjects are joined by neither...nor, either...or, not only...but also, or simply or/nor, the verb agrees with the subject closest to it.
   + Neither the data engineers nor the database administrator was aware of the breach. (The verb "was" agrees with the singular "administrator").

#### Rule-3. Tricky Singulars (Indefinite Pronouns)
Words like each, every, everyone, someone, anybody, nobody, either, and neither are always singular, even if they imply a group.
   + Each of the ETL pipelines has been restarted. (The subject is "Each", not "pipelines").
   + There are two server backup options. Either is fine to use. (Meaning: Pick option A or option B, both are acceptable).
+ Problems
   + The cost of the new AWS instances (A) / as well as the database migrations (B) / are significantly higher (C) / than we initially estimated. (D) / No Error (E)
   + Neither the frontend developers (A) / nor the DevOps engineer (B) / have access (C) / to the production environment. (D) / No Error (E)
   + Every one of the PySpark scripts (A) / implemented by the team (B) / seem to be (C) / causing memory leaks. (D) / No Error (E)
   + The lead architect, together with (A) / three junior analysts, (B) / is attending the (C) / tech conference in Bangalore. (D) / No Error (E)
   + Not only the raw data streams (A) / but also the backend API (B) / needs to be (C) / thoroughly tested before deployment. (D) / No Error (E)
+ Solution
   + (C). Replace "are" with "is". The primary subject is "cost" (singular), not the instances or migrations. (Rule 1)
   + (C). Replace "have" with "has". The verb must agree with the closest subject, which is "engineer" (singular). (Rule 2)
   + (C). Replace "seem" with "seems". The subject is "Every one" (singular), not the scripts. (Rule 3)
   + (E). No Error. The verb "is" correctly agrees with the first subject, "lead architect". (Rule 1)
   + (E). No Error. The closest subject is "API" (singular), so the singular verb "needs" is correct. (Rule 2)

## Day 2: 
### Rule 4: "A number of" vs. "The number of"
   + "A number of" means "several" or "many" and always takes a plural verb.
      + A number of network errors were detected during the stress test.
   + "The number of" refers to a specific, singular mathematical quantity and takes a singular verb.
      + The number of network errors is steadily decreasing.

### Rule 5: Fractions and Percentages
+ When dealing with words like half of, a third of, 50% of, or the majority of, look at the noun that comes after "of". The verb must agree with that noun.
   + If the noun is uncountable/singular: Half of the database is corrupted. (Database is singular)
   + If the noun is plural: Half of the servers are offline. (Servers are plural)

### Rule 6: Collective Nouns (United vs. Divided)
+ Nouns like team, committee, jury, board, or staff usually take a singular verb because they act as one single unit. However, if the sentence shows that the members are disagreeing or acting individually, use a plural verb.
   + United (Singular): The IT committee has approved the new firewall policy.
   + Divided (Plural): The IT committee are divided on which vendor to choose. (Hint: Look for words like "divided", "arguing", or "their").

#### Daily Exam Drills (Error Spotting)

   1. A large number of users (A) / has reported (B) / that the mobile banking application (C) / is crashing on startup. (D) / No Error (E)
   2. Three-fourths of the server configuration (A) / are already completed, (B) / but we still need to set up (C) / the load balancers. (D) / No Error (E)
   3. The board of executives (A) / was completely divided (B) / over the decision to outsource (C) / the cloud infrastructure. (D) / No Error (E)
   4. The number of open tickets (A) / in the IT helpdesk queue (B) / are causing (C) / significant delays in resolution times. (D) / No Error (E)
   5. Over sixty percent of the bandwidth (A) / is being consumed (B) / by a single background process (C) / running on the host. (D) / No Error (E)

### Solutions & Breakdown:
   1. **(B)**. Replace "has" with "have". "A large number of" dictates a plural verb. *(Rule 4)*
   2. **(B)**. Replace "are" with "is". Look at the noun after the fraction: "server configuration" is singular. *(Rule 5)*
   3. **(B)**. Replace "was" with "were". The board is "divided," meaning they are acting as individuals, not a unified group. Hence, it needs a plural verb. *(Rule 6)*
   4. **(C)**. Replace "are" with "is". The subject is "The number", which is singular. *(Rule 4)*
   5. **(E)**. No Error. "Bandwidth" is an uncountable/singular noun, so the singular verb "is" is perfectly correct. *(Rule 5)*
## 3. Nouns (Countable vs. Uncountable & Exceptions)
### Rule 1: Uncountable Nouns Cannot Be Pluralized
Certain nouns in English represent abstract concepts, masses, or groups and do not have a plural form (no "s" at the end). They also always take a singular verb and cannot be used with "a" or "an."
   + Common Exam Examples: Information, equipment, machinery, advice, luggage, furniture, software, hardware, evidence.
   + Incorrect: The IT department ordered new equipments and updated the softwares.
   + Correct: The IT department ordered new equipment and updated the software.
   + (Tip: If you need to make them plural, use phrases like "pieces of equipment" or "types of software".)

### Rule 2: Plural in Form, Singular in Meaning
Some nouns end in "s" making them look plural, but they refer to a single concept and take a singular verb.

  
