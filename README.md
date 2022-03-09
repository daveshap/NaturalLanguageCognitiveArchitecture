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
