## Natural Language Processing (NLP)
Natural Language Processing, or NLP, is the ability for computers to understand the meaning of human language. 
![[Pasted image 20260213224223.png]]
*You can see how through NLP the computer is able to locate and classify named entities in the text into pre-defined categories such as the names of persons and locations.*

## Bag of words
Previously, the features for our machine learning problems have been numbers or categories. What do we do when our data is text? A simple option is to count the number of times important words appear in each piece of text. This technique is called bag of words.

Suppose we wanted to analyze the following two sentences: "U2 is a great band" and "Queen is a great band". We might end up with the word counts shown in the table.
![[Pasted image 20260213224351.png]]

## Bag of words: n-grams
Let's now consider the following sentence. When counting the individual words, "great" gets added to the list even though the sentiment towards the book is actually the opposite. 
This can be solved by counting sequences of words, a technique called n-grams. Here we are counting two-word sequences, allowing us to capture more information. ![[Pasted image 20260213224459.png]]

Bag of words is a useful technique that is commonly used in NLP. There are some limitations but for how simple it is, it yields some pretty impressive results.

## limitations
A limitation of bag of words is that word counts don't help us consider synonyms. For example, there are many words that all mean "blue", such as "sky-blue", "aqua" and "cerulean". Ideally, we would like to group these as a single feature.![[Pasted image 20260213224552.png]]

## Word embeddings - Incrustación de palabras
One solution to these problems is Word Embeddings. It is a special way of creating features that group together similar words. Word embeddings would create similar features for various shades of blue. Word embeddings have another interesting property: they are mathematical representations of words that obey intuitive rules. 

For example, in word embeddings, if we take the features for "King", subtract the features for "man", and add the features for "woman", we get a set of features that are very close to those of "queen".![[Pasted image 20260213224713.png]]


## Language translation
After mapping words or sentences to numbers, with the bag of words technique or using word embeddings, we can pass them to a neural network whose job it is to translate the input sentence to a different language. Here you can see the dutch sentence, "met of zonder jou", being translated to "with or without you".![[Pasted image 20260213224752.png]]

