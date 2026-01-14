📈 A-Share Wyckoff AI Analyst (A股威科夫AI分析师)这是一个基于 Python 的自动化股票分析工具。它结合了传统的威科夫理论 (Wyckoff Theory) 与现代 AI 大模型 (GPT-4o / DeepSeek)，能够自动拉取 A 股分钟级数据，绘制专业的 K 线图表，并生成包含趋势推演的分析报告。Shutterstock探索✨ 主要功能数据获取: 使用 Akshare 接口获取 A 股实时/历史分钟级 K 线数据。专业绘图: 使用 mplfinance 本地生成高清 K 线图，包含成交量、MA50、MA200 均线，完美适配威科夫分析需求。AI 深度分析:角色扮演: AI 扮演理查德·威科夫本人进行分析。核心逻辑: 基于供求关系、因果定律、努力与结果三大定律。多模型支持: 兼容 OpenAI (GPT-4o) 和 DeepSeek (V3/R1) 等支持 OpenAI 格式的 API。自动化报告: 输出 Markdown 格式的完整日报，内嵌图表链接。🛠️ 环境准备确保你的环境安装了 Python 3.8 或以上版本。1. 安装依赖在项目根目录下创建 requirements.txt 并运行安装命令：Bashpip install -r requirements.txt
requirements.txt 内容:Plaintextpandas
akshare
mplfinance
openai
⚙️ 配置 (环境变量)本项目完全通过环境变量进行配置，既支持本地运行，也完美适配 GitHub Actions。变量名必填默认值说明OPENAI_API_KEY✅-你的 API 密钥 (OpenAI 或 DeepSeek)SYMBOL❌600970股票代码 (支持 6/0/3/4/8 开头)BARS_COUNT❌600获取的分钟 K 线数量 (决定图表跨度)OPENAI_BASE_URL❌https://api.openai.com/v1DeepSeek 用户必填: https://api.deepseek.comAI_MODEL❌gpt-4o-mini指定模型，如 deepseek-chat 或 gpt-4o💡 配置示例1. 使用 DeepSeek (推荐)如果你使用 DeepSeek 进行分析：Bashexport OPENAI_API_KEY="sk-xxxxxxxx"
export OPENAI_BASE_URL="https://api.deepseek.com"
export AI_MODEL="deepseek-chat"
export SYMBOL="600519"
2. 使用 OpenAIBashexport OPENAI_API_KEY="sk-xxxxxxxx"
export AI_MODEL="gpt-4o"
export SYMBOL="000001"
🚀 运行方法本地运行 (Linux/Mac)Bash# 设置临时的环境变量并运行
export OPENAI_API_KEY="your_key_here"
export SYMBOL="601888"
python main.py
Windows PowerShellPowerShell$env:OPENAI_API_KEY="your_key_here"
$env:SYMBOL="601888"
python main.py
📂 输出文件结构运行成功后，脚本会自动创建以下目录和文件：Plaintext.
├── data/
│   └── 600970_1min_20231218_120000.csv   # 原始行情数据
├── reports/
│   ├── 600970_chart_20231218_120000.png  # 本地生成的威科夫 K 线图
│   └── 600970_report_20231218_120000.md  # AI 生成的分析报告
└── main.py
🧠 AI 分析逻辑细节为了节省 Token 并提高分析精度，程序采用了以下策略：绘图: 使用 BARS_COUNT (默认600根) 绘制较长周期的图表，方便观察背景趋势 (Background)。AI 分析: 仅截取最近 120 根 (2小时) 的数据投喂给 AI。这让 AI 专注于当前的微观结构 (Micro-structure) 和最新的供求对抗，模拟盘中实时盯盘的视角。⚠️ 免责声明 (Disclaimer)本项目仅供技术研究和量化编程学习使用。AI 生成的分析报告基于历史数据推演，不构成任何投资建议。股市有风险，入市需谨慎。
