# The Cost Model — Narrative v2
## Casual, accessible rewrite. No jargon.

> **What this is:** A new narrative direction for the cost model story.
> Less academic. More human. The kind of thing you'd explain to a friend over coffee.
> Source of truth for copy rewrites on proposal.html and any future blog post.

---

## The Big Idea (one paragraph version)

A manufacturing company in Chile had been pricing their products the same way for 30 years — materials times a factor. It worked well enough to stay in business. But nobody actually knew which products made money and which ones didn't. We fixed that. Here's how a whiteboard sketch became a pricing engine.

---

## ACT 1 — A business that doesn't know its own costs

Dulox makes stainless steel products. Custom stuff — restaurant kitchens, trash bins, counters, campanas, shelves. Everything is different. Different size, different shape, different amount of work.

For 30 years, they priced everything the same way:

> **price = materials × a factor**

The factor was supposed to cover everything else — the operators, the machines, the time, the electricity, the consumables. One number to rule them all.

And honestly? It worked. The company was profitable. So nobody questioned it.

The problem only became obvious when you looked closer. That factor treats a simple flat shelf the same as a cylindrical bin with interior welds and a mirror polish finish. Those two products are not remotely the same amount of work. One takes 2 hours. The other takes 12.

When you use one factor for both, you end up systematically undercharging for complex products and overcharging for simple ones. Simple products subsidize complex ones. Nobody knows. The company keeps moving.

**This is how a structural problem hides inside a profitable business.**

The salesperson quotes a complex order too cheap, wins the deal, and the factory loses money on it. Nobody connects the dots because nobody can see the real cost. The margin just quietly bleeds.

The only reason it hadn't been a crisis yet was volume and luck. That's not a growth plan.

---

## ACT 2 — You can't fix what you can't see

The root cause wasn't the factor. The factor was a symptom.

The real problem was that nobody had ever broken down what it actually costs to make a specific product. Not in a systematic way.

Before you can price something correctly, you have to be able to decompose it — turn it into its real cost parts. Material. Time per process. Machine wear. Consumables. Each piece, each step, each hour.

The factory had never done this. Not because they were negligent — because it's genuinely hard. Every product is custom. There is no standard price list. You'd need a model that can look at any new product and estimate the cost without having made it before.

**That's the real challenge. Not the math. The decomposition.**

Once you can decompose a product into its cost parts, the math is easy. Addition. The hard part is knowing what the parts are and how long each one takes.

---

## ACT 3 — Every product speaks the same language, if you know how to listen

Here's the insight that made the model possible.

Even though every product at Dulox is custom, they don't all go through a completely unique process. They share routes through the factory. A cylindrical bin and a custom bucket have different dimensions, but they both go through cutting, rolling, welding, and polishing. The route is the same. The difficulty changes.

We called these routes **process profiles**. Think of it as the manufacturing DNA of a product. Two products that look completely different can share the same DNA if they go through the same steps.

We went through all 1,300+ products and classified each one. Not by what they look like, but by what actually happens to them in the factory.

This gave us the first layer of the model. You look at a new product, you figure out its profile, and you immediately know which processes it will go through. Half the cost question is already answered.

---

## ACT 4 — Four things that make anything harder to make

Knowing the route is not enough. You also need to know how hard the route is for this specific product.

A small simple bin and a large complex bin both go through rolling. But they are not the same amount of work. So how do you measure difficulty?

We landed on four things that drive complexity in almost any manufactured product:

**Size** — bigger products take more cutting, more welding, more polishing, more material. There's no way around it.

**Thickness** — thin steel and thick steel are completely different animals. Thick steel requires more powerful machines, more skilled operators, and takes longer at every step.

**Parts** — a product made from 3 components is not the same as one made from 12. Every joint is a weld. Every weld is time.

**Special stuff** — everything that doesn't fit the first three. Interior welds you can't see from outside. Mirror finish. Refrigeration components. Logo etching. Each one adds time in ways that only someone who's done it a hundred times would know.

These four things — size, thickness, parts, special stuff — give you a score for each process. The score maps to a complexity tier: standard, elevated, or expert. Each tier has measured time estimates. Time × cost = real price.

