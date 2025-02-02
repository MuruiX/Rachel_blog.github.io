---
LINK:
  - ""
  - "[[Text Mining]]"
File: Data Science/Text Mining/Annotation Formats.md
---



## Understanding documents
Documents rarely have a simple structure 很少有簡單結構
Documents are meant to be <font color="#ffc000">human-readable</font>

> [!example] 
> - news article
> - research article

 
# Annotations:

## Enabling machine-readablility
![](PICTURE/Annotation%20Formats/7d1b5a0b7c4e5839be878e737addcad1_MD5.jpeg)
![](PICTURE/Annotation%20Formats/238e557e0f22df25014bc279d43f59ee_MD5.jpeg)


![](PICTURE/Annotation%20Formats/40f8d04fe843998f78dd0efdf6bb66c0_MD5.jpeg)
![](PICTURE/Annotation%20Formats/875ad453c826788203008d9d15282031_MD5.jpeg)

如圖展示的 他從單純的文字變成機器可讀的樣式

## Types of annotation Formats
Boundary notation 邊界符號
Inline markup language elements 內聯標記語言元素
Stand-off
- delimiter-separated values (DSV)
- JSON


## Boundary Notation 
Done at the level of individual tokens 在單個token完成
How do we encode units of interest spanning several tokens
<span style="background:#fdbfff">BIO:  B=Begin  I=Inside  O=Outside</span>

> [!example] 
![](PICTURE/Annotation%20Formats/cf744d8fb3b8ce28a2fafdc77989c298_MD5.jpeg)

- Strengths
	- simple
- limitations
	- cannot handle hierarchical or structured annotations e.g., nested entities(NES) 嵌套實體, relations events

> [!example] Nested entities 
> 
> ![](PICTURE/Annotation%20Formats/0e2b147836c53694ebb0f343da45b599_MD5.jpeg)
> 
> 展示了Named Entity Recognition (NER) 命名實體識別的結果
>  - 是一種NLP技術，用來識別文本中的關鍵實體，比如**地名 (GPE)**，**組織 (Org)**, **人物 (Person)** 和 **事件 (Conflict_Attack)**  
> 	- GPE：
> 		- 國家或地區名稱
> 	- Org：
> 		- 機構或組織的名稱
> 	- Person：
> 		- 具體人名
> 	- Contact_Meet：
> 		- 這類標籤標識涉及會議或高級別會議
> 	- Conflict_Attack（衝突/攻擊, Conflict_Attack
> 		- 標識與戰爭或攻擊有關的事件
> 	- 關係標註（箭頭）
> 		- 表示某人參與了一場活動
> 		- Target (目標)
> 		- 標識某個實體是某個行動的目標
> 
> 
> 



## Inline markup language elements
By addition of markup tags within text
- HTML
- XML

> [!example] 
> ![](PICTURE/Annotation%20Formats/27f458b086a56bae386e7574e187abb7_MD5.jpeg)
> 
> ![](PICTURE/Annotation%20Formats/be4dee88da8aca76cac817831d410773_MD5.jpeg)

Strengths:
- can handle annotations which are hierarchical (e.g., nested NEs, trees) and structured (e.g., events) 可以處理分層的注釋 
Limitations:
- requires substantial processing with standard XML parsers 對標準XML處理器進行大量處理
- impossible to encode overlapping/intersecting annotations, e.g., second Iraqi city of Basra 無法編碼重疊/相交注釋

## Stand-off Annotations (JSON格式)
將標註信息與原始文本分離的標註方式，而不是將標註直接嵌入到文本內部。

### **為什麼使用 Stand-off Annotation？**

1. **避免污染原始數據**：原始文本保持不變，標註信息存儲在外部文件或數據結構中。
2. **允許多層次標註**：可以為相同文本提供多種標註（如詞性、語法結構、命名實體等），並獨立管理它們。
3. **便於版本控制**：標註數據和原始文本分開存儲，有助於管理不同版本的標註信息。
4. **支持長文本處理**：對於超大文本，標註信息存儲在索引數據結構中，提高效率。


> [!example]+
> ```text
> UK and US discuss the role of UN.
> ```
> 
> stand-off 標註文件
> ```JSON
> {
>     "text": "UK and US discuss the role of UN.",
>     "annotations": [
>         {
>             "id": "T1",
>             "type": "GPE",
>             "start": 0,
>             "end": 2,
>             "text": "UK"
>         },
>         {
>             "id": "T2",
>             "type": "GPE",
>             "start": 7,
>             "end": 9,
>             "text": "US"
>         },
>         {
>             "id": "T3",
>             "type": "ORG",
>             "start": 27,
>             "end": 29,
>             "text": "UN"
>         }
>     ]
> }
> ```
> 
> 

annotations are stored separately
requires a way to link between annotations and text
links annotations to text using indexing based on character offsets (computed over raw
text)


- strength:
	- original raw text is left untouched 原始文本未觸及
	- can handle structured and overlapping annotations 可以處理結構化和重疊的注釋
- limitations:
	- **not readily human-readable** 
























