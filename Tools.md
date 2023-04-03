## Langchain
複数のLLMモデルを結合することができるやつ
```
from langchain.llms import OpenAI
from langchain import PromptTemplate
from langchain import LLMChain
from langchain.chains import SimpleSequentialChain

explain_llm = OpenAI(model_name="gpt3.5-turbo")
summarize_llm = OpenAI(model_name="gpt3.5-turbo")

explain_template = """与えられた入力について詳細に説明してください。
入力: {input}
"""
summarize_template = """以下の入力について端的に要約してください。
入力: {input}
"""

explain_prompt_template = PromptTemplate(
    input_variables=["input"],
    template=explain_template,
)
summarize_prompt_template = PromptTemplate(
    input_variables=["input"],
    template=summarize_template,
)

explain_chain = LLMChain(llm=explain_llm, prompt=explain_prompt_template)
summarize_chain = LLMChain(llm=summarize_llm, prompt=summarize_prompt_template)

explain_summarize_chain = SimpleSequentialChain(
    chains=[explain_chain, summarize_chain],
    verbose=True
)

print(explain_summarize_chain.run("野球"))
```

Webページからのドキュメントの生成も可能(llama_index)
```
from llama_index.readers import BeautifulSoupWebReader
from llama_index import GPTSimpleVectorIndex

documents = BeautifulSoupWebReader().load_data(urls=["url"])
index = GPTSimpleVectorIndex(documents=documents)

```

## LlamaIndex
Llama Hubという中にいろいろなデータを操作するためのライブラリが存在(https://llamahub.ai/)
いろんなデータ形式に対応。それぞれのデータを読み込んで仕上げることも可能
[confluence](https://llamahub.ai/l/confluence)
[discord]
[file/pdf]
みたいなのを組み合わせて資料の作成も可能になる→copilotでも同様だが他の部分から取ってくる際にはllama indexがグルーになる。