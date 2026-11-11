# Walmart 评论分析与检索系统

此代码库提供用于抓取、处理和分析沃尔玛客户评论的工具。该系统利用 Pinecone 进行向量存储，使用 Sentence Transformers 实现语义搜索，并使用 Google Gemini AI 提取和分析评论。

## 组件

- **`rag-chatbot.py`**：用于初始化服务，并通过检索增强生成（RAG）流水线生成响应的主脚本。
- **`review_to_pinecone.py`**：处理已提取的评论、生成嵌入向量并将其存储到 Pinecone 中。
- **`semantic_search_client.py`**：提供对已存储嵌入向量执行语义搜索查询的服务。
- **`walmart_review_extractor.py`**：使用 Bright Data 从沃尔玛抓取评论，并通过 Google Gemini AI 进行处理。

## 先决条件

- Python 3.7+
- Pinecone、Gemini AI 和 Bright Data 的访问密钥。

## 设置

1. 克隆代码库：
   - `git clone https://github.com/yourusername/your-repo.git`
   - `cd your-repo`

2. 安装所需的 Python 软件包：
   - `pip install -r requirements.txt`

3. 在根目录中创建 `.env` 文件以设置环境变量。添加以下变量：
   - `PINECONE_API_KEY=your_pinecone_api_key`
   - `GEMINI_API_KEY=your_gemini_api_key`
   - `BRIGHT_DATA_API_KEY=your_bright_data_api_key`

4. 将你的评论数据集文件（`extracted_walmart_reviews.json`）放在项目根目录中以供处理。

## 使用方法

### 提取评论

使用 `walmart_review_extractor.py` 从沃尔玛获取评论：
- `python walmart_review_extractor.py`

### 处理评论并填充 Pinecone

使用以下命令处理已提取的评论，并将其更新插入 Pinecone：
- `python review_to_pinecone.py`

### 语义搜索

使用以下命令对已建立索引的数据执行语义搜索：
- `python semantic_search_client.py`

### 运行 RAG 聊天机器人

最后，使用以下命令运行 RAG 流水线并与之交互：
- `python rag-chatbot.py`

## 日志记录

日志保存在 `data_pipeline.log` 中，同时也会输出到控制台，以便实时监控。

## 注意

请确保正确配置所有必需的环境变量和 API 密钥，以保证脚本顺畅运行。
