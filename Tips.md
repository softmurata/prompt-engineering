## Prompt engineeringについてchatgptでやっているときに感じたこと
・何段階かに通じて自分の必要な情報に落とし込んでいく技術が大切
    ・箇条書きとrefinement
    ex) 箇条書きと情報抽出
    ```
    Please summarize and extract 5 points as bullet points format.
    ```
    ex) refinement
    ```
    Please refine the short 5 points as the bullet points format.
    ```
    ex) 抽出
    ```
    shortly, conceisely
    ```
・初期情報として入れる情報の質が高ければむやみやたらにたくさん入れる必要もなし。
    ・ユースケースの検討が非常に重要

・webchatgptというのを入れると最新のwebの情報をクロールしてきてそれをもとに色々と生成することが可能。
ある程度ドラフトが固まったら、web accessをoffにして仕上げにかかる。
