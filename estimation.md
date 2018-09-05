# estimation

## estimates

an organisation runs on goals and commitments. it wants and needs both speed and predictability.

estimates help in project selection over a wider time frame. so the organisation can make rational economic decisions.

estimates are made with imperfect information. an estimate is a best guess, a forcast about the future, based on available information. your guess will often be wrong. 

a good estimate would minimise the difference between how long something should take, and how long it actually took.

if you give a single date estimate you are making a commitment, a promise. if you deliver late then you loose trust. 

any estimate is not treated as an estimate - it is treated as fact; an actual delivery date because a managers typical next step is to arrange the individually estimated project tasks onto a calendar using known resource (developer) availability, adding some contingency factor (e.g. 20%), which reveals the anticipated completion date which is passed to their manager and on up the organisational hierarchy.

an estimate is a deadline, a contract, which increases stress and leads to working at an unsustainable pace.

the only honest estimate is "I don't know". all estimates are lies.

an estimate should be:
* accurate - 100%
* precise - just the right amount.
* honest

any request for an estimate, especially for a large amount of work, should be answered with something like a three point—minimum, expected, maximum—answer. if that shape of answer, never mind the actual numbers, is not acceptable then you’ve learned that you weren’t being asked for an estimate in the first place.

can we get better at estimates?
* clearer requirements?
* compare against previous actuals? ...we are not using the same technology & frameworks that we did 5 years ago.
* less waste? e.g. wasted effort, scope change.
* fewer interruptions?
* less work in progress?

what are we estimating?
* from beginning to done (released)
* to implement the business requirements
* to meet non-business requirements... being well engineered (clean code, maintainable, robust, secure, performant)
* ancillary tasks: dev environment setup, task prioritisation, requirements clarification, team collaboration, giving progress updates, recording time spent on a task and adjusting time remaining, updating task status, refactoring code, code documentation, coding, unit testing, integration testing, issue investigation, code reviews, multiple manual releases to test environments, quality assurance, user acceptance testing, release checklists, pre-release meetings, handover documentation for other teams (e.g. operations).


## no estimates

this idea was encapsulated in the #NoEstimates hashtag on twitter.

in essence this means not trying to estimate the size of the work; we just make sure we slice work into a size that we can bite on and turn around quickly.

by doing the work, we discover what is required to do the work.



## project estimation issues

### what is the level of productivity and quality on past projects?
* if we do not measure we do not know
* include bugs found before and after release
* accessibility of such information
* maintain accessible historical audit records using appropriate issue tracking and project issue/diary logs
  * such knowledge management is difficult (a subject for another day) due to volume of detail, the passage of time, and staff changes

### software complexity
* wherever possible, use the 80/20 rule to keep complexity low e.g. 80% of the functionality should be achievable with 20% of the effort.
* complex requirements increase opportunities for ambiguity and bugs.
* application usability
* remember that even apparently straight forward requirements are taking time to implement
* we continue to re-invent the wheel despite utilising industry leading technology
* time and mistakes cost money and credibility

### the software testing phase is prone to getting squeezed.
* establish a set of evenly spaced project milestones then track and manage them closely.
* focus on detection of bugs as early in the coding process as possible.
* tightly manage code and database changes between servers (e.g. dev, test, live)

### estimation is not easy.
* Simple calculations such as number of modules, forms, fields are unlikely to highlight complex factors which lead to project overruns.
* guestimates should be avoided
* our techniques of estimating as poorly developed which reflect an unvoiced assumption that is quite untrue, i.e. "that all will go well".
* we are uncertain of our estimates and want to keep credibility so we lack the courteous stubbornness to make people wait for a good product.
* a good project manager is a person with the ability to know what will go wrong before it actually does and has the courage to estimate when the future is cloudy.
* estimation requires experience, access to good historical information, and the courage to commit quantitative measures when qualitative data are all that exist.

### although asking a programmer how long each task will take might improve buy-in you might as well multiply his answer by a factor of 3 or more.
* without a record of past performance an answer is nothing more than a guess which excludes day to day, week to week realities of unforeseen delays.
* a man day never works out to exactly 7.5 hours of productive work.

### an analyst programmer is tasked to do almost everything to a high standard
* availability of a business analyst on the project is perceived by a programmer as taking the heat off requirements analysis and testing effort.
* for most projects, a programmer should not be responsible for testing his own work.

### consultation, reviewing, and close supervision should be perceived as important
* "two sets of eyes are better than one"
* this applies to requirements analysis, coding, and detailed testing strategy

### people factors
* competence, degree of methodical approach, experience, review / supervision, re-iterating best practice, unforeseen absence / holidays, etc.
* movement of changes between servers (dev, test, live)
* application testing well is difficult and takes time

### managers focus exclusively on a target deadline date. 
* credibility is reduced if this slips one or more times.
* one option: issue a target delivery date as late in the software development cycle as possible.

### managing change requests and scope creep (requirements that change once development has started)




## Project Estimation Guidelines

### project scope must be established in advance
* we will continue to be pushed to provide estimates for woolly requirements
* even knowing the specific details doesn't help us

### we will always be playing a guessing game
* have the confidence to use a combination of the following:
  * over-estimate
  * delay setting a target deliverable date (don't feel bad about delaying a deliverable date)

### past measurements should be used as a basis from which estimates are made
* but even that will be imperfect

### tightly manage opportunities for "scope creep"


### a project is to be broken into small pieces which are estimated individually
* use realistic breakdowns such as:
  * analysis and design (business and technical): 40-50%
  * coding: 15-20%
  * testing and debugging (includes writing test cases and capturing evidence): 30-40%
* instead of providing an guestimate for analysis, coding, and testing, for each item, specify optimistic, most likely, and pessimistic guestimates. an "expected" value should then be taken forward for each.
  * perhaps we should two target dates, the optimistic and the pessimistic?
* if guestimating, it should be advantageous to use a multiple of 3 or more.


## links
* [2016 Robert C. Martin - Effective Estimation (or: How not to Lie)](https://youtu.be/eisuQefYw_o)
* [No Estimates? By Woody Zuill (@WoodyZuill) At Agile India 2017](https://youtu.be/3f1JebvRnOw)
* [#NoEstimates (Allen Holub)](https://youtu.be/QVBlnCTu9Ms)
* [#NoEstimates: 6 Software Experts Give Their View on the Movement](https://plan.io/blog/noestimates-6-software-experts-give-their-view/)
