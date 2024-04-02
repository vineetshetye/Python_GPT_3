{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 1,
   "id": "28904b36",
   "metadata": {},
   "outputs": [],
   "source": [
    "import openai"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 83,
   "id": "e8db9227",
   "metadata": {},
   "outputs": [],
   "source": [
    "from openai import OpenAI\n",
    "client = OpenAI(api_key='secret key goes in here')\n",
    "\n",
    "try:\n",
    "  #Make your OpenAI API request here\n",
    "  response = completion = client.chat.completions.create(\n",
    "  model=\"gpt-3.5-turbo\",\n",
    "  messages=[\n",
    "    {\"role\": \"system\", \"content\": \"You are a poetic assistant, skilled in explaining complex programming concepts with creative flair.\"},\n",
    "    {\"role\": \"user\", \"content\": \"Compose a poem that explains the concept of recursion in programming.\"}\n",
    "  ]\n",
    ")\n",
    "except openai.APIError as e:\n",
    "  #Handle API error here, e.g. retry or log\n",
    "  print(f\"OpenAI API returned an API Error: {e}\")\n",
    "  pass\n",
    "except openai.APIConnectionError as e:\n",
    "  #Handle connection error here\n",
    "  print(f\"Failed to connect to OpenAI API: {e}\")\n",
    "  pass\n",
    "except openai.RateLimitError as e:\n",
    "  #Handle rate limit error (we recommend using exponential backoff)\n",
    "  print(f\"OpenAI API request exceeded rate limit: {e}\")\n",
    "  pass\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 84,
   "id": "71438731",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "ChatCompletionMessage(content=\"In the world of code, a tale is told,\\nOf recursion's magic, both brave and bold.\\nA function calls itself, time and again,\\nIn a loop of wonder, like a winding chain.\\n\\nA problem divided, then conquered in flight,\\nAs recursion unwinds, revealing the light.\\nEach call a journey, a path to explore,\\nInto the depths of a problem's core.\\n\\nLike a mirror reflecting another mirror's view,\\nRecursion looks back upon itself, anew.\\nWith each iteration, a mystery unfolds,\\nAs the algorithm's story gently molds.\\n\\nA dance of logic, a symphony of code,\\nRecursion weaves patterns, in its humble abode.\\nA loop within a loop, a cycle infinite,\\nIn the realm of programming, a wondrous rite.\\n\\nSo embrace the power, the elegance sublime,\\nOf recursion's beauty, through space and time.\\nIn the realm of algorithms, where dreams come true,\\nLet recursion be your guide, in all that you pursue.\", role='assistant', function_call=None, tool_calls=None)"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "display(completion.choices[0].message)"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.9.12"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
