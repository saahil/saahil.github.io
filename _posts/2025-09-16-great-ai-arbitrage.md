---
layout:     post
title:      The Great AI Arbitrage
date:       2025-09-17 07:00:00
summary:    Technology, not viability, is the reason for disillusionment with Generative AI
categories: technology data generative-ai llm
---

The recent [MIT NANDA study](https://nanda.media.mit.edu/ai_report_2025.pdf) (State of AI in Business 2025) on the business adoption of generative AI has been eye-opening for many, including especially those who believed that the ever-improving model quality from leading labs meant that they were ripe for disrupting cognitive functions in age-old industrial processes. The study showed, amongst other things, that this was by far not the case, and that almost 95% of the generative AI use-case implementations didn’t end up in sustained and profitable usage in companies.

While there’s a lot to unpack and opine subjectively on the study (especially considering that the sample used in the study is only 52 companies), I’m going to use this single finding that I find the most interesting, as a jumping-off point to this series of articles

> *“While only 40% of companies say they purchased an official LLM subscription, workers from over 90% of the companies we surveyed reported regular use of personal AI tools for work tasks.” State of AI in Business 2025, MIT NANDA*
> 

That should not be surprising to any of us who are outside research settings. Anyone who has worked in a company larger than 20 employees has, at some point, run into this scenario - there’s a new LLM or coding agent in town, you’d like to put a credit card on file to start and feel around the vibe of the tool before making a decision to switch, but getting your request approved by management is so cumbersome that you end up using your personal CC for trying out. You might defer the official request until later, if you even expect the request to eventually be cleared by the CISO - who may refuse the eventual request due to data provenance reasons.

But what *is* remarkable about this finding is the stark contrast it puts against the *official* initiatives that enterprises undertake with generative AI in general, and LLMs in particular. In addition to the 40% figure of companies purchasing official licensing, there’s of course the famous *5%* figure that refers to companies that report profitable and sustained production implementations with the technology. 

In this article, we will use the MIT study itself, but with a quantitative breakdown, to answer the question 

<aside>
💡

Why can’t organizations capture the value from generative AI that individual employees so effortlessly access?

</aside>

In particular, we will examine three critical aspects related to enterprise generative AI adoption - 

1. Why the inference economics actually favour model providers at the current pricing already?
2. Where the real adoption of generative AI is happening?
3. What capability gaps exist that explain the divide between individual and enterprise-level AI adoption? 

In the follow-up articles in the series, we will then go on to deduce how enterprises can assess whether their planned generative AI POCs are likely to succeed or fail, based on the use-case categorization of the MIT Nanda study. 

## The Silicon Floor

When we distinguish between “consumer” and “enterprise” use-cases of LLMs, the temptation is to compare ChatGPT-like applications to the early days of Uber and Zomato - that the main objective *must* be to capture market segments at all (VC’s) costs, avoid commoditization and only then aim for profitability. However, one only needs to work through the economics of LLM APIs to see that what we’re witnessing today is anything but comparable to the gig-economy days. In this section, we will quantitatively show that model providers are, in fact, well on their path to profitability on their consumer products, if not already there. 

![The capex view of Llama3’s training costs. For full analysis can be found [here](/files/llm_training_economics.html). ]({{"/images/training_summary.png"}})
*The capex view of Llama3’s training costs. For full analysis can be found [here](/files/llm_training_economics.html).*

While training costs for LLMs are substantial - our analysis shows Llama 3 herd of models required between [$197M-$748M in total development costs](/files/llm_training_economics.html) when including experimental runs, infrastructure, and electricity costs - these represent one-time expenses. For API providers, the inference costs far outweigh training costs. This has been corroborated directly by several credible sources, such as Yann LeCun who [said](https://www.businessinsider.com/meta-yann-lecun-ai-scientist-deepseek-markets-reaction-inference-2025-1?utm_source=chatgpt.com) in context of the erstwhile media frenzy over Deepseek

> *“The huge sums of money going into US AI companies were needed primarily for inference, not training AI. Most of the infrastructure cost for AI is for inference: serving AI assistants to billions of people.” Yann LeCun, Chief AI Scientist at Meta*
> 

With this in mind, in the rest of this section, we'll just go ahead and assume that the cost of inference (runtime serving costs - GPU rental or own-cost amortization, power, cooling, datacenter cost) is the main driver for deciding operating margins for model providers, such as OpenAI and Anthropic, and not training. This may, of course, not hold true for business models other than model-as-an-API, but we'll come to alternative business models for foundational companies at a later point.

![OpenAI’s estimated profit margins on ChatGPT consumer app alone. The costs are for COGS only. For details refer to the [full breakdown](/files/llm_inference_economics_full_plus_api_merged.html). ]({{"/images/paid-vs-full-infographic-inference.png"}})
*OpenAI’s estimated profit margins on ChatGPT consumer app alone. The costs are for COGS only. For details refer to the [full breakdown](/files/llm_inference_economics_full_plus_api_merged.html).*

As for the economics of LLM inference, a definitive answer as to the model providers’ economics is hard to come by. Various sources claim different numbers on total cost of ownership of models and serving infrastructure, and the major sources of contention are 

1. Whether there are enough paid monthly subscribers to cover the inference cost for free users
2. Whether there are enough *low usage* paid subscribers subsidizing the costs for heavy users
3. Whether there are enough consumption-based API users (e.g. coding agents) where the costs and earnings are easier to attribute than monthly subscriptions. 

Our [own calculations](/files/llm_inference_economics_full_plus_api_merged.html), using Deepseek-v3.1 MoE (37B active params) as proxy for SOTA closed models, paint an ambiguous picture about potential revenues and margins for top model providers such as OpenAI and Anthropic. Assuming a [reported](https://sqmagazine.co.uk/openai-vs-anthropic-statistics/) ~190–200M DAU for ChatGPT, we estimate that OpenAI may be spending between 300 to 700M USD per month on inference for their chat app users. Assuming 10% of those DAUs are paid users, they might be earning a monthly revenue between 350 to 400M USD. This indicates that, with tailored optimization strategies per user-segment, OpenAI might either already be profitable on ChatGPT app, or close to getting there. 

For API customers, the economics are somewhat [different](/files/llm_inference_economics_full_plus_api_merged.html): developers and enterprise clients paying ~$10 per million input tokens and ~$20 per million output tokens may provide gross margins ranges between -50% to 70%, making the API business a lever for OpenAI and Anthropic’s to cross-subsidize their consumer application business, if needed. 

A detailed breakdown of all our calculations may be seen [here](/files/llm_inference_economics_full_plus_api_merged.html). Additional sources of *non-service* revenues that we haven’t included in our analysis are the revenue share that OpenAI and Anthropic might earn on their enterprise inference deals with Azure (Azure OpenAI), AWS (Bedrock) or Google (Vertex AI Partner Models). 

Therefore, even assuming considerable deviations in the reported usage data and model details, the economics of GA inference currently favour the market leaders in generative AI. OpenAI, Anthropic, Google Deepmind and such, for all we can observe, have not made any major moves to squeeze their margins yet, which should indicate how different these dynamics are to the gig economy days.

## The “Shadow Economy” Paradox

As we have seen above, the major foundation model providers can already provide access to generative AI technology profitably to millions of users worldwide. In fact, our calculations reveal that had it not been for the incredible demand for these model APIs, the model providers may never have been able to operate profitably, i.e. the economy of GPU utilization works out for them only due to the scale.

It would be fair to say that a major chunk of the daily active users of these chat-style applications are employees of the very enterprises that report little to no gains in efficiency with generative AI (more on that soon). 

What I find remarkable about this figure is that a significant share of employees reporting productivity boost with tools such as ChatGPT are using their private subscriptions to these services, for professional purpose (the “shadow economy”).

> *"A significant number of workers already use AI tools privately, reporting productivity gains, while their companies' formal AI initiatives stall." State of AI in Business 2025, MIT NANDA*
> 

The reason this fact is remarkable is that these employees have wildly different feedback for the task-specific generative AI tooling and solutions that their own companies were developing at the time.  

> *"A significant number of workers already use AI tools privately, reporting productivity gains, while their companies' formal AI initiatives stall." State of AI in Business 2025, MIT NANDA*
> 

In summary, the foundation model providers are already profitable off the back of the day-to-day productivity increase of employees of the same companies, whose own custom AI tools largely suck. 

So, why don’t these enterprises just let their employees use company credit cards for Claude, instead of sinking millions into failed custom generative AI tooling?

## The Real Adoption Barriers

It should be clear to the readers that it is not due to a mismatch in the fundamental model economics, training-time or inference-time, that only 5% of the enterprises deploying generative AI pilots end up extracting regular and sustained business value out of them. The MIT study itself points to *technological* *gaps* that are, in fact, to blame.

The study assigns an overarching term to this identified gap in LLM-based applications - “The Learning Gap”. Basically, the LLMs - and precisely *not* the chat apps - suffer from the following glaring insufficiencies that make them unsuitable to be used as trustworthy task-specific companions, experts or - in terms that we’ve all come to accept - “*copilots”*:

1. The LLMs themselves don’t learn over time from the users’ feedback.  
2. As a corollary to the above, the LLMs require too much context to be supplied every time, and there isn’t a straightforward and *effective* way for the right context to be dynamically chosen based on the task-at-hand (👀 vector search).   
3. Even if the LLM-based workflows complete tasks without intervention *most* of the time, they break for edge-cases and don’t learn from these failures. Since, by definition, these edge cases are more complicated to define and expect, the overall trustworthiness of the LLM-based tooling suffers as a result.  

> *"Our purchased AI tool provided rigid summaries with limited customization options. With ChatGPT, I can guide the conversation and iterate until I get exactly what I need. The fundamental quality difference is noticeable, ChatGPT consistently produces better outputs, even though our vendor claims to use the same underlying technology."* - Corporate lawyer at a mid-sized firm quoted in *State of AI in Business in 2025, MIT NANDA*
> 

Enterprise employees, being well-versed in current SOTA tools and models, are able to successfully augment their own job functions precisely because they don’t expect ChatGPT et al. to retain feedback, or improve over time. We could go as far as to suggest that employees *don’t* consider AI chatbots to be replacements for *any* level of expertise in their job functions - not even interns. 

This is in stark contrast to ambitious enterprise generative AI pilots, whose stated aim often is to directly augment their workforce. Such pilots then, obviously, lead to total disenchantment since the technology clearly is not able to accumulate knowledge over time, retain relevant context (and, importantly, decide which context needs to be chucked away), and basically train itself on the job like a junior or associate-level employee would. 

As it stands, SOTA LLMs don’t stand a chance at getting promoted in the next appraisal cycle. 

## The Opportunity

So how are enterprises and startups going to respond to these key challenges (profitable TCO not being one of them) that make it difficult for generative AI initiatives to succeed? In the next articles, we will discuss some concrete failure patterns that companies regularly run into such as lost opportunity costs of fine-tuning LLMs, and applying LLMs only for low-leverage job functions. Then we will make direct suggestions based on current research and available enterprise adoption data, as to how one should prioritize use-cases that are well-suited to be augmented with capabilities that current LLMs possess.