# Short Question Answering


## Welcome

The service receives a pair of text files for the context and the question and uses them as input to the pre-trained model.

## What’s the point?

The service outputs a text string that is the answer to the question in the specified context.
Context is limited to 320 tokens, question is limited to 60 tokens.

## Model details:

The service receives a couple of textual sentences in English and uses it as input for the BERT Base neural model, trained to solve the question-answering task using a combination/fusion of several open-source question-answering datasets and outputs the answer for a given question in the specified context with high accuracy. The model runs on a P100 GPU. The input sequences are limited to 320 and 60 words for a context and the question respectively.

## How does it work?

The user must provide the following inputs in order to start the service and get a response:

Inputs:

 -   `endpoint`: sqa.naint.tech.
 -   `method`: qa.
 -   `input_path`: Path to '\*.txt' file containing JSON representation of input arguments 'context' and 'question', and their respective values.

Example of input file content:

```
{"context": "A function problem is a computational problem where a single output (of a total function) is expected for every input, but the output is more complex than that of a decision problem, that is, it isn't just yes or no. Notable examples include the traveling salesman problem and the integer factorization problem.", "question": "A function problem is an example of what?"}
```

You can call the service from SingularityNET CLI (`snet`).

Assuming that you have an open channel (`id: 0`) to this service:

```
$ snet client call 0 0.1 sqa.naint.tech qa_bert samples/sample.txt
Read call params from the file: samples/sample.txt

answer: "a computational problem"
```

## What to expect from this service?

Input data:

Context: `A function problem is a computational problem where a single output (of a total function) is expected for every input, but the output is more complex than that of a decision problem, that is, it isn't just yes or no. Notable examples include the traveling salesman problem and the integer factorization problem.`
Question: `A function problem is an example of what?`

Response:
`answer: "a computational problem"`
