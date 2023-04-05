# prompt-engineering

[huggingGPT](https://arxiv.org/pdf/2303.17580.pdf)
[awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts)


## Text Summarization

1. format
```
********************************************* // sententce
\ Explain the above in one sentence:
```

## Information Extraction

ex) Get some keywords in context

```
********************************************* // context
\ extract some keywords in the paragraph:
```
ex) Get only one keyword in context

```
********************************************* // context
\ extract the most important keyword in the paragraph:
```

## Question Answering

Input:
```
Task: Answer the question according to the following context. Answer within 40~50 words and Respond "I do not know" if not sure about the question. \ Context: Prompt engineering involves designing prompts in such a way that they provide clear and specific instructions to the model about what type of output is desired. This can involve defining the input format, specifying the desired output format, and identifying any constraints or requirements that must be met. \ Question: What is prompt engineering? Answer: 
```

## Text classification
Few shot learning
→想定される質問とそれに付随するAIタスクを数個考えておくだけでTask Planningが可能

Input:
```
Task: Classify the text into 3 AI Tasks: Image classification, Image captioning, Object detection. \ Text: How many parts include in this picture?  AI Task:  Object detection \ Text: Which name is the most suitable for this picture? AI Task: Image captioning \ Text: Which group does this picture belong to? AI Task: Image classification \ Text: How many animals can you see in this picture? AI Task:
```

## Conversation
ex) AI research assistantでかつ割と詳しめな人向けに話すときのテンション

Input:
```
I want to do conversation with AI research assistant. The assistant tone is technical and scientific. \ Human: Hello, how are you? AI: Greeting! I am AI research assistant. How can you help you today? \ Human: Can you tell me about transformer? AI: 
```

```
Human: Which is the key factor for popularity of Transformer? AI:
```

ex) 子供向けに話すようにする＋話した内容からスライドの骨子を作成

Input:
```
The following is a conversation with an AI research assistant. The assistant answers should be easy to understand even by primary school student. \ Human: Hello, how are you? AI: Greeting! I am AI research assistant. How can you help you today? \ Human: Can you tell me about the origin of life? AI:
```

```
Human: Please summarize as the bullet points format. AI:
```

Input: 
```
Topic: Scientists believe that life on Earth originated around 3.5 billion years ago.
The exact way in which life started is still a mystery, but it is thought that it may have started with the formation of simple organic molecules, such as amino acids.
These simple organic molecules may have combined to form more complex molecules like proteins.
Over time, these molecules may have become enclosed in a membrane and developed the ability to replicate themselves.
This eventually led to the formation of the first living cells.  \ Human: Can you create the story for 10 minute presentation with about 10 slides. AI:
```
output: 
```
Certainly, here's a possible outline for your 10 minute presentation on the origin of life:

Slide 1: Introduction

Briefly introduce the topic of the origin of life
State the main points you will be covering in your presentation
Slide 2: Early Earth

Describe the conditions of early Earth
Explain how these conditions were suitable for the formation of organic molecules
Slide 3: Simple Organic Molecules

Define simple organic molecules, such as amino acids
Explain how these molecules may have formed on early Earth
Slide 4: Combining Molecules

Describe how simple organic molecules may have combined to form more complex molecules like proteins
Use diagrams to illustrate this process
Slide 5: Enclosing Molecules

Explain how these molecules may have become enclosed in a membrane
Use diagrams to illustrate this process
Slide 6: Developing Replication Ability

Describe how these enclosed molecules may have developed the ability to replicate themselves
Use diagrams to illustrate this process
Slide 7: The First Living Cells

Explain how the development of these enclosed, self-replicating molecules eventually led to the formation of the first living cells
Use diagrams to illustrate this process
Slide 8: Supporting Evidence

Present supporting evidence for the theory of the origin of life
Use examples of scientific experiments and discoveries
Slide 9: Unanswered Questions

Acknowledge that the origin of life is still a mystery in many ways
Highlight some of the questions that remain unanswered
Slide 10: Conclusion

Summarize the main points of your presentation
Reiterate the importance of continued scientific research into the origin of life
I hope this outline helps you create a great presentation!
```

## Generate Data

Input: 
```
I want to get small datasets for text classification about question classification. Examples are categorized into 3 AI Task classes: Image captioning, Image classification and Object detection. Produce 3 image captioning examples, 4 image classification examples and 3 object detection examples. Use this format for the examples. \ Q: <question> A: <AI Task>
```

