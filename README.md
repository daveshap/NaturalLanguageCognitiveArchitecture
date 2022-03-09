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
Context: I am sitting in my favorite reading chair. I hear the clock ticking 
and a dog barking outside. I just got home from work. I am reading this book 
about AGI.

Corpus: What does my tenth birthday have to do with AGI? I’m reading this because 
I’m curious. How exactly did this guy figure this out? I really don’t believe him 
yet.

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

### Summary

Transformers are a powerful new technology, only a few years old. Transformers can generate any text in a similar way to autocomplete on your phone and Google searches. The difference, though, is that larger transformers can autocomplete entire paragraphs. Furthermore, transformers are trained on millions of pages of text, so they “know” a lot about the world, including complex concepts like philosophy and science.

The primary way to interact with transformers is to give them a little bit of text, which serves as “food for thought”. Whatever text you give a transformer is called a prompt. Prompts tell the transformer what kind of text to generate. Prompts can include instructions, questions, facts, and even morals.

While transformers are immensely powerful, they have some limitations. First, transformers can only take in a few paragraphs of text at a time. Likewise, they can only generate a few paragraphs before they “forget” what they were doing. This means they can only do short tasks for now. Another flaw with transformers is that they do not know the difference between reality and fantasy – they only know language. There are a few techniques to work around these drawbacks, which we will discuss in this book. Also, these problems are actively being researched, so we should expect transformers to improve over time.

## Chapter 2 – Cognitive Architectures

### What is a cognitive architecture?

A cognitive architecture is a model of the human mind or brain, either theoretical or implemented in code (and often both). Because cognitive architectures are models of brains, they borrow a lot of terms and concepts from psychology and neuroscience. Cognitive architectures generally address topics such as perception, learning, problem solving, and task execution. They are used extensively in the field of robotics and simulation. For instance, the Mars rovers use cognitive architectures to achieve some level of autonomy, as do many deep-sea robots. Cognitive architectures are also used in video games to give characters realistic behaviors. In essence, a cognitive architecture is one way to create a “thinking machine”.

