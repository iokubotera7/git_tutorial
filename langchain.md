## Callbacks
Callbacksモジュールは、特定のイベントや条件が満たされた際に実行される関数やアクションを定義するための機能。  
### コールバックハンドラ
LangChainのCallbacksを活用するために重要なものとして、コールバックハンドラがある。  
コールバックハンドラは、アプリケーションの特定のイベントに対して、自分で定義した処理を実行できるようにするオブジェクト。  

## Memory
Langchainでメモリを追加する方法は以下の通り。  
1. プロンプトテンプレートで会話履歴を追加
  ```
from langchain_core.prompts import ChatPromptTemplate, MessagePlaceholder

#プロンプトテンプレートで会話履歴を追加
prompt_template = ChatPromptTemplate.from_messages(
  [
    MessagePlaceholder(variable_naem="history"), # 会話履歴を追加
    ("human", "{input}"),
  ]
)

# Runnableの準備
runnable = prompt_template | chat_model
```
2. RunnableWithMessageHistoryでRunnableをラップ。
   RunnableWithMessageHistoryはRunnableに会話履歴を追加することができるコンポーネント
   ```
   from langchain_community.chat_message_histories import ChatMemoryHistory
   from langchain_core.chat_history import BaseChatMessageHistory
   from langchain_core.runnables.history import RunnableWithMessageHistory

   store = {}

   # セッションIDごとの会話履歴を取得
   def get_session_history(session_id: str) -> BaseChatMessageHistory:
     if session_id not in store:
       store[session_id] = ChatMessageHistory()
     return store[session_id]

   # RunnableWithMessageHistoryの準備
   runnable_with_history = RunnableWithMessageHistory(
     runnable,
     get_session_history,
     input_messages_key="input", # 辞書型で入力する場合の入力キー
     history_messages_key="history" # 辞書型で入力する場合の会話履歴のキー
   )
   ```
4. 