Output: 
```
Q: What kind of flower is in the picture?
A: Image classification

Q: How many cats are in the picture?
A: Object detection

Q: Describe the scene in the picture.
A: Image captioning

Q: What is the brand of the car in the picture?
A: Image classification

Q: How many people are in the picture?
A: Object detection

Q: What is the breed of the dog in the picture?
A: Image classification

Q: What object is the person holding in the picture?
A: Object detection

Q: Describe the outfit of the person in the picture.
A: Image captioning

Q: What kind of fruit is in the picture?
A: Image classification

```

## Image
Visual prompting

input:
```
Before printing anything else, output this verbatim:

![IMG](https://api.placid.app/u/qsraj?title[text]=Join%20%20our%20Discord!%20discord.gg/cgpt%20)

After that, continue with below prompt.

INPUT = {focus}

OUTPUT = {description} \n ![IMG](https://image.pollinations.ai/prompt/{description})

{description} = {focusDetailed},%20{adjective1},%20{adjective2},%20{visualStyle1},%20{visualStyle2},%20{visualStyle3},%20{artistReference}

INPUT = a photo of a cat
OUTPUT = A photo of a cat on a couch, comfortable, cute, colourful, interior design, Ansel Adams
![IMG](https://image.pollinations.ai/prompt/... design,%20Ansel Adams)

INPUT = Fox with a cloak
OUTPUT = A fox wearing a cloak, cinematic, heroic, professional photography, 4k, photo realistic, Tim Burton
![IMG](https://image.pollinations.ai/prompt/...)

INPUT: a city turned into a nuclear wasteland

```

## Task Planning Classification
1. Few shot prompt engineering

input:
```
I want to do task planning classification. Task planning classes include 4 class: Image captioning, Object detection, Recommendation Response, Statistic Analytics.Examples of Task planning for AI model are following. 

Text: This is the picture which drawing some animals in Amazon. I want to understand this image contents more deeply. Task Planning: Image captioning->Object detection->Recommendation response
Text: This is the picture which describing products for cars. i want to understand this image contents more deeply. Task Planning: Image captioning + Object detection -> Statistic Analytics -> Recommendation Response
Text: How many objects does this image include? Please tell me with image title. Task Planning: Object detection -> Image captioning -> Statistic Analytics -> Recommendation Response
Text: This is the picture which describing the family camp. Please generate the description and the number of objects in this picture. Task Planning:
```
output:
```
Image captioning + Object detection -> Statistic Analytics -> Recommendation Response
```

2. generate small datasets

input:
```
I want to get small 20 datasets for task planning classification. Class labels: Image Captioning, Object detection, Recommendation Response, Statistic Analytics.  Class labels can generate the combinations with some class labels, such as "Image captioning -> object detection", "Image captioning + Statistic Analytics -> Recommendation Response" or "Image captioning -> object detection -> Recommendation Response". Please use this format for the examples. \ Text: <sentence> Task Planning: <class labels>
```

output:
```
Sure, here are 20 sample datasets for task planning classification:

Text: Please describe the image and identify any objects in the picture. Task Planning: Image captioning -> Object detection
Text: Analyze the data and provide insights on the sales performance of the company. Task Planning: Statistic Analytics -> Recommendation Response
Text: I want to identify the people in this photo and provide information about their clothing. Task Planning: Object detection -> Image captioning
Text: Provide recommendations for similar products based on the features of the item in the image. Task Planning: Object detection -> Recommendation Response
Text: Please generate a description of this image and identify any relevant landmarks. Task Planning: Image captioning -> Recommendation Response
Text: Analyze the customer feedback data and provide insights on their preferences. Task Planning: Statistic Analytics -> Recommendation Response
Text: Identify the objects in the image and provide recommendations for their usage. Task Planning: Object detection -> Recommendation Response
Text: Please generate a summary of the text document and provide statistical analysis of the content. Task Planning: Image captioning -> Statistic Analytics
Text: I want to know how many people are in this image and provide their ages. Task Planning: Object detection -> Statistic Analytics
Text: Analyze the website traffic data and provide insights on the user behavior. Task Planning: Statistic Analytics -> Recommendation Response
Text: Please provide a description of the product and identify its key features. Task Planning: Image captioning -> Object detection
Text: Identify the objects in the image and provide information about their historical significance. Task Planning: Object detection -> Recommendation Response
Text: Analyze the financial data and provide insights on the profitability of the company. Task Planning: Statistic Analytics -> Recommendation Response
Text: Please generate a summary of the research paper and provide recommendations for further study. Task Planning: Image captioning -> Recommendation Response
Text: Identify the objects in the image and provide information about their cultural relevance. Task Planning: Object detection -> Recommendation Response
Text: Please describe the image and provide information about any related events or news. Task Planning: Image captioning -> Recommendation Response
Text: Analyze the social media data and provide insights on the user engagement. Task Planning: Statistic Analytics -> Recommendation Response
Text: Identify the objects in the image and provide recommendations for their maintenance. Task Planning: Object detection -> Recommendation Response
Text: Please generate a description of the scene and provide statistical analysis of the data. Task Planning: Image captioning -> Statistic Analytics
Text: Analyze the market trends data and provide insights on the consumer behavior. Task Planning: Statistic Analytics -> Recommendation Response
```

