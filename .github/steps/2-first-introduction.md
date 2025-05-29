## ステップ2: Copilotで作業をこなす

前のステップでは、GitHub Copilotがプロジェクトへのオンボーディングを手伝ってくれました。それだけでも大幅な時間節約になりますが、今度は実際に作業を進めましょう！

最近、生徒が同じアクティビティに2回登録してしまうというバグがあることがわかりました。これは許容できないので、修正しましょう！

残念ながら、この問題を解決するための情報はほとんど与えられていません。そこで、Copilotに問題箇所を見つけてもらい、潜在的な解決策を作成してもらいましょう。

しかし、その前に、Copilotについてもう少し学びましょう！ 🧑‍🚀

### Copilotはどのように機能しますか？

簡単に言えば、Copilotは非常に専門的な同僚のようなものだと考えることができます。彼らと効果的に作業するには、背景（コンテキスト）と明確な指示（プロンプト）を提供する必要があります。さらに、人によって得意なことは異なり、それは彼らのユニークな経験（モデル）によるものです。

- **コンテキストの提供方法:** コーディング環境では、Copilotは自動的に近くのコードや開いているタブを考慮します。チャットを使用している場合は、明示的にファイルを参照することもできます。

- **どのモデルを選ぶべきか:** この演習では、それほど重要ではありません。さまざまなモデルを試すのは楽しみの一つです！それはまた別のレッスンです！ 🤖

- **プロンプトの作成方法:** 明確かつ具体的に指示することで、Copilotは最善の仕事をしてくれます。ただし、従来のシステムとは異なり、フォローアップのプロンプトでいつでも指示を明確にすることができます。