---

## ACT 5 — The knowledge lives inside one person's head

Here's where the story gets harder.

None of this model works without the data inside it. And that data isn't in a spreadsheet anywhere. It's in the head of the production manager — Hernán — who has worked at Dulox for over 30 years.

He knows, instinctively, how long every process takes. He knows which products are going to be trouble before they even start. He can look at a sketch and immediately feel the complexity. He's been doing it so long that he doesn't even think about it consciously anymore.

That knowledge is real. It's accurate. It is also completely invisible to anyone else in the organization.

Getting it out of his head was the hardest part of the whole project.

You can't just sit someone down and say "tell me everything you know." That's not how expertise works. The knowledge is contextual. It comes out in pieces, in situations, in reactions to specific products. The early sessions with Hernán were uncomfortable — he'd say "that takes about 40 minutes" and when you asked "for what size?" he'd stop and say "well, it depends." The whole project was about making the "it depends" into something concrete.

**Every organization has a Hernán. Someone whose knowledge runs the whole operation without anyone fully realizing it.**

When that person leaves, they take everything with them. That knowledge doesn't exist anywhere else. The organization has to start from scratch.

---

## ACT 6 — Don't change the workflow. Intercept it.

Most "let's digitize the factory" projects fail the same way. They ask people to do new things. New software. New forms. New habits.

These are people who've been doing their job for 15 years without any of that. Every new step is friction. Friction becomes abandonment. The project dies.

The better move is: don't change the workflow. Find the artifact that already carries the information you need, and wrap the technology around that.

Hernán already draws a sketch for every production order. He's done it for decades. The sketch has dimensions, materials, process notes, special instructions for the operators. Everything the model needs is already in that sketch.

So the ingestion loop became simple:

1. Hernán draws the sketch (same as always)
2. Someone photographs it (one extra step, 5 seconds)
3. A vision model reads the sketch and extracts the structured data
4. That data feeds the cost model
5. Hernán reviews the output, corrects where needed
6. The correction improves the model

His behavior changed by almost nothing. The system captures everything.

---

## ACT 7 — What happens when the number is right

When the model works, a few things change.

Salespeople stop guessing. They can quote a complex product with confidence — not because they've memorized every process, but because the system can show its work. "This product is this profile, this complexity tier, and this is why it costs this much." That's a different conversation than "the factor says X."

The company can see margin by product type for the first time in 30 years. They can see which categories are systematically underpriced and which have room. They can stop subsidizing complex work with simple work.

When new people join, they don't have to spend two years absorbing Hernán's intuition through osmosis. The model is a starting point. A baseline. It explains the logic. The onboarding gets faster.

**The factory didn't change. The machines are the same. The operators are the same. Hernán still draws his sketches every morning. What changed is that now, when the sketch is done, the number is right.**

---

## The bigger point

This story is about one factory. But the pattern is everywhere.

Every organization has knowledge that lives inside specific people and nowhere else. That knowledge is what makes them good at what they do. It's also a structural fragility — because when those people leave, the knowledge leaves with them.

The interesting thing about the last few years is that we now have tools to capture that knowledge in a way that wasn't practical before. Not to replace the expert. To give the expert a mirror — a way to see and share and improve what they already know.

The AI part of this project is not the impressive part. The impressive part is the epistemological work: convincing an expert to articulate what he's never had to articulate, structuring it into something consistent, and building a system that holds it over time.

**Knowledge hides where nobody is looking. Experts surface it every day, without realizing it. The job is to catch it before it disappears.**

That's the real project. The pricing engine is just the output.

---

## TONE NOTES

- First person ("I" not "the team")
- No jargon. If a word needs a glossary entry, replace it.
- Name things in plain language first, then introduce the technical term if necessary
- Short sentences. One idea per paragraph.
- Don't hide the difficulty. The expert sessions were uncomfortable. The first version was wrong. Show it.
- The reader should feel like someone is thinking out loud — not presenting a finished idea
- Avoid: "leverage," "synergy," "data-driven," "AI-powered," "paradigm," "robust"
- The emotional core: there's something meaningful about making 30 years of expertise visible for the first time. End there.
