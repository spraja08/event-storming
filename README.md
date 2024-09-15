# Event Storming : Do's & Don'ts

These notes are distilled from a few real life experiences of conducing event storming remotely, using Miro.  (Yes, face-to-face is ideal but not practical always...) Any suggestions on improving the techniques as well as the interpretations of **DDD** as documented here are most welcome. (DDD itself can be learned from Eric Evans' blue book and Vaugn Vernon's red or green books). The scope is not to explain event storming or DDD but to provide guidance on making some key decisions while running the workshop itself. And the Audience for this are the moderators of event storming workshops

## 1. Prepare the Templates upfront

Other than the main canvas, the following helps with the over all flow by reducing distractions:
- The definitions for a quick reference, 
- The library of building blocks (stickies for events, roles, aggregates etc) where the participants can copy from and drag and 
- The list of steps that indicates the progress

![miro template with guides](https://github.com/spraja08/event-storming/blob/main/images/1-prepare-a.png)

## 2a. Domain Events Dump

- Start by getting everyone to log their version of Domain Events without working on the chronology first (The ordering will be done subsequently) 
- If a warm up is needed, the participants may start with listing their life events that happened in that morning. 
- Focus on the behaviour of the system (strictly, not on the structure of the system) 
- Avoid technical events ("database entry created"). Focus on the essential business events

## 2b. Domain Events Streamlining

- Choose a moderator (business expert or the product manager) to sort the Domain Events chronologically, filtering the duplicates out.
- Cover the happy flows. Abstract the exception flows in a subprocess to be expanded later.
- Review the Domain Events for the consistent usage of the vocabulary (ubiquitous language) and resolve the variations with the help of the business expert

![events filtered](https://github.com/spraja08/event-storming/blob/main/images/2-events.png)

## 3. Commands & Actors

- From a readability perspective, map the Actors and Commands above the events. (by now, the events are connected in a flow)

![commands mapped](https://github.com/spraja08/event-storming/blob/main/images/3-commands.png)

## 4. Read Models, Policies & External Systems

- Sweep from left to right and attach the policies to the Domain Events (wherever some rules needed to be evaluated before the Domain Event could occur)
- Read Model basically is the "information" that the user needs for deliberation before issuing the Command to the system. Again, high level and not the db design or Data Transfer Objects design.
- Map out the External Systems that are used for that Domain Event to happen
- The policies need to be expanded in detail. They might become a subprocess that may also involve external systems. This would lead to modelling extra Domain Events and Read Models.
  
![policies and ext systems](https://github.com/spraja08/event-storming/blob/main/images/4-policy.png)

## 5. Aggregates

- Here is where the business participants might hit a cognitive overload. Pre-warn them that they can take it easy here.
- An interpretation that works for the technical participants is this:
  -  Every Domain event represents a state change in the system.
  -  An Aggregate holds such state and maintain the changes (using multiple related highly-cohesive entities)
  -  Some interpretations mention that Aggregates also are responsible for the execution of policies (business logic)

- It is good to look across the subsequent events in the chain (most likely they are changing the states of same aggregates) so that the Aggregates won’t be too fine grained in the start itself.
- Again, capture enough to represent the system behaviour (not to be tempted to do a detailed ER-model)

![aggregates](https://github.com/spraja08/event-storming/blob/main/images/5-aggregates.png)

## 6. Bounded Contexts

- From the left, start grouping "cohesive" domain events into a single bounded context using the heuristics below: 
  -  Same set of aggregates are being used
  -  These aggregates have consistent meaning for the respective Actors (complying to the ubiquitous language). Beware of the Aggregates that have the same names but different meanings (polysemes)
  -  The Actors involved do not have to "switch contexts" as they perform their works (they have a single context)
  -  Every subsequent Domain Event is an incremental step change and not jumping into a completely different outcome
  -  Usually, crossing the organizational unit (Line of Business) represents the boundary of a bounded context. But beware of the consequences as stated by Conway's Law.
  -  Watch out for the supporting functions(Payments, Performing Know-Your-Customer(KYC) etc). If these are used by multiple processes in the organization, these can also be grouped into Supporting Bounded Contexts.
  
![bounded contexts](https://github.com/spraja08/event-storming/blob/main/images/6-bounded.png)

- Finally, you may apply the golden principles -" high cohesion and loose coupling" to judge and adjust (Would this lead to an *independently deployable* chunk)

Sure, here's the text converted into Markdown format:

## 7. What Can Go Wrong and the Fixes

### a. Lack of clear business context and domain knowledge:
- **Issue:** Participants may not have a deep understanding of the business domain and processes, leading to incomplete or inaccurate event identification.
- **Fix:** Ensure you have the right mix of business experts and domain knowledge owners participating in the event storming session. Spend time upfront to establish the business context and boundaries.

### b. Overwhelming number of events:
- **Issue:** Participants may generate too many events, leading to cognitive overload and difficulty in organizing and making sense of the flow.
- **Fix:** Encourage participants to focus on the most critical and high-level business events first. Periodically review and group related events to keep the model manageable.

### c. Difficulty in establishing the proper sequence of events:
- **Issue:** Participants may struggle to correctly order the events in the right chronological sequence.
- **Fix:** Provide a clear visual timeline or swimlane to help participants place the events in the right order. Leverage the business domain experts to guide the sequencing.

### d. Lack of consistent language and terminology:
- **Issue:** Participants may use different terms or vocabularies to describe the same concepts, leading to confusion and ambiguity.
- **Fix:** Encourage the use of a ubiquitous language and facilitate a discussion to align on the right terms and definitions. Maintain a glossary of agreed-upon terms.

### e. Difficulty in identifying the right level of abstraction:
- **Issue:** Participants may struggle to strike the right balance between high-level, abstract events and overly detailed, technical events.
- **Fix:** Guide the participants to focus on the essential business events and avoid getting caught up in the technical implementation details. Revisit the level of abstraction periodically.

### f. Lack of engagement and participation:
- **Issue:** Some participants may be more passive or reluctant to contribute, leading to a skewed or incomplete model.
- **Fix:** Foster an inclusive environment, encourage active participation, and ensure that all voices are heard. Break the group into smaller teams if necessary to increase engagement.

### g. Difficulty in identifying boundaries and bounded contexts:
- **Issue:** Participants may have trouble drawing the boundaries between different bounded contexts or identifying the appropriate aggregates.
- **Fix:** Provide guidance on the principles of bounded context and aggregates, and facilitate discussions to help participants recognize the natural boundaries within the domain.

### h. Inability to manage exceptions and alternative flows:
- **Issue:** The event storming exercise may focus primarily on the "happy path" scenarios, neglecting the exceptional or alternative flows.
- **Fix:** Encourage participants to consider and capture the exceptional scenarios and alternative flows, either as separate subprocesses or as variations within the main flow.

Event Storming exercise is an iterative process, and it's common to encounter some of these challenges. The key is to remain flexible, leverage the domain expertise of the participants, and continuously refine the model as the understanding of the domain evolves.
