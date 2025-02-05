# 👋 オープンソース貢献への道

> 💡 **気づいたことがあれば、どんな小さなことでも報告してください:**
> あなたが経験した問題は、きっと他の誰かも経験しています。
> その報告が、プロジェクトをより良くする最初の一歩になります。

## 🌱 はじめの一歩：Issue報告者になろう！

> 💡 **「誰かが困っているかも」という気づきを大切に！**
>
> 最初のIssue報告は誰でも緊張するもの：
> - 「この報告は価値があるのかな…」
> - 「他の人は困ってないかも…」
> - 「英語じゃないとダメかな…」
>
> でも、あなたの気づきは貴重な情報です：
> - 誰かが同じ問題で困っているはず
> - 報告があれば修正のチャンス⭐️
> - 日本語での報告もウェルカム🤗

### Issueの基本構成

```markdown
## 概要
[問題の簡潔な説明]

## 再現手順
1. [具体的な手順1]
2. [具体的な手順2]
3. [具体的な手順3]

## 期待される動作
[本来どう動作するべきか]

## 実際の動作
[現在どう動作しているか]

## 環境情報 （必要な場合）
- OS: [OS名とバージョン]
- コマンドのバージョン: x.x.x
```

> 🤖 **Issueの書き方に困ったら：**
> エラーメッセージや状況をAIに伝えて「これをIssueの形式で書いてください」と依頼してみましょう。
> AIが整理された形で問題を記述してくれます。それを確認して投稿すれば OK です！


## 🌿 次のステップ：テストライターになろう！

> 💡 **テストは最高の問題報告です！**
>
> テストがあると、みんなが助かります：🤝
> - 再現環境構築なしで問題を確認できる👍
> - 修正の確認も一発で済む👍
> - 期待する動作が明確になる👍
> - その後自動で問題を検知できる👍

### PHPUnitの基本

> AAA（アレンジ・アクト・アサート）パターンを覚えれば、テストも簡単に書けます：
>
> 1. **Arrange**: 準備する（舞台を整える）
> 2. **Act**: 実行する（主役を演じる）
> 3. **Assert**: 確認する（結末を確かめる）
>
> この3ステップで、コードの振る舞いをストーリーのように表現します！

```php
use PHPUnit\Framework\TestCase;

class StringCalculatorTest extends TestCase
{
    public function testCanAddNumbers()
    {
        // 1. テスト対象のインスタンスを作成（Arrange）
        $calc = new StringCalculator();

        // 2. テスト対象の実行（Act）
        $result = $calc->add("1,2");

        // 3. 結果の検証（Assert）
        $this->assertEquals(3, $result);
    }

    public function testEmptyStringReturnsZero()
    {
        $calc = new StringCalculator();
        $result = $calc->add("");
        $this->assertEquals(0, $result);
    }

    public function testCanHandleNewLines()
    {
        $calc = new StringCalculator();
        $result = $calc->add("1\n2,3");
        $this->assertEquals(6, $result);
    }

    /**
     * @dataProvider additionProvider
     */
    public function testBasicAdditionCases($input, $expected)
    {
        $calc = new StringCalculator();
        $result = $calc->add($input);
        $this->assertEquals($expected, $result);
    }

    public function additionProvider()
    {
        return [
	        'single number' => ['1', 1],
	        'two numbers' => ['1,2', 3],
	        'three numbers' => ['1,2,3', 6],
	        'calculation with zero' => ['0,1,2', 3],
	    ];
    }
}
```

## 🌳 さらなる成長：問題解決者になろう！

> 💡 **「直せたらいいな」その気持ちを行動に！**
>
> バグ修正や機能改善は誰でも最初は不安なもの：
> - 「コードベースが大きい…」
> - 「修正の影響が心配…」
> - 「方針は正しいのかな…」
>
> でも大丈夫。AIと[MergeClip](https://github.com/koriym/MergeClip)が、あなたの問題解決をサポートします！

### ステップ1: 問題を理解する

```bash
# 関連コードをMergeClipで取り込む
mergeclip /path/to/related/files
# または Finder で関連ファイルを選択して右クリック > クイックアクション > MergeClip
# コードと問題を示してAIに質問例
「このIssueに関連するコードの動作を説明してください」
「このバグが発生する原因として考えられるものは？」
```

### ステップ2: 解決策を考える
```bash
# AIに相談例
「このバグを修正するための方法を提案してください」
「この修正による他への影響はありますか？」
```

### ステップ3: 修正を実装する
```bash
# 修正案をAIに確認
「この修正方法は適切でしょうか？」
「必要なテストケースを提案してください」
```

## まとめ

1. **小さな一歩から始めよう**
    - 気づいたことを報告するところから始める
    - AIのサポートを活用する

2. **テストで品質向上に貢献**
    - 具体例から始める
    - データプロバイダーで網羅的なテスト

3. **問題解決に挑戦**
    - AIとMergeClipを活用
    - 段階的にアプローチ

あなたの貢献が、プロジェクトの品質向上に直接つながります！
プロジェクトと共に成長していきましょう 🌟
