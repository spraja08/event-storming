# Event Storming : Do's & Don'ts

These notes are distilled from a few real life experiences of conducing event storming remotely, using Miro.  (Yes, face-to-face is ideal but not practical always...) Any suggestions on improving the techniques as well as the interpretations of **DDD** concepts listed here are most welcome. 


## 1. Prepare the Templates upfront

Other the main canvas, the following helps with the over all flow by reducing distractions:
- the definitions for a quick reference, 
- the library of building blocks (stickies for events, roles, aggregates etc) where the pariticipants can copy from and drag and 
- the list of steps that indicates the progress

![miro template with guides](https://github.com/spraja08/event-storming/blob/main/1-prepare-a.png)

## 2. Domain Events

- Start by getting everyone to log their version of domain events without working on the chronology first (The ordering will be done subsequently) 
- If a warm up is needed, the participants may start with listing their life events that happened in that morning. 
- Focus on the behaviour of the system (strictly, not on the structure of the system) 
- Avoid technical events ("database entry created"). Focus on the essential business events
- Choose a moderator (business expert or the product manager) to sort the domain events chronologically, filtering the duplicates out.
- Review the domain events for the consistent usage of the vocabulary (ubiquitous language) and resolve the variatiosn with the help of the business expert

![events filtered](https://github.com/spraja08/event-storming/blob/main/2-events.png)
