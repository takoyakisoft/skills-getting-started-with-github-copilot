## ステップ1: Copilot こんにちは

「GitHub Copilotをはじめよう」演習へようこそ！ :robot:

この演習では、さまざまなGitHub Copilotの機能を使って、Mergington高校の生徒が課外活動に登録できるウェブサイトを作成します。 🎻 ⚽️ ♟️

<img width="600" alt="Mergington高校ウェブアプリのスクリーンショット" src="https://github.com/user-attachments/assets/472398fd-1aa1-4084-b443-4e242deb30d9" />

### GitHub Copilotとは？

<img width="150" align="right" alt="Copilot ロゴ" src="https://github.com/user-attachments/assets/4d22496d-850b-4785-aafe-11cba03cd5f2" />

GitHub CopilotはAIコーディングアシスタントで、より速く、より少ない労力でコードを書く手助けをし、問題解決とコラボレーションにより多くのエネルギーを集中できるようにします。

GitHub Copilotは、開発者の生産性を向上させ、ソフトウェア開発のペースを加速させることが証明されています。詳細については、[GitHubブログの「調査：GitHub Copilotが開発者の生産性と幸福度に与える影響の定量化」](https://github.blog/news-insights/research/research-quantifying-github-copilots-impact-on-developer-productivity-and-happiness/)をご覧ください。

最も一般的なインタラクションは次のとおりです。

- **インライン提案**: 入力中に、Copilotは近くのコンテキストを使用してエディタに直接コードを提案します。これは、[Intellisense](https://code.visualstudio.com/docs/editor/intellisense)のようなコード補完ツールを使用したことがある場合は馴染みのあるインタラクションですが、補完が関数全体になる場合がある点が異なります。
- **Copilot - Askモード**: コーディング関連の質問をすることができる専用のチャットパネルです。オンラインのAIアシスタントチャットを使用したことがある場合は馴染みやすいでしょう。ただし、大きな違いは、プロジェクトファイルが自動的にコンテキストを提供し、カスタマイズされた応答を提供することです。
- **Copilot - Editモード**: Askモードに似ていますが、会話的ではありません。Copilotは、リクエストを実装するために選択したファイルに変更を加えます。
- **Copilot - Agentモード**: Copilotは、リクエストが達成されるまで反復的に実行されます。コンテキストを選択し、コード変更を行い、ターミナルコマンドを実行し、ツールを実行し、そして最も重要なこととして、調整を行うために自身の作業をレビューします。

> [!TIP]
> 現在および今後の機能については、[GitHub Copilotの機能](https://docs.github.com/ja/copilot/about-github-copilot/github-copilot-features)ドキュメントで詳しく知ることができます。さまざまな[モデル](https://docs.github.com/ja/github-models)を選択したり、独自の[拡張機能](https://github.com/features/copilot/extensions)を作成したりすることもできますが、それは別のレッスンです！

### GitHub Copilotはどのように使えますか？

作業を進める中で、GitHub Copilotがウェブサイト全体や、VS Code、JetBrains、Xcodeなどのお気に入りのコーディング環境のさまざまな場所で役立つことがわかるでしょう！ただし、今日のコーディングでは、[Codespace](https://github.com/features/codespaces)として知られる事前設定済みの開発環境でVS Codeを使って練習します。

### :keyboard: アクティビティ: Copilot Chatからプロジェクトの概要を取得する

開発環境を起動し、Copilotを使ってプロジェクトについて少し学び、その後テスト実行してみましょう。

1. 下のボタンを左クリックして、新しいタブで**Codespaceの作成**ページを開きます。デフォルト設定を使用してください。

   [![GitHub Codespacesで開く](https://github.com/codespaces/badge.svg)](https://codespaces.new/{{full_repo_name}}?quickstart=1)

1. **リポジトリ**フィールドが演習のあなたのコピーであり、オリジナルではないことを確認してから、緑色の**Codespaceの作成**ボタンをクリックします。

   - ✅ あなたのコピー: `/{{{full_repo_name}}}`
   - ❌ オリジナル: `/skills/getting-started-with-github-copilot`

1. Visual Studio Codeがブラウザに読み込まれるまでしばらく待ちます。

1. 左側のサイドバーで、拡張機能タブをクリックし、`GitHub Copilot`と`Python`拡張機能がインストールされ、有効になっていることを確認します。

   <img width="350" alt="VS Code用Copilot拡張機能" src="https://github.com/user-attachments/assets/ef1ef984-17fc-4b20-a9a6-65a866def468" />

   <img width="350" alt="VS Code用Python拡張機能" src="https://github.com/user-attachments/assets/3040c0f5-1658-47e2-a439-20504a384f77" />

1. VS Codeの上部にある**Copilotアイコン**を見つけてクリックし、Copilotチャットパネルを開きます。

   <img width="150" alt="画像" src="https://github.com/user-attachments/assets/5e64db46-95cb-415d-badc-b6b8677f10c1" />

1. GitHub Copilotを初めて使用する場合は、続行するために利用規約に同意する必要があります。

1. Copilotにプロジェクトを紹介してもらうために、以下のプロンプトを入力します。

   > ![静的バッジ](https://img.shields.io/badge/-プロンプト-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > @workspace このプロジェクトの構造を簡単に説明してください。
   > 実行するにはどうすればよいですか？
   > ```

   > **注**: Copilotが推奨する指示に従う必要はありません。環境はすでに準備されています。

   <details>
   <summary>@workspaceとは何ですか？</summary>
   詳細に気づきましたね、素晴らしいです！でも、今はとりあえず使ってみましょう。🤓 次のステップで説明することをお約束します。
   </details>

1. プロジェクトについて少し詳しくなったので、実際に実行してみましょう！左側のサイドバーで`実行とデバッグ`タブを選択し、**デバッグの開始**アイコンを押します。

   <img width="300" alt="画像" src="https://github.com/user-attachments/assets/50b27f2a-5eab-4827-9343-ab5bce62357e" />

1. ウェブページがブラウザで実行されているのを見たいので、URLとポートを見つけましょう。表示されていない場合は、下部パネルを展開し、**ポート**タブを選択します。

1. リストでポート`8000`と関連するリンクを見つけます。リンクにカーソルを合わせ、**ブラウザで開く**アイコンを選択します。

   ![画像](https://github.com/user-attachments/assets/92d5642e-ce99-4a66-850c-2d311a673596)

### :keyboard: アクティビティ: Copilotを使ってターミナルコマンドを思い出す 🙋

素晴らしい！アプリに慣れて動作することも確認できたので、Copilotにブランチの開始を手伝ってもらい、カスタマイズを行いましょう。

1. まだVS Codeに戻っていない場合は、VS Codeに戻ります。

1. 下部パネルで**ターミナル**タブを選択します。右側でプラス`+`記号をクリックして、新しいターミナルウィンドウを作成します。

   > **注:** これにより、ウェブアプリケーションサービスをホストしている既存のデバッグセッションを停止するのを避けることができます。

1. 新しいターミナルウィンドウ内で、キーボードショートカット`Ctrl + I`（Windows）または`Cmd + I`（Mac）を使用して、**Copilotのターミナルインラインチャット**を表示します。

1. 忘れてしまったコマンド（ブランチを作成して発行する）を思い出すためにCopilotに助けを求めましょう。

   > ![静的バッジ](https://img.shields.io/badge/-プロンプト-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > ねぇ、Copilot、新しいGitブランチを作成して発行するにはどうすればいいの？
   > ```

   > **ヒント:** これは簡単な例ですが、Copilotはループ、パターンマッチング、ファイル変更などを含む、よりカスタマイズされたコマンドを提供するのに優れています！Copilotに提案を求めることを恐れないでください。ただし、それはあくまで提案であり、安全のために常に最初に確認する必要があることを忘れないでください。

1. Copilotはおそらく次のようなコマンドを提案したでしょう。手動で変更するのではなく、Copilotに特定の名前を使用するように応答しましょう。

   ```bash
   git checkout -b {new_branch_name}
   git push -u origin {new_branch_name}
   ```

   > ![静的バッジ](https://img.shields.io/badge/-プロンプト-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > 最高！ありがとう、Copilot！
   > ブランチ名は "accelerate-with-copilot" を使おう。
   > ```

   > **ヒント:** Copilotが期待通りのものをくれなかった場合でも、必要なものを説明し続けることができます。Copilotはフォローアップの応答のために会話履歴を記憶します。

1. コマンドに満足したら、`実行`ボタンを押してCopilotに実行させましょう。コピー＆ペーストは不要です！

1. しばらくすると、VS Codeの下部ステータスバーの左側でアクティブなブランチを確認します。`accelerate-with-copilot`と表示されていれば、このステップは完了です！

1. ブランチがGitHubにプッシュされたので、Monaはすでにあなたの作業をチェックしているはずです。少し待って、コメントに注意してください。彼女が進行状況の情報と次のレッスンで応答するのがわかります。

<details>
<summary>困っていますか？ 🤷</summary><br/>

フィードバックが得られない場合は、次の点を確認してください：

- ブランチが正確な名前 `accelerate-with-copilot` で作成されたことを確認してください。プレフィックスやサフィックスは付けないでください。
- ブランチが実際にリポジトリに発行されたことを確認してください。

</details>