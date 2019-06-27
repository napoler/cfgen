# cfgen中文优化版本

Uses a combination of Markov chains and a context-free grammar to generate random sentences with features of both language models.

*Created by [William Gilpin](http://www.wgilpin.com/), 2014-2019*


## Requirements and Installation

**Automatic installation**

Download and extract the repository and then run

	$ python setup.py install

Often, the parser will fail to install. So instead run

	$ pip install git+git://github.com/emilmont/pyStatParser



**Manual installation**

Requirements

+ Python 2.7+ / Python 3.4+
+ Numpy
+ NLTK
+ [pyStatparser](https://github.com/emilmont/pyStatParser)

Optional installs (to use all tools)
+ language-check (for fixing some basic errors)
+ After The Deadline (for scoring)
+ Jupyter Notebook (for tutorial)

Manually install the code and basic dependencies by running these commands

	$ git clone https://github.com/williamgilpin/cfgen
    $ conda install nltk
    $ pip install git+git://github.com/emilmont/pyStatParser

For scoring grammar or automatically correcting the resulting sentences, install the Python package [language-check](https://pypi.python.org/pypi/language-check).

    $ pip install language-check

## Basic Usage

Point the tool to your corpus and set up the language model. Here we will use 2-grams of Mary Shelley's Frankenstein.

	my_model = GrammarModel('cfgen/full_books/frankenstein.txt', 2)  

Now generate an example sentence

	example_sentence = my_model.make_sentence()
    corrected_example_sentence = clean_output_text(example_sentence, use_language_tool=True)
    print(corrected_example_sentence)

A full workflow is given in the file **demos.ipynb**. 

<!-- I wrote about this project [on my blog.](https://gammacephei.wordpress.com/2014/08/17/algorithmic-trolling-of-social-networks/) -->

## Sample output

From a model trained on Mary Shelley's Frankenstein:

	these conversation possessed to his time
	those sense all fulfillment, me of affairs a soul been of I.
	The next kindness her black, light of it I wished as our perish certainty.
	horrible wretch that memory, their lake I to me, which the glad unhappiness 
	of the paroxysm of a several engagement of Clerval in her apartment and all 
	mainland, and on a progress, me surprised so divine me.


From a model trained on the Book of Revelations:

	Who said ever to no crown to was the listener and SECOND: 
	my man, and to the wheat,
	and had eat in this angel.

	Their pieces kill the sort the angel come up 
	to another translucent and weep any stone.
	Her timeless will measure them to the day, 
	hold created with earth noises and hurled every nation.

	There shown out upon the voice
	It be in seventh which is to trample, I.

	This tampering opened not for its time.

	The land to their moment Who threw their glory to cherish that art.

	The glory to the speaking, and at that white appearance, and say given 
	the thousand for the sake. And said show in myself. And it of no sweet victory 
	whose gateways enemies was loathe to the bowl
	and it for them and worked out as my hast to every vision.

	Their noise erase me.



<!-- ## TODO

+ Make the code automatically parse a subset of sentences in a corpus in order to generate a subsetted set of nonterminal grammar rules

+ Use Bayesian methods to randomly select among possible clause constructions based on previous clauses in the sentence, and use a Markov model to select words contextually based on higher level grammatical features of the sentence.

+ Punctuation is terrible right now because it has to be scraped off of hte corpus to prevent the tokenizer from choking.
 -->