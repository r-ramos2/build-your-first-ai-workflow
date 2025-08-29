<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build Your First AI Workflow

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-agent-nocode)

**Author:** R  


---

## Building an AI Workflow

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/ai-agent-nocode_sdrjg8e123dv)

---

## Introducing Today's Project!

In this project, I will demonstrate how to build an AI-powered workflow that adds events to my calendar using text input. I'm doing this project to learn how to automate tasks using n8n, ChatGPT, and Google Calendar integration.

### Tools and Techniques

I used Google Calendar, n8n, and AI model integration. Key concepts I learned include setting up AI workflows, connecting tools like Google Calendar, troubleshooting errors, and customizing AI with system messages to manage scheduling tasks.

### Project reflection

This project took me approximately 2 hours. The most challenging part was troubleshooting time zone and date errors in the calendar tool. It was most rewarding to see the AI agent successfully book events in my calendar!

I did this project today to improve my understanding of AI workflows and automate my calendar. This project met my goal of learning to set up and troubleshoot AI-powered automation with practical applications!

---

## Exploring n8n

This project uses n8n to automate tasks by connecting apps like ChatGPT and Google Calendar. Workflows are step-by-step sequences that complete tasks automatically. You can involve AI in a workflow by adding decision-making or content generation.

I signed up for a free trial for n8n, which includes 14 days of access and up to 5 workflows. I don't need to enter credit card details to start the trial, so I won't be charged.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/ai-agent-nocode_c9d8f7a2)

---

## Starting an AI Workflow

To set up a workflow, I first configured a trigger, which means defining how the workflow starts. My trigger is a chat message. Other options include time-based triggers or events like receiving an email.

I connected my trigger with an AI agent node. AI Agents are systems that act autonomously without triggers. But, in this project, I am building an AI workflow that runs predefined tasks triggered by chat input.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/ai-agent-nocode_fmtkjyrg)

---

## Integrating ChatGPT

An AI workflow can be broken into three key components: the AI model (for processing input and generating responses), the tools (like Google Calendar), and the triggers or actions that link them to automate tasks and achieve desired outcomes.

My workflow's chat model uses OpenAI. Usually, connecting with OpenAI requires an API key. I could connect with OpenAI for free by using limited free tier access, or by integrating my own API key through a platform like n8n.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/ai-agent-nocode_o5p6q7r8)

---

## Integrating Google Calendar

In this workflow, the tool is Google Calendar because it allows the AI agent to create new events in my calendar based on the instructions provided through the chat.

To connect with Google Calendar, you have to allow n8n access to your calendar and events. For security best practice, it's important to review and limit the permissions granted, ensuring n8n only has access to what's necessary for the workflow.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/ai-agent-nocode_c9d8dfgv2)

---

## Testing My Workflow

I tested my AI workflow by sending a chat message to book a time in my calendar. The response was that the time was not available, which is an error because the time I selected was free in my Google Calendar, indicating an issue with the calendar.

To troubleshoot errors, you can investigate the AI agent's logs. I observed that the logs showed a mismatch between the requested time and calendar availability, meaning the workflow isn't correctly checking the calendar before booking events.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/ai-agent-nocode_c9d8egrfdv)

---

## JSON Expressions

I decided to troubleshoot by reviewing my Calendar tool setup, where I noticed an error in the Start Time and End Time settings. They were set to always create events for the current time, ignoring the AI model's time suggestions for scheduling.

I updated the start and end times to `{{ $fromAI('start_time') }}` and `{{ $fromAI('end_time') }}`, allowing the AI model to provide dynamic values based on the chat input instead of using static times. This ensures the event is scheduled properly.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/ai-agent-nocode_897rg465e)

---

## System Messages

On my second test, my workflow successfully triggered the event creation, but it still made an error in selecting the correct date. This was because the AI agent didn't have today's date as context, leading it to default to the wrong year.

This time, I tried to troubleshoot the error by writing a system message, which is: "You are a calendar assistant. Check my availability and create events for free times. Today's date is {{DateTime.now().setZone('TIMEZONE').toFormat('dd LLL yyyy')}}.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/ai-agent-nocode_rfgdhn456)

---

## Success!

On my final test, a new event was scheduled at the right time because I switched the System Message setting from Fixed to Expression, allowing the AI model to dynamically calculate the current date and time, fixing the issue with the calendar input.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/ai-agent-nocode_w3x4y5z6)

---

## System Message Variation

---

---
