---
theme: seriph
title: MCP Demo
drawings:
  persist: false
transition: fade
defaults:
  class: p-0
---

<div class="absolute inset-0">
  <img
    src="./generated_images/slide1-drupal-site.png"
    alt="Illustration of a Drupal website as a human interface, with three prominent tiles for Events, Speakers, and Registration."
    class="h-full w-full object-cover"
  />
</div>

<!--
Hi everyone. My name is Josh Miller. I'm a Director of Web Development, a longtime Drupal developer, and someone who cares deeply about the future of the open web.

Thank you to Pantheon.io for inviting me to do this spotlight presentation here at DrupalCon Chicago 2026. They asked me to talk about a topic that I think is extremely important for our community.

Today we're going to talk about Model Context Protocol — MCP.

More specifically:

Why the open web needs it.
Why Drupal is uniquely positioned to support it.
And why this community should be paying attention right now.

Everything I'm about to show you today works on a normal Drupal site using the Drupal MCP module. That means any Drupal website can host MCP endpoints today.

Before I jump in, I also want to acknowledge the people doing the heavy lifting here.

Mateu Aguiló Bosch, known as e0ipso on GitHub, has been doing incredible foundational work on MCP in the Drupal ecosystem.

If this demo resonates with you, please consider sponsoring him:
https://github.com/sponsors/e0ipso

Also, the team at Omedia has been working very hard to make this low-level technology practical for real organizations.

If you're interested in building MCP integrations for your organization:
https://omedia.dev/services

This work is difficult infrastructure work — the kind of thing the open web needs more people supporting.

Alright. Let's start with something very simple.

What you're looking at here is a completely normal Drupal website.

This one is called the Open Web Exchange.

It does three things:

- It lists events
- It lists speakers
- It allows people to register for events

All of this is implemented with completely standard Drupal tools:

Event content types.
Person nodes.
Webform registrations.

If someone wants to attend an event, they browse the site, read about speakers, and fill out a registration form.

This is a great interface for humans.

But there's a problem.

And the problem is that AI agents don't work like humans.
-->

---

<div class="absolute inset-0">
  <img
    src="./generated_images/slide2-websites-are-broken.png"
    alt="Diagram showing why AI agents struggle with traditional websites, highlighting pagination, linked bios, and multi-step click paths as obstacles."
    class="h-full w-full object-cover"
  />
</div>

<!--
When an AI agent tries to understand a website, it has to behave like a human browser.

It has to:

- crawl paginated lists
- follow links to speaker bios
- parse HTML
- reconstruct relationships between pieces of content

That's a terrible interface for an AI.

It leads to:

- incomplete information
- hallucinated summaries
- partial understanding of the site

In other words, we're forcing AI to navigate websites designed for people.

But AI isn't human.

And increasingly, users aren't interacting with websites directly anymore.

They're asking AI assistants questions.

Which raises a big question for the open web.

If AI becomes the interface, how do websites stay relevant?

That's where MCP comes in.
-->

---

<div class="absolute inset-0">
  <img
    src="./generated_images/slide3-intro-mcp.png"
    alt="Architecture graphic showing an AI agent connecting through MCP to a Drupal website, where Events, Speakers, and Registration are exposed as structured services."
    class="h-full w-full object-cover"
  />
</div>

<!--
MCP stands for Model Context Protocol.

At a high level, MCP is a communication layer that lets AI systems access structured tools and resources without developers having to build every integration themselves.

Instead of forcing AI to crawl webpages, MCP lets websites expose structured services.

Think of it like this.

Your website already exposes:

- a human interface, HTML pages
- a search interface, SEO

MCP adds a third interface:

an agent interface

In MCP architecture, an AI client communicates with an MCP server that exposes tools, resources, and prompts connected to an underlying system.

For example, a GitHub MCP server might expose tools like:

- list repositories
- read pull requests
- fetch issues

Instead of developers writing every tool manually, those integrations are already provided by the MCP server.

Now apply that same idea to websites.

Your website can expose services like:

- list events
- fetch speaker information
- register a user

Instead of browsing your website, AI can use it.

And that's what I'm going to show you.
-->

---

<div class="absolute inset-0">
  <img
    src="./generated_images/slide4-demo.png"
    alt="Demo flow showing an AI assistant asking for upcoming events, retrieving structured event and speaker information, and completing registration through the website."
    class="h-full w-full object-cover"
  />
</div>

<!--
Let me show you how this works.

First, I'm going to interact with the human interface of the site.

Click through site.

Here are the events.
Here are the speakers.
Here's the registration form.

This is exactly what we expect from a Drupal site.

Now let's switch perspectives.

Instead of a human user browsing the site, imagine someone talking to an AI assistant.

They might ask something like:

What events does the Open Web Exchange have coming up?

Behind the scenes, Claude connects to the Open Web Exchange MCP server.

Instead of scraping webpages, it calls structured tools exposed by the Drupal site.

Those tools return:

- event data
- speaker data
- registration endpoints

The AI can now reason over that structured information.

Let me show you what that looks like.

Run Claude interaction.

The AI retrieves the list of upcoming events.

Then the user asks about speakers.

The AI queries the speaker tools.

Finally the user says they want to register.

Claude calls the registration tool, which integrates directly with Drupal Webform.

And just like that, the user is registered for an event.

No webpage navigation.
No scraping.
No hallucinated summaries.

The AI used the website as a service layer.

This is the piece I think the web community needs to think about very carefully.

If AI becomes the primary interface to information, then websites that only expose HTML pages are going to become invisible.

But websites that expose structured services will remain essential.

MCP gives websites a way to participate in that ecosystem.

It allows organizations to:

- control how their data is accessed
- expose real capabilities to AI agents
- maintain authority over their own information

And importantly, this isn't controlled by one company.

It's an open protocol.

Which means the open web community can participate.
Drupal can participate.
You can participate.
-->

---

<div class="absolute inset-0">
  <img
    src="./generated_images/slide5-questions.png"
    alt="Closing slide for questions, prompting discussion about Drupal MCP, Open Web Exchange, and agentic web interfaces."
    class="h-full w-full object-cover"
  />
</div>

<!--
So I want to end with a very simple request.

If you care about the open web, we need more work happening in this space.

The Drupal MCP module already exists.
It works today.

But it needs:

- contributors
- experimentation
- real deployments

Please consider supporting the people doing this work.

Sponsor Mateu Aguiló Bosch:
https://github.com/sponsors/e0ipso

And talk with Omedia if you're interested in building MCP integrations for your organization:
https://omedia.dev/services

The web has reinvented itself many times.

Search engines changed it.
Mobile changed it.
Social media changed it.
AI will change it too.

The question is whether the open web participates in that change, or gets left behind.

Thank you.

I'd love to hear your thoughts.

Questions?
-->
