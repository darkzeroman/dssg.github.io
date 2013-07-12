---
published: false
layout: post
title: "Machine Learning for Human Rights"
author: Rob Mitchum
pic: "kenya.jpg"
pic-credit: Stephenwanjau/Wikimedia Commons
---

"2-car acc @ State & Lake, both drivers injred" 

That short, hastily typed text message or tweet contains a lot of information that police, emergency responders, news organizations and drivers could use. A human observer could quickly identify that it refers to an auto accident, a medical emergency, and a street intersection in Chicago. But without prior experiences and lots of human input, a computer would likely have a hard time recognizing that State and Lake are streets in Chicago, that “acc” is short for accident, or that "injred" is a typo for "injured.” 

The non-profit organization [Ushahidi](http://www.ushahidi.com/) was created by a team of developers so that text messages from eyewitnesses on the ground could be quickly mapped and shared with aid agencies, authorities and journalists. Since its first use during the violent period after the disputed 2007 election in Kenya, the organization’s crowd-sourced mapping platform has been shared with human rights volunteers around the world. 

<img src="/img/posts/uchagizi.png">

But while Ushahidi harnesses technology to more rapidly spread information about what’s happening in the streets, it still runs largely on human power. Currently, during a political crisis, natural disaster, or environmental emergency, volunteers must manually review each SMS, tweet or web report from the field before it can be mapped. 

The text that comes in is unorganized, filled with abbreviations and typos and could be in a variety of different languages. Volunteers must manually sort through each message to detect languages, extract entities such as locations, tag categories and check redundancies
 
In partnering with Ushahidi, the Data Science for Social Good fellows hope to make that review process easier, faster, and more accurate with machine learning and natural language processing techniques. Instead of manually categorizing each and every message during a crisis, the project team is developing a tool that will automatically suggest categories for incoming reports, allowing volunteers to concentrate on the most urgent reports and more innovative uses of the data.
   
#### Before the Data
To build such a tool, you need reports from past crises that Ushahidi’s volunteers have already categorized. As more human-labeled reports are fed into the algorithm, it gets better and better at categorizing them without human assistance. Without this historical “labeled data,” an algorithm can’t learn to categorize unlabeled text. 

The Ushahidi team (Kayla Jacobs, Nathan Leiby and Kwang-Sung Jun) along with their Mentor (Elena Eneva) spent the first few weeks brainstorming and investigating the project, speaking with experts from the field of disaster relief, and connecting with Ushahidi’s software engineers. The team also observed a training simulation where volunteers practiced sorting crisis messages in real time, so that the fellows could identify places where they could improve the workflow.
 
"We learned that how they assigned messages is very flexible: people in the chatroom saying they will take message number 10," Leiby said. "So it sounds like that's an area where if we can intelligently assign things to people, that might be helpful. We didn't expect that at all."
 
One idea inspired by that observation was to classify incoming messages by language, so that they could be automatically assigned to volunteers familiar with the language for further categorization. That became one of 20 brainstormed ideas the team pitched to Ushahidi, from which they chose four feasible targets that, if automated, would most help the volunteers in their sorting: 

- detecting the language a Ushahidi report is written in
- guessing a report’s category - such as “food” or “water” in the disaster context, “violence at the polling place” or “polling place opening late” in the election monitoring context.
- identifying entities in reports: people, places and other proper nouns
- flagging (near) duplicate messages

<img src="/img/posts/workflow.png">

#### The value of a "dumb" prototype
When the team received 27 previous uses of the Ushahidi platform -- including elections in India and Venezuela, floods in Pakistan, burglaries in Atlanta, and more – the team turned from user research to quickly building a prototype that sorts messages for those initial four tasks.

The team constructed this bare-bones prototype using off-the-shelf machine learning toolkits for free text recognition and categorization. For automatic categorization of messages, the team is using [scikit-learn](http://scikit-learn.org/stable/), a Python machine learning module they were introduced to in a DSSG Learning Lunch talk by fellow Scott Alfeld. Other tools the team is currently working with include [nltk](http://nltk.org/), for recognizing entities and locations, and [SimHash](https://github.com/owainlewis/sim-hash) for detecting duplicate information. 

<img src="/img/posts/ushahidi-prototype1.png">

The original prototype’s performance… well, it's "not very good yet," according to Jacobs. But this first iteration is a crucial first step towards the ultimate goal of the summer.
 
"That's the very baseline proof that it's possible," Leiby said. "Then we can start to ask other questions: Is this the kind of information they would want? Can we give it to them in a more accurate or more prioritized form? How do we make it useful for you?"
 
Going forward, the team will flesh out the prototype, improving it iteratively as they get feedback from Ushahidi, Jun said.
 
Happily, the team found themselves with complementary talents that can be applied to these problems. While Kayla applies her background in natural language processing to the entity and duplicate recognition tasks, Kwang is using his machine learning experience to improve detection of categories and language, and Nathan is in charge of software framework setup and integration, as well as writing UI code.
 
"We've got three main sides to our project, which fits our team really well," Jacobs said. "It's been a real pleasure to work on this team, because we all have our own strengths and ways we can both teach each other and learn from each other."
 
 
 
 
 
 

