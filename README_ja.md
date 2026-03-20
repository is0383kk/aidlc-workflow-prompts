# AI 駆動開発ライフサイクル（AI-DLC）プロンプト

このリポジトリは、Amazon Web Services が提案する「[AI-Driven Development Lifecycle（AI-DLC）](https://prod.d13rzhkk8cj2z0.amplifyapp.com/)」のプロセスに沿ったプロダクト開発をするためのプロンプトを格納しています。

- https://aws.amazon.com/jp/blogs/news/ai-driven-development-life-cycle/

※プロンプト実行は、**Amazon Q developer CLI／Claude Code／Codex CLI などの AI エージェントの対話を前提**として設計されています。

# １．概要

本プロンプト集は、以下の 5 つのフェーズで構成されています

1. **ユーザーストーリー計画** - 要件をユーザーストーリーとして定義します
2. **作業単位分割計画** - ユーザーストーリーを実装可能な作業ユニットに分割します
3. **ドメインモデル設計計画** - ビジネスロジックのドメインモデルを設計します
4. **コード実装計画** - ドメインモデルからソースコードを実装します
5. **アーキテクチャコンポーネント計画** - 実装物を動作させるためのアーキテクチャを構築します

## ■ プロンプト構成

```
├── 01-user-story-planning.md          # ユーザーストーリー作成プロンプト
├── 02-unit-of-work-planning.md       # 作業単位分割プロンプト
├── 03-domain-model-planning.md        # ドメインモデル設計プロンプト
├── 04-domain-to-code-planning.md      # コード実装プロンプト
└── 05-architecture-component-planning.md  # アーキテクチャコンポーネント作成プロンプト

```

# ２．使用方法

## ■ 基本的な作業の流れ

1. **プロンプトを選択**: 開発フェーズに応じたプロンプトファイルを選択
2. **AI アシスタントに入力**: 選択したプロンプトを AI アシスタントに入力
3. **計画書の作成**: AI が作業計画書を作成
4. **質問への回答**: 計画書内の質問に回答
5. **計画の承認**: 作業計画をレビューし承認
6. **ステップバイステップ実行**: AI が計画に沿って 1 ステップずつ実行

## ■ ステップ 1. ユーザーストーリー作成 (`01-user-story-planning.md`)

**役割**: プロダクトオーナー
**目的**: 開発対象のシステムに対する明確なユーザーストーリーを作成

0. 【任意】コンテキストをクリアします
1. `01-user-story-planning.md`に作成したいものを記述し、ファイル内のプロンプトを実行します
2. ユーザストーリ作成のための作業計画書が作成されます: `docs/inception/01-user-story/user-story-plan.md`
3. `docs/inception/01-user-story/user-story-plan.md`内に質問事項が記載されているので回答し保存します
4. AI エージェントに`docs/inception/01-user-story/user-story-plan.md`に従いユーザストーリを作成するように指示します
5. `docs/inception/01-user-story/result`にユーザストーリに関するワークダウンファイルが作成されます

## ■ ステップ 2. 作業単位分割 (`02-unit-of-work-planning.md`)

**役割**: ソフトウェアアーキテクト
**目的**: ユーザーストーリーを並行実装可能な作業ユニットに分割

0. 【任意】コンテキストをクリアします
1. `02-unit-of-work-planning.md`内のプロンプトを実行します
2. ユーザストーリを分割するための作業計画書が作成されます: `docs/inception/02-unit-of-work/units-plan.md`
3. `docs/inception/02-unit-of-work/units-plan.md`内に質問事項が記載されているので回答し保存します
4. AI エージェントに`docs/inception/02-unit-of-work/units-plan.md`に従いユーザストーリを作業分割するように指示します
5. `docs/inception/02-unit-of-work/result`に作業分割後のユーザストーリが出力されます

## ■ ステップ 3. ドメインモデル設計 (`03-domain-model-planning.md`)

**役割**: ソフトウェアエンジニア
**目的**: ユーザーストーリーを実装するためのドメインモデル設計

0. 【任意】コンテキストをクリアします
1. ドメインモデル設計対象となるユーザストーリ（例：`unit1-task-creation.md`）を選択し、`03-domain-model-planning.md`のインプットに指定します
2. `03-domain-model-planning.md`内のプロンプトを実行します
3. ユーザストーリからドメインモデル設計を行うための作業計画書が作成されます: `docs/construction/03-domain-model/domain-model-plan.md`
4. `docs/construction/03-domain-model/domain-model-plan.md`内に質問事項が記載されているので回答し保存します
5. AI エージェントに`docs/construction/03-domain-model/domain-model-plan.md`に従いユーザストーリを作業分割するように指示します
6. `docs/construction/03-domain-model/unitX/result`にドメインモデル設計書が作成されます

## ■ ステップ 4. 実装 (`04-domain-to-code-planning.md`)

**役割**: ソフトウェアエンジニア
**目的**: ドメインモデル設計からソースコードを実装

0. 【任意】コンテキストをクリアします
1. 実装対象となるドメインモデル設計（例：`docs/inception/03-domain-model/unitX/result/`）を選択し、`04-domain-to-code-planning.md` のインプットに指定します
2. `04-domain-to-code-planning.md` 内のプロンプトを実行します
3. ドメインモデル設計から実装を行うための作業計画書が作成されます: `docs/construction/04-domain-to-code/unitX/domain-to-code-plan.md`
4. `docs/construction/04-domain-to-code/unitX/domain-to-code-plan.md` 内に質問事項が記載されているので回答し保存します
5. AI エージェントに`docs/construction/04-domain-to-code/unitX/domain-to-code-plan.md`に従いユーザストーリを作業分割するように指示します
6. ドメインモデル設計から実装物が作成されます（例：`task_management`）

## ■ ステップ 5. アーキテクチャコンポーネント作成 (`05-architecture-component-planning.md`)

**役割**: ソフトウェアアーキテクト
**目的**: 実装物を動作させるためのアーキテクチャコンポーネントを追加

0. 【任意】コンテキストをクリアします
1. 対象となる実装物のディレクトリ（例：`task_management`）を選択し、`05-architecture-component-planning.md` のインプットに指定します
2. 対象となる作業分割後のユーザストーリ（例：`docs/inception/02-unit-of-work/result/unitX-XXX.md`）を選択し、`05-architecture-component-planning.md` のインプットに指定します
3. `05-architecture-component-planning.md` 内のプロンプトを実行します
4. アーキテクチャコンポーネント作成のための作業計画書が作成されます: `docs/construction/05-architecture-component/architecture-component-plan.md`
5. `docs/construction/05-architecture-component/architecture-component-plan.md` 内に質問事項が記載されているので回答し保存します
6. AI エージェントに `docs/construction/05-architecture-component/architecture-component-plan.md`に従いアーキテクチャコンポーネントを作成するように指示します
7. アーキテクチャコンポーネントが作成されます

# ３．成果物の構造

プロンプト実行により、以下のような構造でドキュメントと実装物が生成されます：

```
docs/
├── inception/                  # 企画・計画フェーズ
│   ├── 01-user-story/
│   │   ├── user-story-plan.md
│   │   └── result/
│   └── 02-unit-of-work/
│       ├── units-plan.md
│       └── result/
│           ├── unit1-*.md
│           └── unit2-*.md
├── construction/               # 構築フェーズ
│   ├── 03-domain-model/
│   │   └── unitX/
│   │       ├── domain-model-plan.md
│   │       └── result/
│   ├── 04-domain-to-code/
│   │   └── unitX/
│   │       └── domain-to-code-plan.md
│   └── 05-architecture-component/
│       └── architecture-component-plan.md
│
└── ソースコード＋アーキテクチャコンポーネント
```
