## Demo Overview

In this demo I quickly implement a python module, []codeinterpreter-api](https://github.com/shroominic/codeinterpreter-api), built as an open source functionality akin to the OpenAI's Code Interpreter. The module queries various Large Language Model (LLM) API through LangChain, a framework for communicating with LLMs that includes contains useful absractions for tasks like code understanding, question-answering, and summarization. In this case, I use it to query the ChatGPT API and the model chat-gpt3.5-turbo to produce code based on a written prompt. The module then tests and ioterates on the code produced by ChatGPT using CodeBox, a simple cloud infrastructure built to allow you to run python code in a isolated environment. The code is returned to the LLM with any errors until it produces bug-free, runnable code, which is run and returned to the user as a response.

## The Data

This project uses data I collected on all the food I ate and their nutrition label contents for roughly 4.5 days.

<img src="media/first5rows.jpg">

Looking at the first five rows, we can see that the data contains labeled columns with the consumption date and time, plus columns with nutrient labels. 

<img src="media/inforeport.jpg">

We can see that the data is organised but has many missing values across all columns.

## Objective

I want to look at the recorded data to see how my daily intake of each primary nutrient compares with the recommendation for the average adult male.

## Results

Based on the following prompt:

```python
user_request = "Compare daily intake of the macronutrients recorded in this dataset with the \
            average recommendations for a 30 year old male. Plot the summed daily intake per macronutrient \
            for every day as a time series and include a reference for the recommended daily macronutrient value on the \
            plot. Any information you require that you cannot determine from the data, look up on the internet. \
            The columns have headers that describe the column contents. Each row, in the first two columns, has a date \
            and a time of consumption. Please use contrasting colors for the different nutrient types and make their reference lines different shades. \
            If any row does not have total fat, try summing the saturated and unsaturated fat for that row. For any element with no value, replace the \
            unknown with zero. Label all plotted lines and references in a legend."
```

I was able to produce this chart.

<img src="media/CodeInterpreterAPI_Final.jpg">

The response also included text-based insight along with the plot response for context. It says

> Here is the plot showing the daily intake of macronutrients compared to the recommended daily 
> intake for a 30-year-old male. The solid lines represent the actual daily intake, while the dashed 
> lines represent the recommended intake. As you can see, the intake of proteins, carbohydrates, and 
> fats varies from day to day, and it often exceeds the recommended values.

## Continued progress

By slight refinement of language or trying prompts with a more organised structure, I could designate specific colors or further specify plot elements. I could also ask questions to continue investigation, such as producing similar charts for the available micronutrients in the dataset.

## Conclusions

This exciting demo highlights the possibility of surging LLM based code interpreters being deployed at a scalable level. We could imagine deploying an application where people can regularly record the foods they eat, nutrition facts are queried and stored, and users can query a chatbot with custom questions that the chatbot can produce visualisations and insight on, on demand. 