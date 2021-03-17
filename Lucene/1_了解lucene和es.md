## 翻译

- lucene
- elastic（有弹性的、可伸缩的）search

## 大概lucene

> https://lucene.apache.org/

[Lucene Core](https://lucene.apache.org/core/) is a Java library providing powerful **indexing** and **search** features, as well as spellchecking, hit highlighting and advanced analysis/tokenization capabilities.

- lucene core：全文检索Java类库
- 提供特性：
  - **建索引**【store】
  - **搜索引**【search】
  - 拼写检查
  - 检索高亮
  - 分析能力【analyze】
  - 分词（符号识别）能力

## 大概es

**Elasticsearch** is a [search engine](https://en.wikipedia.org/wiki/Search_engine_(computing)) based on the [Lucene](https://en.wikipedia.org/wiki/Lucene) library.

It provides a distributed, [multitenant](https://en.wikipedia.org/wiki/Multitenancy)-capable [full-text search](https://en.wikipedia.org/wiki/Full-text_search) engine with an [HTTP](https://en.wikipedia.org/wiki/HTTP) web interface and schema-free [JSON](https://en.wikipedia.org/wiki/JSON) documents.

- es：搜索引擎（基于全文检索类库 / 基于lucene）
- 特性：
  - lucene有的，es肯定也有【store / search】
  - 分布式
  - 弹性的
  - 基于HTTP
  - 基于JSON

## lucenu vs es

- lucenu【**全文检索类库**】【导入jar包】
- es【**搜索引擎**（基于全文检索类库）】【需要部署到服务器】（http通信）