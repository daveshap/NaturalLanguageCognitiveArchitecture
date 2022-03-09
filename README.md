# Natural Language Cognitive Architecture
### A Prototype Artificial General Intelligence

![NLCA architectural diagram](https://github.com/daveshap/NaturalLanguageCognitiveArchitecture/blob/main/images/01%20architectural%20diagram.png?raw=true)

## Introduction

### Preface

> The right information at the right moment changes lives. The right information at the right moment saves lives. 

This was my mantra, my highest design principle behind the Natural Language Cognitive Architecture (NLCA, or “nalka”). Everything I designed and tested flows from this core purpose. Whether you are a frustrated and tired parent, a busy doctor, or a soldier on the battlefield – correct information is the key to success and survival.

This book is meant for people who want to implement and experiment with NLCA. Secondarily, this book is for anyone who is curious about AGI and cognitive architectures. For those attempting to implement NLCA, you should already possess intermediate programming skills (such as Python) as well as some knowledge of databases and APIs. All other readers should have at least some understanding of AI and machine learning concepts – I will do my best to explain ideas with analogies, metaphors, and diagrams but some background knowledge will always help.

### Background

I grew up watching TV shows and movies such as Star Trek: The Next Generation. Commander Data, an android, was an optimistic example for the future of robotics and AI. Here, we had a machine with superhuman strength and intelligence who was (almost) never dangerous and (almost) always benevolent. His primary goal, his central motivation, was to “become more human”. In machine learning, Data’s goal to become more human would be called an “objective function”; a metric that he is trying to optimize. In the context of AGI and cognitive architecture, Data’s goal of becoming more human is what I call a “Core Objective Function”. A Core Objective Function is a clear purpose stated in natural language. There are three Core Objective Functions in NLCA: reduce suffering, increase prosperity, and increase understanding. Do not get bogged down on those functions right now, there is an entire chapter on the Core Objective Functions later. 

I started experimenting with deep neural networks and evolutionary algorithms back in 2009. Deep neural networks are all the rage today. They are a type of machine learning model that emulates the neurons in a human brain. There are some important differences between real neurons and artificial neural networks, but those differences are immaterial to this book. All you need to know is that deep neural networks are biomimetic in nature, they mimic biological processes. Evolutionary algorithms are also becoming popular, but they do not figure into the design of NLCA. A few years later I started playing with TensorFlow, Google’s most powerful and most popular deep neural network software. I also started entering Kaggle competitions. Kaggle is a data science competition platform where teams use machine learning to solve problems and win prizes. I never won anything on Kaggle, but it was a critical learning experience. I have been dabbling, experimenting, and tinkering for well over a decade. On top of that, I have augmented my understanding of intelligence and the mind by reading such works as Phantoms in the Brain by VS Ramachandran, A Thousand Brains by Jeff Hawkins, Thinking Fast and Slow by Daniel Kahneman, Language Instinct by Steven Pinker, and dozens more.

All the while, my day job is systems engineering – I work with huge, complex computer systems. Some days I handle petabytes of data. Other days I maintain datacenter hardware or repair million-dollar-per-hour business applications. My career has me working with databases, applications, servers, cloud, automation, and microservices on a daily basis. This professional focus has given me a unique perspective on how to go about constructing an intelligent machine such as Commander Data.

I have combined my passion for artificial intelligence with my professional expertise. This hybridization has given me critical insights. Those insights resulted in the research and theory captured in this book; NLCA is the culmination of more than a decade of study and experimentation. I really and truly implemented NLCA in the form of a chatbot – this book outlines my process and observations while creating an honest to goodness prototype AGI.

My primary motivation was to create an intelligent information companion like Iron Man’s JARVIS, a fictional AI that becomes sentient, or the ship computer from Star Trek: The Next Generation. I realized that so many problems in life can be solved by having the right information at the right time. Sometimes we do not know what information to search for. But an intelligent machine that knows us well might be able to provide exactly what we need, exactly when we need it. Everything I created flows from this design objective.

One last caveat before we dive into the summary of NLCA: this is very much a work in progress. While I have successfully implemented or demonstrated all of what you will read about in this book, there are some components that are still not performing up to snuff. The reason for my releasing this book prematurely is so that more minds can work on these problems – I cannot do it all by myself! I have many divergent avenues of investigation, so if I want to explore them, I will need help. My time and cognitive resources are limited so this book is as much a recruiting tool as anything else.

### What will AGI look like?

First, we must define AGI. One prevailing definition of AGI is the ability of an intelligent agent to understand or learn any intellectual task that a human being can. There are many permutations of this definition, but the consensus seems to be human-level learning and comprehension.

We have plenty of expectations about AGI because of science fiction. Intelligent automatons have fascinated humans for thousands of years, from the Minoan legend of Talos to HAL 9000 and Command Data. But these are all works of fiction, so what will AGI really look like when it arrives?

Let us start by breaking down the components of intelligence – what are the internal and external behaviors that we expect of intelligent entities? I found that Bloom’s taxonomy, a system developed for teaching, is a good way to break down the behaviors and outcomes of learning. After all, the current definition of AGI is the ability to learn and understand anything a human can. In descending order of complexity and difficulty, 
Bloom’s taxonomy is:

1.	Create – Produce new or original work.
2.	Evaluate – Justify a stand or decision.
3.	Analyze – Draw connections among ideas.
4.	Apply – Use information in new situations.
5.	Understand – Explain ideas or concepts.
6.	Remember – Recall facts and basic concepts.

Ultimately, then, AGI must be able to remember facts and concepts, and eventually work its way up to the ability to create new and original work. Under what conditions do we expect the AGI to achieve these goals? Humans generally require study, instruction, and practice – so it may be natural to assume, as Alan Turing did, that an AGI would need to go through the same pedagogical process of learning that humans do; humans learn spontaneously from the time we first open our eyes. Learning and curiosity are intrinsic to our organism, but then we also have institutions of structured learning as well as the ability to self-educate with a variety of tools, such as books and online courses. In any case, humans cannot help but learn from exposure and practice. Our brains are hardwired to ingest new information and integrate it into our models of the world, with or without any conscious effort.

Thus, spontaneous learning is one of the key features we should expect of AGI – whatever else the AGI does, it must learn and adapt all on its own, completely automatically. Even in fictional examples, whether you are talking about Skynet or Commander Data, we all seem to agree that a truly intelligent machine must learn from its experiences in real-time. The AGI might not know everything from the moment you turn it on, but it should be capable of learning anything over time.

Spontaneous learning is a strictly internal, cognitive behavior. Learning needs to happen for something to be intelligent but how would an AGI go about demonstrating its intelligence? We humans often hold creation up as the pinnacle of intelligence and achievement, hence creation’s place at the top of Bloom’s taxonomy. Experts and geniuses are expected to write a book, compose a symphony, or propose a theory of cosmology. Thus, an AGI must be able to produce something, a creation of some sort, to demonstrate its intelligence.

These two behaviors, spontaneous learning and creation, are the goalposts I have set for myself. My architecture, NLCA, must be able to spontaneously learn anything and, ultimately, be able to create novel and valuable intellectual output. Right now, the most sophisticated AI systems can win at any game, yet we have no AI capable of building games. An AGI should be able to learn to play any game, but also deconstruct the process of writing a game, write the code for the game, and test the game.

### Philosopher in a Library

Several animals have evolved language, including prairie dogs and dolphins. In all cases, language evolves primarily due to social pressures. There are many evolutionary advantages to social and communal living – safety in numbers! But these advantages come with the added complexity of getting along. Social living requires us to keep track of social order and fairness, which means we must transmit our needs and observations to our tribe. Once we achieve the ability to share what is in our mind, we also gain the ability to share hunting strategies and food locations – an incredible evolutionary advantage! The need for speech then creates its own explosive evolutionary pressure. Dolphins, for instance, have adaptive hunting strategies. In captivity, it has been shown that dolphins can communicate their intent to improvise with each other before doing tricks. Prairie dogs can describe threats to their den. Koko the gorilla was taught to communicate with sign language, and she was able to react to the news of Robin Williams’ death by expressing her sadness. More comically, she once ripped a sink off a wall and blamed her kitten. This single anecdote reveals much about the evolution of language and Koko’s abilities. First, she knew that what she did was wrong. As a social species, gorillas must keep track of right and wrong, and who to trust. But also, as a social species, gorillas can use deception and misdirection – she lied so that people might not know of her wrongdoing. This means that gorillas possess some “theory of mind” – they are aware of their perspective as well as other perspectives. They keep track of what is and is not in various minds. Gorillas have not naturally evolved language, but Koko clearly has much of the prerequisite neural machinery for language. This fact provides evidence that several social cognitive abilities predate spoken language, and that those abilities must be in place before language can evolve.

While communication and language are not unique to humans, written language absolutely is. No other species has even come close to the invention of written language. It is true that spoken language is instinctual while written language is not – children spontaneously learn speech as toddlers, but it takes several more years of diligent practice and instruction to become literate. Because of this disconnect between spoken and written language, we can surmise that our brains are flexible enough to translate our thoughts and observations into symbolic representations, but that literacy is not an ability that we have evolved to master yet. Perhaps, given the importance of reading and writing, humans will eventually evolve a natural affinity to put pen to paper. For now, keep in mind that writing is the primary ability that sets us apart from animals. Books are humanity’s superpower. We can encode decades of our own experience into books – our thoughts, senses, observations, narrative histories, and arbitrarily abstract concepts. We can write books about literally anything: history, philosophy, math, ethics, medicine, fiction, etc. Books allow us to transmit knowledge, wisdom, and ideas across time and space – a feat that spoken language alone cannot.

Consider just how much we humans learn from books. Most of our knowledge and abilities are captured in text. Whether you want to build a moon rocket or perform surgery – most of the knowledge to do so is recorded in natural language. Natural language, in this case, is a specific term referring to languages that have organically emerged from human cultures. These languages include those such as English, Farsi, Japanese, and Swahili. The alternative kinds of languages are constructed languages and computer languages. The most famous constructed language is Esperanto, but many fictional worlds also contain constructed languages, such Elvish from JRR Tolkien’s Lord of the Rings. Computer languages include such examples as Java and Python, two of the most popular programming languages in the world.

Natural language is infinitely flexible and can capture almost any idea or experience. Our brains have an internal language that Steven Pinker refers to as mentalese – inarticulate and abstract thoughts that are not readily rendered into language but can be translated if needed. For instance, we do not have many words for smells, even though we can recognize thousands of them. Something might smell sweet or acrid, but most of the time, we say something smells like something else, like bananas or roses or wet dog. Another example – you do not plan your footsteps in natural language, but if pressed, you can describe your path-planning process with words. Either way, walking is mostly handled by the brain stem and therefore falls below the concern of executive cognitive reasoning. Walking is not an intellectual task, therefore immaterial to AGI. All thoughts and sensations, therefore, are just information and signals with representations in the brain, mentalese. Mentalese can be translated into any number of representations, so why not represent it entirely in natural language? Works of fiction do this quite well, where authors convey all five senses, internal monologue, and even abstract thoughts, memories, and dreams all in natural language. Therefore, I believe that natural language is a sufficient medium to represent any idea, experience, sensation, thought, or memory.

Since written language can represent everything, then it follows that any intellectual activity may be approximated by manipulation and processing of text. In computer science, the domain of text-based processing and manipulation is called NLP – Natural Language Processing. Therefore, my assertion is that NLP is more than enough to achieve AGI. Now, while I believe that text-based intelligence will be more than adequate to construct an AGI, I do not believe that NLP will be the only method. There are competing theories about what is and is not necessary to achieve AGI, and I believe that there will be single-mode architectures, such as NLCA, and multimodal architectures that integrate several types of representations. For instance, someone else might come along and create an AGI that “thinks” in images and sounds, rather than language. Increasingly exotic and abstract representations may be possible in the future, but such speculation falls beyond the scope of this book.  

Now, imagine that a philosopher is sitting alone in a library with no doors and no windows. The library is equipped with every book ever produced by humanity, plus a writing desk and a comfy reading chair. The philosopher’s only interaction with the outside world is via letters. They receive letters from the outside world via a mail slot, through which they can also send letters back out to the world. The philosopher can use the letters to request more information about the outside world and use the library to research whatever they need, compiling binders of notes and stacks of books to help them compose those outbound letters. They then send out their letters and await a return. This philosopher-locked-in-a-library model is the best way to think about NLCA, as it communicates entirely via missives, postal letters exchanged between its inner world and the outer world. 

Lastly, imagine that the philosopher keeps a diary or a journal about their thoughts and activities in the library. They never send their diary out. Imagine they receive a letter with novel and interesting concepts, and they wish to continue thinking about those concepts after they have researched and sent out a reply letter. They perform many of the same activities that they did to compose an outbound letter, but instead they record this new information in their diary. We humans use diaries to record our thoughts and feelings, to help us make sense of life and its complexities. Humans who keep diaries tend to be more emotionally intelligent and successful. This secondary behavior of keeping an internal diary is also a key component of NLCA.

The Natural Language Cognitive Architecture is the blueprint for a machine that thinks in plain English (or whatever language you choose), and this philosopher-locked-in-a-library model is one way to think about the behaviors that amount to artificial general intelligence. 

I propose that natural language is the best medium for an AGI’s cognitive architecture for a few reasons. First, natural language is infinitely flexible. Almost every sentence you ever read or utter will be entirely unique, and yet your brain can interpret and synthesize sentences. This means that any concept, event, idea, or object can be described with natural language. Secondly, natural language lends itself to interpretability – we do not want an AGI that will be a blackbox! Instead, we want to be able to deconstruct every decision our AGI makes and observe its thinking in real-time. With natural language, the AGI cannot obfuscate its intentions. Thirdly, NLP is a large and well-established domain of computer science – we have all the tools we need!

### Longhand Demonstration

In this demonstration, I will walk you through the process of how NLCA works by breaking down learning and cognitive behaviors into text-based functions. This demonstration is not completely exhaustive of NLCA’s functions, but it will orient you to the task of translating cognitive functions into text-based functions.

Look at your surroundings and recent events. This forms your “context”. While many of your observations and sensations are not represented in language, you could describe your context with words if you like. You can describe where you are, what you are doing, what you are thinking, your current actions, and goals all in natural language. The context is your external state.

What about your internal state? Your internal state is your stream of consciousness or working memory. This is your subjective experience of having thoughts, sensations, and self-awareness. It also contains your identity and values, or ego. Once again, much of your internal state is not automatically represented in natural language but you could easily describe your internal state with words. This internal state is what I call the “corpus” in my theory.

How do you express your intelligence?

You recall memories, procedures, and facts into your working memory. This process is almost entirely automatic. Remember your tenth birthday? See how with four simple words I forced you to recall a (hopefully) happy moment. What about complex tasks or problem solving? It is much the same – you recall recent and similar experiences as well as procedures that aid you in addressing a problem. These neurological functions are approximated in my theory as a knowledge system, an iterative and recursive interaction with a database, where understanding is layered over time. This layered, iterative increase in comprehension enables NLCA to generate progressively more valuable and creative output – the highest tier of Bloom’s taxonomy.

You can test NLCA yourself with the following procedure. Grab a pen and paper and transcribe your thoughts and decision-making process.

1.	Write out your context.
	- Senses
	- Observations
	- Recent actions
2.	Write out your corpus.
	- Current thoughts and memories.
	- Questions about what you are doing and why.
	- What your next goals and needs are.
3.	Generate your output.
	- Write out answers to the above questions.
	- Generate some ideas about next actions.
	- Evaluate those actions against your values and needs.
	- Choose an action based on those evaluations.
	- Execute your action.
4.	Keep a separate sheet of paper strictly for yourself.
	- Record notes, thoughts, and expectations.
	- Journal about your emotions and feelings.
	- Track your progress and projects.

Here is a brief example of what you might have written:

```
Context: I am sitting in my favorite reading chair. I hear the clock ticking and a dog barking outside. I just got home from work. I am reading this book about AGI.

Corpus: What does my tenth birthday have to do with AGI? I’m reading this because I’m curious. How exactly did this guy figure this out? I really don’t believe him yet.

Output: I’ve got about an hour before dinner so I guess I can read a bit more.
```

I will walk you through the logic and practical implementation of this exercise in machine code throughout the rest of this book. I will also provide many examples of transformer outputs so you can see exactly what generative transformers are capable of and how to use them. In all cases, it will have a similar format to the above, where human-written text is bold and machine-written text is plain. I used OpenAI’s DAVINCI-INSTRUCT-BETA engine to generate all such output unless otherwise stated. OpenAI is a non-profit research company founded by Elon Musk, among others. The DAVINCI-INSTRUCT-BETA engine is one of their AI services, a text-based deep learning tool that will be described in greater detail in chapter 1. The DAVINCI-INSTRUCT-BETA engine is part of their famous GPT-3 technology.

### Up Next

This book is divided into five parts. This first part, the introduction, is what you are presently reading. In this introduction I gave you some background about myself, my motivations, and my goals. Then I established some definitions and expectations about AGI. Lastly, I gave you an analogy for NLCA and an example so you can start with a high-level understanding of how my cognitive architecture works. Starting with this framework, you should be able to integrate the rest of the book and develop a solid mental model of NLCA.

The second part, Part 1, will start by defining and describing the core technology underpinning NLCA: generative transformers. Next, I will describe cognitive architectures, what they are, and how they are used. Lastly, I will give a broad overview of NLCA. This thirty-thousand-foot-view of NLCA will then be iterated upon in Part 2.

Part 2 will take a much closer look at each component of NLCA, examining the theory and implementation of each. Part 2 will focus on describing the design paradigms of each component as well as how every component interacts with each other.

Part 3 will discuss important topics around and within NLCA, such as the practical steps to implement NLCA in code and the ethical concerns of NLCA and AGI. This section will also address issues such as the control problem, inner alignment, and outer alignment – how do we implement AGI in such a way that it will not murder us all?

Finally, the book wraps up with appendices and a bibliography. The appendices contain dozens of examples to assist you. These examples should aid your comprehension and implementation. The bibliography contains many of the works that served as source material and inspiration for NLCA.

# Part 1 – Overview

This section of the book is divided into three chapters. The first chapter describes “transformers” – a novel type of deep neural network. Transformers are the first general-purpose machine learning technology, meaning they can address a variety of problems without special training. This chapter will also describe how transformers are used, which is critical information to understand the implementation of NLCA.

The second chapter describes cognitive architectures: what they are and why they are important. After all, this book proposes a new type of cognitive architecture, so it is critical to understand what already exists in this field.

The last chapter of this book introduces you to NLCA. I will give you a high-level overview of the architecture of NLCA and describe the major components. 

## Chapter 1 – Transformers

### What can transformers do?

First and foremost, generative transformers generate text. This can take many forms; they can write fiction, instruction manuals, screenplays, and product descriptions. They can also generate ideas, follow instructions, and answer questions.

![Transformers are fed text instructions; their output is also text.](https://github.com/daveshap/NaturalLanguageCognitiveArchitecture/blob/main/images/02%20transformer%20behavior.png?raw=true)

In the following example, I fed the bolded instructions to the transformer, and the rest was written by the machine. Now, this is not a good sonnet, but you can see how transformers are capable of complex tasks. Many semantic and conceptual embeddings were required to generate this output:

```
Input: Write a sonnet about tiny dragons in the style of Shakespeare:

Output: How does it feel to be a tiny dragon
Stuck with a wingspan shorter than your stature?
Is it better than being a normal dragon
And being able to take down whole villages in a single night?
I suppose it depends on how you compare it
To your past life as a human, which was always a drag
You may not be able to fly as high or as far
But at least you had a life, and not just a cold corpse
As a tiny dragon, you're free to fly
To any heights you please, and there's no one to know
```

In order to generate this sonnet, the transformer needed to understand (1) my instructions, (2) what a sonnet is, (3) what William Shakespeare’s style is, and (4) imagine what a tiny dragon might do. There is a lot going on under the hood.

Here is another example where I ask a transformer to come up with a list of possibilities:

```
Input: Lynn is a stressed out grad student. What are some things that might make her feel better?

Output: 1. Getting a massage.
2. Going for a walk outside.
3. Playing with her dog.
```

Again, the machine demonstrates an ability to abstract instructions and generate relevant output. In this second case, the transformer clearly understands the concept of stress as well as what it means to “feel better”. This ability to work with squishy or vaguely defined concepts is monumental! Never before have computers been able to engage with soft goals such as these.

### How do you use transformers?

The primary method to interact with transformers is via prompts. Remember that a transformer is basically just a text-completion engine, so you need to prime it with some food for thought. The prompt can be anything from a simple question, a snippet of news, a chapter of fiction, or even code. 

There are two overarching kinds of prompts: zero-shot and few-shot. With zero-shot, you give the transformer instructions or text, and it just goes, such as the previous two examples. With few-shot prompts, you include one or more examples of the output you want to see, and the transformer learns to generalize the instructions from there. The two prior examples are zero-shot because I gave the transformer no examples, only instructions. The bold part of the previous examples is the prompt while the plain text was generated by the machine.

Prompts can be statically written, fill-in-the-blanks (composed), or dynamically generated. I work with a variety of types of prompts throughout this book, most of which are hybrids of these types. You can even write prompts designed to write new prompts; a technique called a metaprompt. Research into metaprompts is ongoing.

Static prompts are written by hand and do not change. These have limited flexibility but sometimes that is a good thing, such as when you want the morals and values of the system to remain the same. Static prompts form the backbone that gives AGI entities consistent beliefs and behaviors. Think about Isaac Asimov’s “Three Laws of Robotics”. Such a set of imperatives could be implemented as a static prompt.

Composed prompts are partially static with a few sections that can be populated (filled in) on the fly. Sometimes the blanks are small – just a few words or a question. Other times the blanks are several paragraphs, as with question-answering problems. With a question-answering prompt you might populate the question and/or some text-based knowledge with which to answer the question. Say you want to ask a question about Venice, Italy, so you populate the prompt with the Wikipedia article on Venice and your question. Unfortunately, most Wikipedia articles are too large for transformers today, so you need to pare down the input. More on that topic later.

Dynamic prompts are mostly (or entirely) created by previous outputs from static or composed prompts. This means that the prompt can be completely different based on the needs of the system. This concept of feeding the output of one prompt into the input of the next is called prompt chaining. Prompt chaining is one of the key abilities that enables transformers to think about anything and address any situation, especially when combined with facts from empirical sources.

### Why are transformers important?

Generative transformers represent a watershed moment for machine learning and artificial intelligence. For the first time, we are pivoting from narrow-AI to general-AI. Instead of being trained to do one task extremely well, generative transformers can do just about any text-based task. Transformers are a revolutionary technology, like antibiotics for medicine or the internal combustion engine for automobiles. This general-purpose utility of transformers is only just being explored, but already they are changing the tech world. 

Transformers can behave as a general-purpose cognitive engine, iterating over short tasks in a highly flexible manner. For instance, they can confabulate explanations for scenarios, generate follow-up questions, and infer causal relationships. These abilities are remarkable, but they are atomic, able to work well only on short chunks of text. This leaves us with the need to string these abilities together into a larger system, a cognitive architecture. Transformers are the single most important building block for achieving AGI to date.

### What is a transformer?

Generative transformers are the keystone technology that enabled me to create NLCA. The transformer architecture was originally invented by Google in 2017, and it is an evolution of previous deep neural network designs, such as LSTM (Long-Short Term Memory) and RNN (Recurrent Neural Network). These two types of neural networks eventually gave rise to transformers. The key thing to know is that a transformer uses an encoding/decoding loop. This loop “transforms” an input into an abstract, embedded representation like mentalese, called a vector. A vector is just a series of numbers. Then the transformer uses that abstract internal representation to “decode” the output into something else, depending on the task. If this sounds like a blackbox that is because it is. There are many researchers working on understanding these abstract internal representations so that we can explain exactly how transformers are able to perform tasks. We can, however, empirically demonstrate their value, accuracy, and reliability.

This seemingly magical ability to transform any text – including complex instructions and concepts – into abstract representations and then produce any desired result is why we are talking about transformers. 

A transformer, in this context, is a type of deep learning neural network. They work by encoding an arbitrary amount of text into an internal representation and then decoding the output stream into some other text. Some of the predictive text and autocomplete you see on your phone and Google searches use transformers today. Transformers got their name because they encode and decode, hence transform, text from one thing to another. You can use transformers to predict the next word in a _______. Sentence? Your brain does the same thing. You can also use transformers to translate between languages, predict news articles, and generate lists of items such as questions and ideas.

![Scheme of a transformer neural network.](https://github.com/daveshap/NaturalLanguageCognitiveArchitecture/blob/main/images/03%20transformer%20neural%20network.png?raw=true)

For all intents and purposes, transformers are textual autocomplete engines. However, instead of just completing the next word or two, I use them to complete sentences and paragraphs. These types of transformers are called generative transformers. The largest transformers today are trained on hundreds of gigabytes of text – so much that it would take a single person hundreds of lifetimes to read it all.

This training process creates “embeddings”. Embedding happens in layers. First, the transformer just learns the basic syntax of a language – sequences of characters form words and rules govern those sequences and patterns. After a while, the transformers start to embed associations. The word king is somehow related to the word queen. Later, those word embeddings are linked to even more concepts like monarchy, which is linked to government and revolutions. This level of embedding is called “semantic embedding” – meaning that the neural network has learned the semantic meaning of words and how they associate with each other. Finally, higher order conceptual embeddings emerge. These conceptual embeddings allow neural networks to engage in meaningful conversation and follow instructions. The concept of monarchy is fully embedded in the transformer, along with millions of other concepts. 

### What are the strengths of transformers?

Transformers are trained on many hundreds of gigabytes of text information. This includes all of Wikipedia and Gutenberg, thus they have many lifetimes worth of knowledge and wisdom embedded. This means they are more than just repositories of facts; they can generate hypotheses, complex evaluations, fiction, and code. Because of this ability to generate, creation is intrinsic to transformers.

These embedded concepts are akin to human mental models. A mental model is an internal representation of how something works and behaves. For instance, you might have a mental model of your dog – you know what it needs and prefers, as well as how to interact with it. Mental models allow us humans to rapidly interact with our world and predict outcomes. 

This combination of embedded concepts and knowledge enables transformers to work on all kinds of tasks, from explaining the internet to neophytes to evaluating moral and ethical conundrums – transformers have read more philosophy books than any human ever has. This flexibility is a powerful asset, but also a liability, as we will explore in a moment.

Lastly, transformers can be fine-tuned. This is a technological process of using additional training data to increase the performance of transformers for specific tasks. For instance, you can start with a general-purpose transformer and then finetune it with science fiction books, resulting in a transformer that is even better at writing science fiction. This ability to be fine-tuned allows transformers to be customized very easily. Fine-tuning datasets can also reduce problems like bias, racism, and false beliefs.

### What are the weaknesses of transformers?

Transformers are given to harmful bias and confabulation. They are trained on human text, some of which contains bigotry, intolerance, or false information. Large transformers can easily be used to generate racist, sexist, violent, or misleading content. I will not be demonstrating that capability in this book but suffice to say it is there and it is a major concern. Confabulation is the tendency to just fabricate ideas on the fly. Transformers have no idea what is real or fake – they only know language and the text they were trained on. Transformers have never experienced the concrete world so, to them, fiction and nonfiction are the same. Fortunately, confabulation can be reduced by using bits of factual hard data to stay on track.

Transformers are completely stateless – they do not remember anything from one execution to the next. Perhaps future types of transformers will have the ability to recall past states, but for now we must build logic around the transformer to remember everything. One way to think of it is that transformers have severe amnesia – they treat every interaction the same. 

Lastly, large transformers today can only handle small amounts of text before they forget what they were doing. You, as a human, can read and retain an entire book, but transformers can only process a few paragraphs with any level of cohesion, thus their performance falls apart with complex or long tasks. This means that we need to break problems down into smaller steps, which adds a huge design burden.

I expect these problems will see rapid improvement over the next few years. As transformers improve, it will be easier, faster, and cheaper to implement NLCA. For instance, the small text window is presently a limitation of transformer architecture and a phenomenon called “attention” – the longer a task is, the more sophisticated the attention mechanism must be. This is an active field of study, both in transformers and in cognitive architectures. I also hope to see additional controls over transformers, such as the ability to switch off confabulation and bias. Again, some of those problems can be addressed simply with fine-tuning, but creating fine-tuning datasets is cumbersome, so hopefully we see better, more flexible transformers soon.

###Summary

Transformers are a powerful new technology, only a few years old. Transformers can generate any text in a similar way to autocomplete on your phone and Google searches. The difference, though, is that larger transformers can autocomplete entire paragraphs. Furthermore, transformers are trained on millions of pages of text, so they “know” a lot about the world, including complex concepts like philosophy and science.

The primary way to interact with transformers is to give them a little bit of text, which serves as “food for thought”. Whatever text you give a transformer is called a prompt. Prompts tell the transformer what kind of text to generate. Prompts can include instructions, questions, facts, and even morals.

While transformers are immensely powerful, they have some limitations. First, transformers can only take in a few paragraphs of text at a time. Likewise, they can only generate a few paragraphs before they “forget” what they were doing. This means they can only do short tasks for now. Another flaw with transformers is that they do not know the difference between reality and fantasy – they only know language. There are a few techniques to work around these drawbacks, which we will discuss in this book. Also, these problems are actively being researched, so we should expect transformers to improve over time.