> [!TIP]
> Copilotの知識と能力を補う方法は他にもいくつかあります。たとえば、[チャット参加者](https://docs.github.com/ja/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#chat-participants)、[チャット変数](https://docs.github.com/ja/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#chat-variables)、[スラッシュコマンド](https://docs.github.com/ja/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#slash-commands-1)、[MCPツール](https://code.visualstudio.com/docs/copilot/chat/mcp-servers)などです。

### :keyboard: アクティビティ: Copilotを使って登録バグを修正する :bug:

1. Copilotにバグの原因箇所を提案してもらいましょう。**Copilotチャット**パネルを**Askモード**で開き、以下のように質問します。

   > ![静的バッジ](https://img.shields.io/badge/-プロンプト-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > @workspace 学生がアクティビティに2回登録できてしまいます。
   > このバグはどこから来ている可能性がありますか？
   > ```

   <details>
   <summary>@workspaceとは何ですか？</summary>

   素晴らしい質問です！これは特殊な[チャット参加者](https://docs.github.com/ja/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#chat-participants)で、プロジェクトリポジトリを探索し、関連する追加のコンテキストを含めようとします。

   </details>

1. 問題が`src/app.py`ファイルと`signup_for_activity`メソッドにあることがわかったので、Copilotの推奨に従って（半手動で）修正しましょう。まずコメントを追加し、Copilotに修正を完了させます。

   1. VS Codeで、ファイルの**エクスプローラータブ**を選択してプロジェクトファイルを表示し、`src/app.py`ファイルを開きます。

   1. ファイルの下部近くまでスクロールし、`signup_for_activity`メソッドを見つけます。

   1. 生徒の追加を説明するコメント行を見つけます。この上の行が、登録チェックを行うのに論理的な場所と思われます。

   1. 以下のコメントを入力し、Enterキーを押して次の行に進みます。しばらくすると、Copilotからの提案とともに一時的なシャドウテキストが表示されます！素晴らしい！ :tada:

      ```python
      # 生徒が既に登録されていないか検証する
      ```

   1. `Tab`キーを押してCopilotの提案を受け入れ、シャドウテキストをコードに変換します。

      > **ヒント:** 他の提案を見たい場合は、`Tab`キーを押す代わりに、シャドウテキストの提案にカーソルを合わせるとツールバーが表示されます。矢印を使用して他の提案を選択するか、3つのドット`...`と`補完パネルを開く`オプションを選択して、専用パネルにすべての提案を表示します。

   <details>
   <summary>結果の例</summary><br/>

   Copilotは日々進化しており、常に同じ結果を生成するとは限りません。提案に満足できない場合は、この演習の作成中に生成した有効な提案結果の例を次に示します。これを使用して続行できます。

   ```python
   @app.post("/activities/{activity_name}/signup")
   def signup_for_activity(activity_name: str, email: str):
      """生徒をアクティビティに登録する"""
      # アクティビティが存在するか検証
      if activity_name not in activities:
         raise HTTPException(status_code=404, detail="アクティビティが見つかりません")

      # アクティビティを取得
      activity = activities[activity_name]

      # 生徒が既に登録されていないか検証
      if email in activity["participants"]:
        raise HTTPException(status_code=400, detail="生徒は既に登録されています")

      # 生徒を追加
      activity["participants"].append(email)
      return {"message": f"{email} を {activity_name} に登録しました"}
   ```

   </details>

### :keyboard: アクティビティ: Copilotにサンプルデータを生成させる 📋

新しいプロジェクト開発では、テスト用に現実的な見た目の偽データがあると便利なことがよくあります。Copilotはこのタスクに非常に優れているので、さらにいくつかサンプルアクティビティを追加し、**インラインチャット**を使用してCopilotと対話する別の方法を紹介しましょう。

**インラインチャット**と**Copilotチャット**パネルは非常によく似たツールですが、自動コンテキストが若干異なります。そのため、Copilotチャットはプロジェクトについて説明するのに適していますが、インラインチャットは特定の行や関数について質問するのにより自然に感じるかもしれません。

1. まだ開いていない場合は、`src/app.py`ファイルを開きます。

1. 上部（23行目あたり）で、サンプルの課外活動が設定されている`activities`変数を見つけます。

1. 関連する行のいずれかをクリックし、キーボードコマンド`Ctrl + I`（Windows）または`Cmd + I`（Mac）を使用してCopilotインラインチャットを表示します。

   > **ヒント:** Copilotインラインチャットを表示する別の方法は、選択した行のいずれかを`右クリック` -> `Copilot` -> `エディタインラインチャット`です。

1. 以下のプロンプトテキストを入力し、Enterキーを押すか、**送信してディスパッチ**ボタンを押します。

   > ![静的バッジ](https://img.shields.io/badge/-プロンプト-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > スポーツ関連のアクティビティを2つ、芸術関連の
   > アクティビティを2つ、知的なアクティビティを2つ追加してください。
   > ```

1. しばらくすると、Copilotは直接コードの変更を開始します。変更は、追加と削除を簡単に識別できるように、異なるスタイルで表示されます。少し時間を取って確認し、**承認**ボタンを押します。

   <details>
   <summary>結果の例</summary><br/>

   Copilotは日々進化しており、常に同じ結果を生成するとは限りません。提案に満足できない場合は、この演習の作成中に生成した結果の例を次に示します。困った場合は、これを使用して続行できます。

   ```python
   # インメモリ活動データベース
   activities = {
      "Chess Club": { # チェスクラブ
         "description": "戦略を学び、チェストーナメントで競う",
         "schedule": "金曜日、午後3時30分～午後5時",
         "max_participants": 12, # 最大参加者数
         "participants": ["michael@mergington.edu", "daniel@mergington.edu"]
      },
      "Programming Class": { # プログラミング教室
         "description": "プログラミングの基礎を学び、ソフトウェアプロジェクトを構築する",
         "schedule": "火曜日と木曜日、午後3時30分～午後4時30分",
         "max_participants": 20,
         "participants": ["emma@mergington.edu", "sophia@mergington.edu"]
      },
      "Gym Class": { # 体育の授業
         "description": "体育およびスポーツ活動",
         "schedule": "月曜日、水曜日、金曜日、午後2時～午後3時",
         "max_participants": 30,
         "participants": ["john@mergington.edu", "olivia@mergington.edu"]
      },
      "Basketball Team": { # バスケットボールチーム
         "description": "競技バスケットボールのトレーニングと試合",
         "schedule": "火曜日と木曜日、午後4時～午後6時",
         "max_participants": 15,
         "participants": []
      },
      "Swimming Club": { # 水泳クラブ
         "description": "水泳トレーニングとウォータースポーツ",
         "schedule": "月曜日と水曜日、午後3時30分～午後5時",
         "max_participants": 20,
         "participants": []
      },
      "Art Studio": { # アートスタジオ
         "description": "絵画やデッサンを通じて創造性を表現する",
         "schedule": "水曜日、午後3時30分～午後5時",
         "max_participants": 15,
         "participants": []
      },
      "Drama Club": { # 演劇部
         "description": "舞台芸術とパフォーマンストレーニング",
         "schedule": "火曜日、午後4時～午後6時",
         "max_participants": 25,
         "participants": []
      },
      "Debate Team": { # ディベートチーム
         "description": "パブリックスピーキングと議論のスキルを学ぶ",
         "schedule": "木曜日、午後3時30分～午後5時",
         "max_participants": 16,
         "participants": []
      },
      "Science Club": { # 科学クラブ
         "description": "実践的な実験と科学的探求",
         "schedule": "金曜日、午後3時30分～午後5時",
         "max_participants": 20,
         "participants": []
      }
   }
   ```

   </details>

### :keyboard: アクティビティ: Copilotを使って作業内容を記述する 💬

バグを修正し、サンプルアクティビティを拡張してくれてありがとう！今度は、Copilotの助けを借りて、作業内容をコミットしてGitHubにプッシュしましょう！

1. 左側のサイドバーで、`ソース管理`タブを選択します。

   > **ヒント:** ソース管理領域からファイルを開くと、単にファイルを開くのではなく、オリジナルとの差分が表示されます。

1. `app.py`ファイルを見つけ、`+`記号を押して変更をステージングエリアにまとめます。

   ![画像](https://github.com/user-attachments/assets/7d3daf4e-4125-4775-88a7-33251cd7293e)

1. ステージされた変更のリストの上にある**メッセージ**テキストボックスを見つけますが、今は**何も入力しないでください**。

   - 通常は、ここに変更の簡単な説明を書きますが、今はCopilotが手伝ってくれます！

1. **メッセージ**テキストボックスの右側にある**Copilotでコミットメッセージを生成**ボタン（キラキラアイコン）を見つけてクリックします。

1. **コミット**ボタンと**変更を同期**ボタンを押して、変更をGitHubにプッシュします。

1. Monaがあなたの作業を確認し、フィードバックを提供し、次のレッスンを共有するまでしばらく待ちます。

<details>
<summary>困っていますか？ 🤷</summary><br/>

フィードバックが得られない場合は、次の点を確認してください：

- `src/app.py`ファイルの変更をブランチ`accelerate-with-copilot`にプッシュしたことを確認してください。

</details>