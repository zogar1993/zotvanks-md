### Write clear and specific prompts
- Use delimiters (also prevents user injections)
- Ask structured output
- Check if conditions are satisfied
- Give successful examples before asking to perform
### Give Model time to think
- Give steps on what to do
- Tell to explicitly reason solutions itself before checking correction
### Iterative Process

## Issues
The model does not know the boundaries of its own knowledge, so it sometimes does "hallucinations", where it gives false but looking true information. To combat this you can ask to include quotes from the reference docs.

## Parts of the prompt

- user: The prompt itself.
- system: The specification that is set by default on the LLM, can be seen as an initial prompt set by the developer that aims to limit and direct the user usage.
- assistant: The response to the prompt. 

## Common usages
- Summarizing: Extracting relevant information out of text.
- Inferring: Checking if the opinion is favorable or not (Sentiment Analysis).
- Transforming: Translating language or format (english to french, json to html).
- Expanding: Provide answers to certain inputs (Replying to complaints, answer to a user who made a review thanking if the review was positive or suggesting specific actions in case it was negative). 