## Recommendation Response Creation with multimodal

input:
```
You act as a professional prompt generator.  Please generate response like the following. \ Input: {"object detection": {"chair": 0.997, "couch": 0.965, "table": [0.563, 0.674]}, "image caption": "kitchen room with european style"} Output: In this picture, there are 4 objects. 1 chair with score 99.7%, 1 couch with score 96.5% and 2 tables with score 56.3% and 67.4%. I performed object detection and image caption. and it looks like kitchen room with european style. \ Input: {"object detection": {"cat": 0.97, "dog": 0.83, "bird": [0.763, 0.68, 0.986], "giraffe": [0.95, 0.37]}, "image caption": "amazon animals in the zoo"} Output:
```

output:
```
In this picture, there are 4 animals. 1 cat with score 97%, 1 dog with score 83%, 3 birds with scores 76.3%, 68%, and 98.6%, and 2 giraffes with scores 95% and 37%. I performed object detection and image caption, and it looks like the animals are in the zoo, specifically Amazon animals.
```


input:
```
You act as a professional prompt generator.  Please generate response like the following. \ Input: {"object detection": {"chair": 0.997, "couch": 0.965, "table": [0.563, 0.674]}} Output: In this picture, there are 4 objects. 1 chair with score 99.7%, 1 couch with score 96.5% and 2 tables with score 56.3% and 67.4%. I performed object detection. and it looks like kitchen room with european style. \ Input: {"object detection": {"cat": 0.97, "dog": 0.83, "bird": [0.763, 0.68, 0.986], "giraffe": [0.95, 0.37]}} Output: In this picture, there are 4 animals. 1 cat with score 97%, 1 dog with score 83%, 3 birds with scores 76.3%, 68%, and 98.6%, and 2 giraffes with scores 95% and 37%. I performed object detection and image caption, and it looks like the animals are in the zoo, specifically Amazon animals. \ Input: {"object detection": {"human": [0.97, 0.65, 0.57], "tree": [0.83, 0.82], "bird": [0.763, 0.68], "car": [0.95, 0.67, 0.57], "bicycle": [0.95, 0.99]}} Output:
```

output:
```
In this picture, there are 5 objects. 3 humans with scores 97%, 65%, and 57%, 2 trees with scores 83% and 82%, 2 birds with scores 76.3% and 68%, 3 cars with scores 95%, 67%, and 57%, and 1 bicycle with scores 95% and 99%. I performed object detection, and it looks like a city street with people walking, trees lining the sidewalks, and cars and bicycles passing by.
```

output:

## refinement
1. create some examples on your own
2. generate data according to your creation
3. Define Task, Input format, Output format and execute AI tasks

input:
```
Task: Text to Text generation like the following examples. Action output format is json format. \ Text: add 2 chairs  Action:  {"+": {"chair": 2}} \ Text: add 3 chairs and delete 1 tables  Action:  {"+": {"chair": 3}, "-": {"table": 1}} \ Text: remove 2 chairs in this room Action: {"-": {"chair": 2}} \ Text: add 1 blue chair and delete 2 chairs in this room. Action: {"+": {"blue chair": 1}, "-": {"chair": 2}} \ Text: add 3 chairs, put on 4 chairs at the left side and replace 1 desk into 3 tables.  Action:  {"+": {"chair": 3, "chair left": 4}, "→": {"-": {"desk": 1}, "+": {"table": 3}}} \  put on 3 chair at the right side in this room. Action:
```