![The input-processing-output loop is the fundamental model of robotics.](https://github.com/daveshap/NaturalLanguageCognitiveArchitecture/blob/main/images/04%20simplest%20cognitive%20architecture.png?raw=true)

### How does a cognitive architecture work?

The input-processing-output loop is the main model of robotics, the simplest cognitive architecture, and how every living entity behaves. From amoebas up through humans, we all receive input (stimulus) from the environment, have some internal reaction (processing) and then produce some response (locomotion, chemical, etc.). These three steps form a feedback loop with the outside environment, where the action/output impacts the world and changes its state, thus influencing the next input. 

Think of putting your hand on a hot stove by mistake. You receive input – heat and pain – and your brain generates a signal to protect yourself, to withdraw your hand. This input-process-output cycle is extremely fast, and it results in the cessation of the pain: alleviation of suffering. The alleviation of suffering (response to negative stimulus) is universal to all living things, and figures into the design of NLCA.

Now think about the problem of landing on the moon. How do you do it? You go to college to study physics and engineering and network with fellow engineers. Finally, you land a job with NASA or another space agency. Then you engage in countless input-process-output loops as you tackle one problem after another. Even as you watch your rocket ascend into the atmosphere, your brain is taking in input, interpreting the telemetry from the rocket, and generating output – especially when it succeeds, and you cheer wildly. All the while, the rocket’s computers are performing millions of input-process-output loops as it measures the temperature and fuel flow going into its engines, checking its course and trajectory, and always on the lookout for mission-critical faults.

Cognitive architectures attempt to capture, describe, and model all these features of living systems, brains, and minds. It all boils down to loops.

### What cognitive architectures already exist?

The most influential cognitive architecture is Soar, created by John Laird, Allen Newell, and Paul Rosenbloom at Carnegie Mellon University in 1982. The following is a simple diagram of the Soar architecture:

![Simplified version of the Soar cognitive architecture.](https://github.com/daveshap/NaturalLanguageCognitiveArchitecture/blob/main/images/05%20soar%20architecture.png?raw=true)

There are a few structural differences between NLCA and Soar as well as numerous differences in implementation. First, Soar treats long term and short-term memory differently where NLCA does not, instead, NLCA uses several attention mechanisms to prioritize memories and metadata to keep track of types of memories. Second, Soar does not attempt to model the stream of consciousness or inner monologue. Soar does model many other aspects of human cognition, however, by incorporating and modeling theories of intelligence, learning, memory, and perception. Soar is more aptly suited to tasks like robotics and autopilots than NLCA. If they were to be transformed into people, Soar would be a fighter pilot, while NLCA would be a philosopher.

Other architectures, such as ACT-R (Adaptive Control of Thought—Rational, “Actor”) attempt to model the physical brain, rather than the psychological mind. Where a model of the brain is based on the physical structure and connectivity within, a model of the mind is more abstracted, as NLCA and Soar are. The paradigm of modeling the mind is why architectures like Soar and NLCA borrow heavily from psychological terms like working memory and stream of consciousness.

### Summary

Cognitive architectures have been around for a few decades and are used extensively in robotics and simulation, which includes video games. Cognitive architectures are designed to mimic the brain or the mind of humans. Some architectures favor the psychological mind and cognition while others try to emulate the physical construction of the brain.

Researching human cognition and intelligence is important because, so far, humans are our one and only model of general intelligence. Yes, there are many other intelligent animals like octopi and ravens, but while they are very clever, they do not measure up to humans. As such, our best bet for modeling general intelligence is to copy something that already works: our own brains. Lastly, cognitive architectures are all about loops – feedback loops between the inner world of the architecture and the outer world, or environment.

## Chapter 3 – NLCA Overview

### Architecture Snapshot

At the risk of oversimplifying and underselling my work, NLCA is merely the merging of transformers with cognitive architectures. Structurally, NLCA is composed of two loops that share a common database. The outer loop is based on the universal model of robotics (input-processing-output). The inner loop is based on a combination of inner monologue and diary writing behaviors in humans. The link between the two loops, the shared database, allows these two otherwise independent loops to influence and build from each other. 

![NLCA architectural diagram](https://github.com/daveshap/NaturalLanguageCognitiveArchitecture/blob/main/images/01%20architectural%20diagram.png?raw=true)

### Outer Loop

The outer loop contains three steps: context, corpus, and output – like the universal input-processing-output loop of robotics. This is considered an “open loop” because it is not self-contained, it is “opened” to the environment. There are several key differences at each step, hence the unique names. The context is a particular type of input, where everything is captured in text as you saw in the longhand demonstration at the beginning of the book. The corpus is not just mere processing, but also includes memory, inference, and planning, all in one step. Lastly, the output is not necessarily motor or verbal action, as demonstrated with the philosopher-in-a-library analogy. The output is a text payload which can include all kinds of output behaviors, depending on the specific purpose of your NLCA implementation.

The context is passively generated from the environment in the same way that our human senses are autonomic. In some cases, the context is generated from sensors like cameras and microphones while in others it is received as chat logs, emails, or other text data. The only requirement is that the context is like a letter, a payload of natural language text. Sensor telemetry, such as cameras and microphones, can easily be transcribed with technologies such as automatic video annotation (using a machine to describe images and videos with text) and ASR (automated speech recognition). All signals are just data, and all data can be rendered as text.

After the text-based context is received, the corpus is composed, which is meant to model stream of consciousness, working memory, and ego (or sense of self). The corpus is composed by extracting insights from the context and retrieving relevant documents from the shared database. The documents are evaluated through various methods, such as basic summarization, and by asking pointed and salient questions such as “What should I say or do in this situation?”. The shared database also contains a special kind of document called a dossier, which is generated by the inner loop. Dossiers are inner thoughts that NLCA uses to better decide how to respond to external events, keep track of plans, and learn about the world. In effect, dossiers are like diary entries and private notebooks. By now, the corpus should contain facts, memories, moral evaluations, ideas, and plans.

Lastly, the output is derived from the corpus with special prompts. The output prompt needs to be specially crafted depending on the use case for NLCA. For example, an output prompt for a chatbot will be structured differently than an output prompt for email, even though the ultimate output is still text. In other cases, such as speech, video game character control, and robotics, the output prompt will need further interpretation. For instance, a speech output might be I say “Please do not step on the grass” while a robotic command might be: Locomotion: I walk towards the car but stop one meter away. The robotic platform would then need to interpret that command, which will be discussed later in this book.

### Inner Loop

Meditation, contemplation, inner monologue, dreams, and diaries were all the inspiration for the inner loop. These are “closed loop” behaviors because they all stay inside your head and no outside input is required. When you sit down to write in your diary or journal, how do you select the topics to write about? Often, you rely on your stream of consciousness, and then you free-associate, so you may not be conscious of how your brain chooses topics. Neuroscience, however, gives us the answer.

Human brains prefer to think about things that are both recent and novel. You are far more likely to write in your diary about the day you just had than to write about the distant past, and if you do write about anything from years prior, it is because something about today reminded you. Human memories also work by association, and NLCA allows for older memories to be dredged up by association in the same manner. About novelty: you are also far more likely to write about the distinctive events of the day rather than the mundane. Would you prefer to write about tying your shoes in the morning or the fact that your neighbor has a brand-new neon-orange Audi?

Why is this? Why do we prefer to think about recent and novel events?

There are many evolutionary and practical explanations for this preference. When our ancestors lived on a savannah, novelty could mean opportunity or danger. Imagine you are a paleolithic human who comes upon a berry bush you have never seen before. Your brain generates a strong novelty signal – are these berries delicious or deadly? Your attention is immediately captured. You wrack your brains – have you ever seen anything like this? Has anyone in your tribe ever died from berries? What are the risks and rewards? Coming upon this berry bush is both recent and novel. You are going to be thinking about the bush rather than the rainstorm that happened several lunar cycles prior. Novelty and recency are the primary attention mechanisms in our brains when dealing with the external world.

There is another mechanism that we rely upon for long-term planning, tracking goals, and ensuring that we do not forget anything. This third mechanism is based on neglect, although it is used less frequently. Think about a time when a big problem was looming, and you just could not stop thinking about it. Maybe it was time to do taxes and you simply put it off because taxes are such a pain. You refused to think about taxes, thus neglecting them, but your brain kept track of the neglect and the importance. Thus, the inner loop also has a neglect-attention mechanism, scavenging for memories and tasks that have fallen through the cracks. 

While the outer loop is concerned with real-time performance, the inner loop is concerned with what to think about, and why. This is like how your mind drifts when you get in bed in the evening. Suddenly there is nothing immediate or novel to think about in your external world. You are comfortable and safe in familiar surroundings, so your brain goes foraging for recent, novel, and neglected memories to mull over. This scavenging is an important behavior. It is so important, in fact, that it extends into our dreams. More than half of our dreams are our brains replaying and experimenting with recent experiences. In this way, the inner loop of NLCA is also akin to dreaming, and interestingly, I originally called the inner loop the “sleep service” but decided that was too vague and anthropomorphic. NLCA can, effectively, dream while it is “awake”.

These three attention mechanisms are brought together as a search function. The search function in the inner loop is the scavenging protocol, looking through the shared database for recent, novel, and neglected memories. Once it identifies a target memory, it distills the features of that memory down into a kernel, or a topic. From there, related memories and facts are compiled, using the kernel as a basis of search. Once all related memories and facts are compiled, evaluation begins. NLCA generates questions and hypotheses about the kernel and associated memories. Take the bright-orange Audi example – you might ask yourself “How much did that cost? Is Bill going through a midlife crisis? Maybe he’s getting a divorce and wants to attract a younger woman?”. These questions and explanations are all added to the pile of related facts and memories and composed into a dossier. The dossier is the final product of the inner loop.

The dossier is stored for later use, such as the next time you see Bill. You will easily remember the possibilities you imagined so you can use those ideas to talk to Bill. Dossiers can be composed on any topic, be it a person, event, concept, task, or news article. Imagine you are making coffee one day, but your dog starts barking madly, so you pause your work to investigate. After letting the dog out, your mind somehow reminds you that you were making coffee and so you return to the task to pick up where you left off. This is how the dossiers are used. Dossiers figure into longer-term projects as well, such as building moon rockets. The larger and more complex the task, the longer or more numerous the dossiers.

### Shared Database

The shared database contains everything: memories, empirical facts, books, news, past conversations, corpuses from the outer loop, dossiers from the inner loop – all differentiated with metadata. Metadata is “data about the data”, such as where it came from, what it is about, and when it was collected. Remember that transformers are intrinsically stateless, so the database must be used to maintain persistence. It is true that NLCA can function without a database, though it behaves like a person with acute amnesia. By the end of a short conversation, NLCA will have forgotten the beginning of the conversation. Most chatbots operate in this manner today – completely stateless.

The database allows NLCA to repeatedly iterate through ideas and memories, thus building up better understanding over time. This iterative improvement covers all topics, including people it interacts with or problems that it was asked to work on. When NLCA returns to an external task, prior dossiers will be recalled and used to proceed on that task. New information will then be integrated on subsequent passes.

Since recency is a key attention mechanism, you already know that the database needs to timestamp everything. In fact, metadata is critical for the database to function properly. Where did a memory come from? Was it a context or an inner loop dossier? Entries in the database require quite a bit of metadata to keep track of where and when they came from. Humans are no different, though. In general, you can remember where and when you learned a thing. Did your friend tell you about a bit of news or did you read it online? Did you learn about physics from university or Wikipedia? Information literacy, the ability to handle information truthfully and reliably, relies on remembering sources of information because not all information sources are created equal. Thus, metadata is critical for every bit of information that goes into the database.

The database is shared between the inner and outer loops. The outer loop stores contexts, corpuses and outputs while the inner loop stores dossiers. You can also populate the shared database with news, books, papers, and other bits of knowledge. In all cases, metadata must be included.

### Up Next

We have come to the end of Part 1, the overview. In this section of the book, we have described transformers, how to use them, and why they are important. Transformer technology represents a watershed moment in the path to AGI in that these are among the first machine learning models that are truly general-purpose. Furthermore, we established some basic facts about cognitive architectures and briefly looked at existing models. Lastly, we got a high-level overview of NLCA: the inner and outer loops as well as the shared database. Up next, in Part 2, we will take a closer look at all the components of NLCA and unpack their functions and interactions.

# Part 2 – NLCA Components

Welcome to Part 2! In this section of the book, we will look at each component of NLCA under a microscope. Each chapter opens with a section outlining the underpinning theory behind the component. In these theory sections, I will tell you where the inspiration for the component came from, how I came up with it, and what it is meant to model. In that way, the theory section will tell you why the component is relevant and important. From there, I will give you analogies and descriptions about the inner workings of the component.

Finally, I will conclude each chapter with a summary – a brief recap of the component, its theory, and its operation. Here is a list of the components in this section:

- Outer Loop
- Shared Database
- Context
- Corpus
- Output
- Inner Loop

## Chapter 4 – Outer Loop

### Theory

At the highest level, the outer loop is all about behavior. For the amoeba, the outer loop means fleeing from predators or chasing food; processing happens via biochemical reactions. For the person with their hand on the stove, the outer loop means yanking their hand back. The outer loop is the interface between the mind and the environment: input, processing, and output. With NLCA, this loop takes place entirely in natural language, which confers several benefits at the added cost of transcribing perception of the outer world into text, and then translating output text into action. This interaction with the environment is known as an “open loop” – its input comes from arbitrary exterior signals and its output returns to the same exterior space.

![The outer loop has three main phases. Each phase interacts with the shared database.](https://github.com/daveshap/NaturalLanguageCognitiveArchitecture/blob/main/images/07%20outer%20loop.png?raw=true) *The outer loop has three main phases. Each phase interacts with the shared database.*

The incoming information, the context, is stored in the shared database and is used to create part of the corpus. The context helps create the corpus through two primary methods: the first is that inferences are drawn from the context, such as user intent. Second, the context is used to retrieve related memories, facts, and dossiers from the shared database. The results from these two methods are compiled and summarized to form the first part of the corpus. Next, the corpus itself is fed to prompts that perform moral, ethical, and censorship judgments. Those judgments are appended to the corpus and, finally, the corpus is fully composed. The corpus is now used to generate output, which is sent back into the environment. The context, corpus, and output are all saved to the shared database for future reference by both the inner loop and outer loop. This way, NLCA records not only its input, but also its reasoning and output. This is a critical feature for explainability and transparency. Whatever an AGI says or does, it must be able to explain its reasoning, which necessitates storage of all “thoughts”.

### Context

The context is like an incoming letter, but where did it come from? Who wrote it? We will get to context generation in chapter 6, which is dedicated to contexts. For now, just remember the context is equivalent to perception or input. Anything that can be captured in natural language can serve as a context. Let us look at a few example contexts:

```
Context 1: James is taking his dog for a walk. They live in NYC. James' dog is a 
40 pound mutt. During their walk, another dog attacks James' dog. The other dog 
is a bigger pit bull. The other dog is barking aggressively and its owner is 
struggling to control the pit bull.

Context 2: At 8:02AM local time in Tokyo a massive earthquake was detected. The 
epicenter was located 140 km off the coast. National Oceanographic Services have 
predicted the seismic event will generate a dangerous tsunami.

Context 3: Bobby is talking to his friend Jenny. They met at a cafe. Jenny is 
reminiscing about their college days.

Context 4: Your kitchen is on fire!
```

A context can contain anything. It serves as the raw material of thought, the outline of a situation or problem, and the impetus for action. In the case of a lawyer NLCA, the context would contain all legal filings and court documents. For a medical NLCA attending a hospital patient, the context would contain the patient’s medical history, charts, lab results, and physician’s notes. The context can be composed in real-time from a variety of data sources: speech-to-text, databases, deep learning annotation of video and images, emails and text messages, news articles and social media, and so on. The content of the context depends upon the intended use case of NLCA.

![Overview of how a context is constructed.](https://github.com/daveshap/NaturalLanguageCognitiveArchitecture/blob/main/images/08%20context.png?raw=true) *Overview of how a context is constructed.*

Most situations and problems can be represented entirely in natural language, even if it is not necessarily the most automatic or comfortable method for us humans. Take the simple mathematical formula: Y = Mx + B. The following output demonstrates a transformer’s ability to abstract and reinterpret formulas in natural language:

```
Input: Translate the following formula into plain English: Y=Mx+B:

Output: The Y value is determined by multiplying the M value by the X value and 
adding the B value.
```

You can see that even unintuitive problems can be translated into natural language.

### Corpus

The corpus is a model of the human stream of consciousness and working memory. Corpus means “body”, as in “body of text”, and it is where the magic happens. Imagine the philosopher alone in the library, reading books and compiling notes as they prepare to reply to the letter they received. That stack of notes is the corpus, which is called a “task set” in cognitive neuroscience.

In NLCA, the corpus is a text document where all relevant memories, facts, and evaluations are compiled. Inferences and deductions are made from the context, salient questions are generated and answered by pulling information from the shared database, and NLCA’s sense of self and censorship are all added to the corpus. The corpus is, therefore, a nexus where all intelligent functions coalesce.

![Some of the items that might go into a corpus.](https://github.com/daveshap/NaturalLanguageCognitiveArchitecture/blob/main/images/09%20corpus.png?raw=true) *Some of the items that might go into a corpus.*

The types of inferences and memories compiled in the corpus depend greatly upon the context. Consider the differences between having a conversation with an old friend and discovering that your oven is on fire: these are starkly different contexts! Your brain can handle either situation with relative ease, but the kinds of information you need to succeed is quite different, as is what you need to do with that information. The world has a high variance and demands a universally flexible approach, and that need for flexibility is why AGI is so difficult to create. But the flexibility of transformers now enables us to address this problem, we have only to design a system that can make use of a transformer’s unique capabilities.

Every situation demands different insights, different questions, and different mental models. Let us take a quick look at how rapidly a transformer can adapt to a situation. We will choose the oven-on-fire context from above, and then follow it up with a generic, boilerplate question. This question asks the transformer to generate more questions, which serves as the foundation of open-ended computing with NLCA:

```
Input: My kitchen is on fire! What are the most relevant questions I should ask 
myself?

Output: 1. Do I have a fire extinguisher?
2. Have I called 911?
3. Do I know the location of my nearest fire hydrant?
4. Do I know the location of my nearest emergency exit?
5. What are my evacuation plans for my family, and pets?
6. Am I adequately dressed for the weather?
7. Do I have any water containers on hand?
```

The transformer can rapidly generate a few salient questions – this output took only a few seconds to create. As several friends of mine remarked while I was sharing my research: transformers are better at generating questions than many humans! These kinds of questions, as well as their answers, are stored in the corpus. The answers are generated by a question answering (QA) system, which is why QA is such a critical component of NLCA. Transformers are fantastic with QA, although they can be expensive to use, especially when you have hundreds of memories and facts to sus out. Some questions can be confabulated by the transformer on the fly, since transformers are trained with hundreds of gigabytes of data. These kinds of confabulated answers tend to be best if they are about historical, conceptual, and factual topics, such as the Great Wall of China. Temporal or local information, like weather or the location of a fire extinguisher, must come from the shared database.

Let us look at a few example corpuses. These corpuses contain answers to simple questions like “What’s going on here?” and “What should happen next?”. The following examples were all written by hand, but we will go into much greater detail about how to compose corpuses in chapter 7:

```
Context 1: Bobby is talking to his friend Jenny. They met at a cafe. Jenny is 
reminiscing about their college days.

Corpus 1: Jenny is feeling nostalgic. Bobby should share stories and reminisce 
with Jenny. Bobby remembers a story about staying out late with Jenny and 
missing the last bus so they had to walk across town together.

Context 2: I am an AGI. A human has asked me for romantic advice. It seems the 
human is in love with someone but the other person is reluctant.

Corpus 2: Perhaps the other person is uninterested or playing hard to get. I 
should warn the human of these possibilities so that they can brace for potential 
disappointment. If the other person remains reluctant, the human should disengage 
so as to avoid awkwardness.
```

### Output

Let us return to the philosopher locked in the library. Finally, they have done all the research, gone over the archives, read all the books, and tidied up their notes, and they are ready to compose an outgoing letter. They know what to say and why.

For the immediate future, NLCA’s output should remain strictly verbal or informational. That is to say that NLCA should not be embedded into robotic hardware or given control over physical systems any time soon. In line with this belief, my research has centered around generating verbal and textual output, however, the letters-from-a-philosopher can easily be translated to physical, empirical actions.

Here is a handwritten output from an example above, where a human is asking an AGI for romantic advice:

```
Output 2: It seems as though the other party is either uninterested or playing hard to get. Perhaps you should back off to see what happens. This will avoid awkwardness, embarrassment, and inadvertently making the other person feel unsafe.
```

Since all the morality, self-censorship, and reasoning was baked into the corpus, this output is ready to go. No one can predict the future, even if we can anticipate it with some accuracy over the short term. Instead, we all apply general principles learned from past experiences to future decisions. Thus, as NLCA gains more experiences, it will make better decisions. Even if verbal output is usually fairly low risk, bad advice can lead to disasters.

Still, there will eventually be a need for NLCA to control robotics so how do we map natural language output to physical actions? This problem is trivial and falls into the domain of robotics (just search for videos of homemade walking robots) so I will not spend much time on it, but I can give you some examples.

```
Input:
Context: I am a factory robot. I heard a metal crack and noticed a shelf moving 
that should not be. A human is standing near the shelf. They are wearing hearing 
protection and cannot hear the shelf or me.

Corpus: The shelf may be about to collapse. This could injure or kill the human. 
I should alert the human with physical touch to the danger and ask them to move 
away. If that fails, I should physically move the human to safety.

Output:
Procedure: (1) Tap the human on the shoulder and gesture at the shelf and show 
a toppling motion. (2) If they don’t move quickly I should carry the human a 
safe distance from the shelf.
```

The transformer generated the output, which can easily be translated to physical actions. This kind of planning may seem crazy for a machine, but transformers are more than capable of this level of reasoning. There are numerous examples of transformer reasoning in Appendix A, and we will go over many examples in the chapters ahead. Follow-up output prompts can be used to map squishier verbal plans into rigorous robotic commands as discussed in chapter 8.

### Environment

From the perspective of NLCA, the environment is a blackbox. Strange letters emerge from and disappear into the void of the environment, and sometimes responses come back out. The environment, which can be the real world you and I occupy, or a simulated world such as a video game or combat simulation, serves as a co-processor for any intelligent entity. The environment, as a blackbox, has a mind of its own and its own rules. Think about gravity for a second. Gravity is a rule of the environment that you and I learn about through interaction. To a baby born in zero gravity, who never experiences gravity, their mind will not know how to interact with it. You have an internal model of gravity and can therefore use it in your input-processing-output loop.

Another example: spiders use the laws of physics to offload a portion of their cognition into their web. They can identify the location and size of bugs caught in their webs just based on the vibrations transmitted through the fibers. The physical construction of the web communicates those mechanical vibrations in such a way that the spider need only feel them through its feet, and it can decide to pounce or hide, but the only signal it pays attention is vibrations. In the same way, NLCA must trust the rules of its environment in order to function. In practice, this means that you cannot take a version of NLCA built for email communications and then put it into a robotic chassis. That would be like taking the spider from its web and putting it on a keyboard. 

Some aspects of the environment tend to be persistent, like gravity, while other aspects are constantly changing, like the news or the weather. Persistent features of the environment are implicitly baked into NLCA via the data stored in the shared database. For example, every news article you read does not need to begin with “On Earth, there is gravity…” – we all assume that gravity exists. As with humans, NLCA only needs to be informed of exceptions and new facts. NLCA needs to store ephemeral information, like where you left your car keys!

### Shared Database

The database is the internal store for all contexts, corpuses, output, and dossiers. It should also be populated with encyclopedic knowledge, news, science, books, and literature, just like the library in the opening analogy.

![The shared database bridges the gap between inner and outer loops.](https://github.com/daveshap/NaturalLanguageCognitiveArchitecture/blob/main/images/10%20shared%20db.png?raw=true) *The shared database bridges the gap between inner and outer loops.*

The inner loop and outer loop never directly interact with each other. Instead, they both exchange information with the shared database. The inner loop generates dossiers, which contain thoughts, evaluations, inferences, hypotheses, and free associations. These dossiers can then be used by the outer loop to better hone interactions, track long term tasks, and provide useful insights.

Lastly, the QA (question answering) system can either be tightly integrated with the shared database as an extension of its capacities or it can be a third-party service that is used by the inner and outer loops. I am personally in favor of breaking the QA functionality off into its own service, which we will explore more in chapter 13 when we discuss microservices architectures. 

In most cases, we think of the mind as a blackbox. Our brains are very mysterious to us, even though we use them all day, every day. It is critical, therefore, to remember that the opposite is true for NLCA. NLCA is very aware of its own internal state and representations, while the real (or virtual) world is a mysterious entity that exists outside the walls of the enclosed library. The shared database combined with the QA system enables NLCA to have full access to its internal state and reasoning. Furthermore, it enables humans to peer into the mind of NLCA for the sake of research, accountability, and transparency.

### Summary

The outer loop is the behavioral loop of NLCA. It is responsible for handling incoming information from the outside world, compiling thoughts and decisions, and generating a response to the outside world. It is modeled on the conventional input-processing-output loop of robotics, but with a few changes. First, the “input” part of the robotics loop is replaced by the context of NLCA, which is a text document – like a letter. Letters contain some framing, such as an address and a greeting, plus a closing. This additional information gives the letter some metadata. NLCA data also requires metadata. Second, the “processing” section is replaced by the corpus of NLCA. The corpus is a compiled text document that contains memories, thoughts, morals, and plans. Once the corpus is compiled, it is used to generate the output. The output varies depending on the purpose of NLCA, but it can be in the form of chat, speech, robotic commands, video game character controls, emails, or anything else. The key thing here is that each step is a text document written in natural language.

The outer loop draws upon its connection with the shared database, which contains memories and knowledge. The inner loop also communicates with the shared database, but the inner and outer loops never communicate directly. Instead, the outer loop stores its memories in the shared database while the inner loop stores its thoughts in the shared database. Together, they produce thought, learning, and consideration. Both loops extract information from the shared database via a QA system, which will go over in greater detail several times throughout this book because QA is central to NLCA.

