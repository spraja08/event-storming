# Event Storming : Do's & Don'ts

These notes are distilled from a few real life experiences of conducing event storming remotely, using Miro.  (Yes, face-to-face is ideal but not practical always...) Any suggestions on improving the techniques as well as the interpretations of **DDD** as documented here are most welcome. (DDD itself can be learned from Eric Evans blue book or Vaugn Vernon's red or green books)


## 1. Prepare the Templates upfront

Other the main canvas, the following helps with the over all flow by reducing distractions:
- The definitions for a quick reference, 
- The library of building blocks (stickies for events, roles, aggregates etc) where the pariticipants can copy from and drag and 
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
- Review the Domain Events for the consistent usage of the vocabulary (ubiquitous language) and resolve the variatiosn with the help of the business expert

![events filtered](https://github.com/spraja08/event-storming/blob/main/images/2-events.png)

## 3. Commands & Actors

- From a readability perspective, map the Actors and Commands abvoe the events. (by now, the events are connected in a flow)

![commands mapped](https://github.com/spraja08/event-storming/blob/main/images/3-commands.png)

## 4. Read Models, Policies & External Systems

- Sweep from left to right and attach the policies to the Domain Events (wherever some rules needed to be evaluated before the Domain Event could occur)
- Read Model basically is the "information" that the user needs for deliberation before issuing the Command to the system. Again, high level and not the db design or Data Transfer Objects design.
- Map out the External Systems that are used for that Domain Event to happen

![policies and ext systems](https://github.com/spraja08/event-storming/blob/main/images/4-policy.png)

## 5. Aggregates

- Here is where the business participants might hit a cognitive overload. Pre-warn them that they can take it easy here.
- One interepretation that works for the technical pariticpants is this:
  -  Every Domain event represents a state change in the system.
  -  An Aggregate holds such state changes (using multiple related highly-cohesive entities)
  -  Some interpretations mention that Aggregates also are responsible for the execution of policies (business logic)
- Again, capture enough to represent the system behaviour (not an ER-model)

![aggregates](https://github.com/spraja08/event-storming/blob/main/images/5-aggregates.png)

## 6. Bounded Contexts

- From the left, start grouping "cohesive" domain events into a single bounded context using the hueristics below: 
  -  Same set of aggregates are being used
  -  These aggregates have consistent meaning for the respective Actors (complying to the ubiquitous language). Beware of the Aggregates that have the same names but different meanings (polysemes)
  -  The Actors involved do not have to "switch contexts" (they have a single context)
  -  Every subsequent Domain Event is an incremental step change and not jumping into a completely different outcome
  -  Usually, crossing the organizational unit (Line of Business) represents the boundary of a bounded context. But beware of the consequences as stated by Conway's Law.
  -  Watch out for the supporting functions(Payments, Implementing KYC etc). If these are used by multiple processes in the organization, these can also be grouped into Supporting Bounded Contexts.
  

![bounded contexts](https://github.com/spraja08/event-storming/blob/main/images/6-bounded.png)