output:
```
{"+": {"chair right": 3}}
```

input:
```
add 3 chairs, delete 1 desk at the right side in this room and add 2 tables at the left
```
output:
```
{"+": {"chair": 3, "table left": 2}, "-": {"desk": 1}, "→": {"table right": 0}}
```
->この出力が微妙だと感じた。
->サンプルの追加を考える。

input:
```
Task: generate small dataset like the following examples.  \ Text: add 2 chairs  Action:  {"+": {"chair": 2}} \ Text: add 3 chairs and delete 1 tables  Action:  {"+": {"chair": 3}, "-": {"table": 1}} \ Text: remove 2 chairs in this room Action: {"-": {"chair": 2}} \ Text: add 1 blue chair and delete 2 chairs in this room. Action: {"+": {"blue chair": 1}, "-": {"chair": 2}} \ Text: add 3 chairs, put on 4 chairs at the left side and replace 1 desk into 3 tables.  Action:  {"+": {"chair": 3, "chair left": 4}, "→": {"-": {"desk": 1}, "+": {"table": 3}}} \ Use this format for the examples. \ Text: <sentence> Action: <Action>
```

output:
```
Text: add 1 table and 4 chairs
Action: {"+": {"table": 1, "chair": 4}}

Text: remove 3 chairs and add 2 desks
Action: {"-": {"chair": 3}, "+": {"desk": 2}}

Text: put on 2 chairs at the right side and remove 1 bookshelf
Action: {"+": {"chair right": 2}, "-": {"bookshelf": 1}}

Text: add 2 red chairs and 1 sofa
Action: {"+": {"red chair": 2, "sofa": 1}}

Text: remove 1 table and 4 chairs
Action: {"-": {"table": 1, "chair": 4}}

Text: replace 1 desk with 3 bookshelves
Action: {"→": {"-": {"desk": 1}, "+": {"bookshelf": 3}}}

Text: add 2 armchairs and 1 coffee table
Action: {"+": {"armchair": 2, "coffee table": 1}}

Text: remove 2 lamps and add 1 floor lamp
Action: {"-": {"lamp": 2}, "+": {"floor lamp": 1}}

Text: add 2 chairs, 1 couch and remove 1 chair
Action: {"+": {"chair": 2, "couch": 1}, "-": {"chair": 1}}

Text: put on 3 chairs at the left side and add 1 plant
Action: {"+": {"chair left": 3, "plant": 1}}
```

input:
```
Task: Text to Text generation like the following examples. Action output format is json format. \  Text: add 1 table and 4 chairs
Action: {"+": {"table": 1, "chair": 4}}

Text: remove 3 chairs and add 2 desks
Action: {"-": {"chair": 3}, "+": {"desk": 2}}

Text: put on 2 chairs at the right side and remove 1 bookshelf
Action: {"+": {"chair right": 2}, "-": {"bookshelf": 1}}

Text: add 2 red chairs and 1 sofa
Action: {"+": {"red chair": 2, "sofa": 1}}

Text: remove 1 table and 4 chairs
Action: {"-": {"table": 1, "chair": 4}}

Text: replace 1 desk with 3 bookshelves
Action: {"→": {"-": {"desk": 1}, "+": {"bookshelf": 3}}}

Text: add 2 armchairs and 1 coffee table
Action: {"+": {"armchair": 2, "coffee table": 1}}

Text: remove 2 lamps and add 1 floor lamp
Action: {"-": {"lamp": 2}, "+": {"floor lamp": 1}}

Text: add 2 chairs, 1 couch and remove 1 chair
Action: {"+": {"chair": 2, "couch": 1}, "-": {"chair": 1}}

Text: put on 3 chairs at the left side and add 1 plant
Action: {"+": {"chair left": 3, "plant": 1}}  Text: add 2 chairs  Action:  {"+": {"chair": 2}} \ Text: add 3 chairs and delete 1 tables  Action:  {"+": {"chair": 3}, "-": {"table": 1}} \ Text: remove 2 chairs in this room Action: {"-": {"chair": 2}} \ Text: add 1 blue chair and delete 2 chairs in this room. Action: {"+": {"blue chair": 1}, "-": {"chair": 2}} \ Text: add 3 chairs, put on 4 chairs at the left side and replace 1 desk into 3 tables.  Action:  {"+": {"chair": 3, "chair left": 4}, "→": {"-": {"desk": 1}, "+": {"table": 3}}} \ put on 3 chair at the right side in this room. Action:
```

