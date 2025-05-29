## ステップ4: プルリクエスト内でGitHub Copilotを使用する

おめでとうございます！この演習のコーディング（およびVS Codeでの作業）は完了です。今度は作業内容をマージする時間です。:tada: 最後に、プルリクエストを高速化できる2つのアクセス制限のあるCopilot機能について学びましょう！

#### Copilotプルリクエストの要約

通常、メモやコミットメッセージを確認し、それらをプルリクエストの説明用に要約します。これは、特にコミットメッセージに一貫性がなかったり、コードが十分に文書化されていなかったりする場合、時間がかかることがあります。幸いなことに、Copilotはプルリクエスト内のすべての変更を考慮し、重要なハイライトを（参照付きで！）提供できます。

> [!NOTE]  
> この機能は**GitHub Copilot Free**では利用できません。[[ドキュメント]](https://docs.github.com/ja/enterprise-cloud@latest/copilot/using-github-copilot/using-github-copilot-for-pull-requests/creating-a-pull-request-summary-with-github-copilot)

#### Copilotコードレビュー

作業に対するより多くの目は常に役立つので、通常のピアレビュープロセスを行う前に、Copilotに最初のパスを実行してもらいましょう。Copilotは簡単な調整で修正できる一般的な間違いを捉えるのに優れていますが、責任を持って使用することを忘れないでください。

> [!NOTE]  
> この機能は**GitHub Copilot Free**では利用できません。[[ドキュメント]](https://docs.github.com/ja/copilot/using-github-copilot/code-review/using-copilot-code-review)

### :keyboard: アクティビティ: CopilotでPRを要約・レビューする

**Copilotプルリクエストの要約**と**Copilotコードレビュー**はどちらもアクセスが制限されているため、このアクティビティはほとんど任意です。アクセス権をお持ちであれば、Monaが喜んで作業を確認します！そうでない場合は、任意のステップをスキップできます。

1. ウェブブラウザで別のタブを開き、演習リポジトリに移動します。

1. 新しいプルリクエストの作成を提案する**通知バナー**に気づくかもしれません。それをクリックするか、上部の**プルリクエスト**タブを使用して新しいプルリクエストを作成します。以下の詳細を使用してください：

   - **base:** `main`
   - **compare:** `accelerate-with-copilot`
   - **title:** `登録検証とアクティビティの追加`

1. (任意) **説明を追加**エリアで、必要に応じて編集モードに入り、**Copilotアクション**アイコンと**要約**アクションをクリックします。しばらくすると、Copilotが説明を追加します。:memo:

   <img alt="Copilot要約ボタン " width="300px" src="https://github.com/user-attachments/assets/3fc5fab4-db03-4ab8-8a16-cdd71ec2ded0">

1. (任意) 右側の情報パネルの上部にある**レビュー担当者**セクションを見つけ、**Copilotアイコン**の隣にある**リクエスト**ボタンをクリックします。Copilotがプルリクエストにレビューコメントを追加するまでしばらく待ちます！

   <img alt="Copilotレビューボタン" width="300px" src="https://github.com/user-attachments/assets/39b15002-a235-4c25-b09d-6a8097e27b62">

   > **ヒント:** Copilotにレビューがリクエストされたというログエントリに注目してください。

1. 下部にある**プルリクエストのマージ**ボタンを押します。素晴らしい！これで完了です！ :tada:

1. Monaがあなたの作業を確認し、フィードバックを提供し、このレッスンの最終レビューを投稿するまでしばらくお待ちください！