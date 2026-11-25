# clean-engineering-code-style

工业级代码、注释编写与单元测试去“AI味”规范。消除过度设计、废话注释与假单测，推行高信噪比的大厂工程实践。

## 核心治理维度

1. **注释去AI味**：严禁翻译代码的废话注释；强制解释业务意图（Why）与约束（Constraints）；消除 AI 助手的客套话与元标签；拒绝无意义 Docstring 轰炸。
2. **架构与实现去AI味**：严禁为简单逻辑套用多个设计模式（遵守 KISS/YAGNI 原则）；杜绝未声明的幽灵依赖与幻觉 API；严禁捕获顶层异常后吞掉堆栈返回 null。
3. **语言特异性治理**：Java 避免滥用 Stream 与 Optional；Python 消除可变默认参数与缺少上下文管理器的问题；TypeScript 杜绝 any 滥用与 useEffect 依赖死循环；Go 杜绝忽略 err 与协程泄漏。
4. **单测去AI味**：拒绝全员 Happy-Path 假单测；拒绝重言式 Mock 自嗨测试；拒绝缺乏断言的幽灵单测；统一 AAA 结构与行为命名。
5. **SQL与高并发**：严禁 SELECT *；避免深分页性能陷阱；规范 Redis 分布式锁原子获取、自动续期与 Lua 释放。

## 安装与使用

### Antigravity
运行内置脚本将技能安装到本地：
`powershell
powershell -ExecutionPolicy Bypass -File scripts/install.ps1
`

### Git / 手动安装
将 `skills/clean-engineering-code-style` 复制至 `~/.gemini/config/skills/` 目录即可。

## License
MIT