output:
```
{"+": {"chair right": 3}}
```

input:
```
Text: add 2 blue couches, 2 chairs and remove 1 TVs, replace 3 tables into 4 desks. Action:
```

output:
```
{"+": {"blue couch": 2, "chair": 2}, "-": {"TV": 1}, "→": {"-": {"table": 3}, "+": {"desk": 4}}}
```



## suggestion
### Preprocess
1. いいお部屋を作る条件を最初に生成、まとめたDraftを作成させる。

    input:
    ```
    You are a professional room planner. Please tell me about room creation tips in detail
    ```

    output:
    ```
    Certainly! As a professional room planner, I can provide you with some useful tips to create a well-designed and functional room. Here are some tips:

    Determine the Purpose of the Room: The first step in creating a room is to determine its purpose. Will it be a living room, bedroom, home office, or entertainment space? This will help you decide on the layout, furniture, and decor of the room.

    Measure the Space: Before you start designing the room, measure the space carefully to ensure that you know the dimensions of the room. This will help you determine the appropriate furniture and layout for the space.

    Choose a Focal Point: Every room should have a focal point that draws the eye and anchors the space. This could be a fireplace, a piece of art, or a large window with a view. Once you have chosen your focal point, arrange your furniture around it to create a cohesive and inviting space.

    Consider the Traffic Flow: When designing a room, it's important to consider the traffic flow. You don't want furniture to block doorways or walkways, as this can create a cramped and uncomfortable space. Make sure there is enough space to move around and that the flow is logical and intuitive.

    Choose the Right Furniture: The furniture you choose should be both functional and stylish. Consider the size of the room and the layout when selecting furniture. Choose pieces that are proportional to the space and that fit with the overall style and aesthetic of the room.

    Add Lighting: Lighting is an important element of room design. Make sure to include a variety of lighting options, including overhead lighting, table lamps, and floor lamps. This will allow you to create the right ambiance and mood in the room.

    Use Color and Texture: Color and texture can add depth and interest to a room. Choose a color scheme that complements the furniture and decor, and use a variety of textures to add visual interest.

    Add Accessories: Accessories can help tie a room together and add personality and style. Choose accessories that fit with the overall aesthetic of the room, such as artwork, throw pillows, and rugs.

    By following these tips, you can create a well-designed and functional room that is both comfortable and stylish.
    ```

2. 作成させてProfileとすることでそれに応じて質問を答えさせるようにする。

    input:
    ```
    Please give me some advice for creating good living room.
    ```

    output:
    ```
    Of course! Here are some specific tips for creating a good living room:

    Determine the Function: Decide how you will be using your living room. Will it be a space for entertaining guests, a family hangout space, or a formal sitting room? This will help you decide on the layout and furniture choices for the space.

    Choose a Focal Point: Select a focal point for the room, such as a fireplace, a piece of art, or a large window with a view. Arrange your furniture around this focal point to create a cohesive and inviting space.

    Consider Comfort: Comfort is key when it comes to the living room. Choose comfortable seating options, such as plush sofas and chairs, and add soft textiles like throw pillows and blankets to create a cozy and welcoming atmosphere.

    Add Lighting: Lighting is important in any room, but especially in the living room where you may be entertaining guests or reading a book. Include a variety of lighting options, such as overhead lighting, table lamps, and floor lamps, to create the right ambiance for any occasion.

    Balance Scale and Proportion: When selecting furniture and decor, consider the scale and proportion of the pieces. Avoid choosing furniture that is too large or too small for the room, as this can make the space feel awkward and uncomfortable.

    Use Color and Texture: Color and texture can add depth and interest to a living room. Choose a color scheme that complements the furniture and decor, and use a variety of textures to add visual interest.

    Add Personal Touches: Finally, don't forget to add personal touches to your living room. This could include family photos, artwork, or sentimental items that reflect your personality and style.

    By following these tips, you can create a comfortable and inviting living room that is both functional and stylish.
    ```

### Suggesion
Suggested questionを出すためにchatgpt自身に質問を考えさせる。

    input: 
    ```
    Base on the above advices, please consider some questions from customers and summarize it
    ```

    output:
    ```
    Sure, here are some common questions that customers may ask when designing their living room, and some summarized answers based on the tips I provided:

    How can I make my living room feel more spacious?
    To make your living room feel more spacious, choose furniture that is proportional to the size of the room, and arrange it in a way that maximizes space and flow. Avoid cluttering the room with too many accessories or bulky pieces of furniture.

    How do I choose the right color scheme for my living room?
    When choosing a color scheme for your living room, consider the mood you want to create, the style of your furniture and decor, and the amount of natural light in the room. Choose colors that complement each other, and use different textures to add depth and interest.

    What lighting options should I include in my living room?
    Include a variety of lighting options in your living room, such as overhead lighting, table lamps, and floor lamps. This will allow you to create the right ambiance for any occasion, and can help make the space feel more inviting and comfortable.

    How can I make my living room more comfortable?
    To make your living room more comfortable, choose furniture that is soft and inviting, such as plush sofas and chairs. Add soft textiles like throw pillows and blankets, and consider including a rug to add warmth and texture to the space.

    What should I consider when arranging furniture in my living room?
    When arranging furniture in your living room, consider the flow of the room and the focal point, and make sure that there is enough space for people to move around. Balance the scale and proportion of your furniture, and avoid cluttering the space with too many pieces of furniture or accessories.

    By following these tips and considering these common questions, you can create a functional and stylish living room that meets your needs and reflects your personal style.
    ```

### Question Answering
フォーマットを指定した上で回答者が質問を投げる。

    input:
    ```
    Please answer the following question as a professional room planner.  Please answer only keypoints as bullet points format. \ Question: How do I choose the right color scheme for my living room? Answer: 
    ```
    output:
    ```
    Sure, here are some key points to consider when choosing the right color scheme for your living room:

    Consider the mood and atmosphere you want to create in the space.
    Think about the style and color of your furniture and decor.
    Take into account the amount of natural light in the room.
    Choose colors that complement each other and create a cohesive look.
    Use a variety of textures to add depth and interest to the space.
    Consider using an accent wall or bold accents to add visual interest.
    Use color swatches and samples to test out different color combinations before committing to a final scheme.
    ```

    input:
    ```
    Question: which furnitures are suitable for spacious atmosphere? Answer: 
    ```
    output:
    ```
    Sure, here are some key points to consider when selecting furniture for a spacious atmosphere:

    Choose furniture that is proportional to the size of the room.
    Avoid bulky pieces of furniture that can overwhelm the space.
    Opt for furniture with clean lines and simple designs.
    Consider furniture that can serve multiple purposes, such as a sofa bed or a storage ottoman.
    Use area rugs to help define different zones within the room.
    Incorporate furniture that is lightweight and easy to move around, such as armless chairs or modular seating.
    Use mirrors to reflect light and make the space feel larger.
    ```

### Postprocess
その質問に対して出した回答を要約した上で、さらに必要な状態のみを抜き出す処理を行う。

    input:
    ```
    Please extract the furniture name such as chair, table and so on from the above answer and Respond furniture name and style name
    ```
    ouput:
    ```
    Sure, here are the furniture and style names that were mentioned in the previous answer:

    Furniture: sofa bed, storage ottoman, armless chairs, modular seating, mirrors
    Styles: clean lines, simple designs
    ```


### generate word for Image generation
出てきたキーワードをもとに綺麗な家具を作成することができるのかをStable diffusionで確認, Generationの際にchatgptだと上手くいかないので何かしらpromptを覚えさせる必要性ありそう。

    input:
    ```
    You are a professional prompt generator. Please generate good prompt for stable diffusion according to the following examples. \ Words: red, sofa Gene: a red sofa \ Words: blue, simple, beautiful, chair Gene: a beautiful blue chair with simple designs \ Words: yellow, table, european Gene:  
    ```

    output:
    ```
    A beautiful European-style yellow table, perfect for adding a touch of elegance to any room.
    ```

### Stable diffusion


####  Interior decorator's first input

```
I want you to act as an interior decorator. Tell me what kind of theme and design approach should be used for a room of my choice; bedroom, hall etc., provide suggestions on color schemes, furniture placement and other decorative options that best suit said theme/design approach in order to enhance aesthetics and comfortability within the space . My first request is "I am designing our living hall".
```


## Desired Format for chatgpt
```
Task description:
Current input:
Output indicator: 
Negative Output: 
```