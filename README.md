# clean-engineering-code-style

工业级代码、注释编写与单元测试去“AI味”规范。消除过度设计、废话注释与假单测，推行高信噪比的大厂工程实践。

## 为什么需要这个项目？

在 AI 辅助编程普及的今天，大模型生成的代码常常充满典型的“机器坏味道”：
- **注释废话文学**：代码写 `int a = b + c;`，注释写 `// 将b和c相加赋给a`，把代码用自然语言念一遍，严重稀释视觉信噪比；
- **过度设计与虚假抽象**：20 行逻辑强套 3 个工厂、2 个策略和 1 个适配器模式，违背 KISS 与 YAGNI 原则；
- **幽灵 API 与幻觉依赖**：凭模式外推臆测不存在的 SDK 方法，甚至引入未经安全审查的外部包；
- **单测全是假测试**：只测没有任何异常的 Happy-Path；对 Mock 打桩后断言 Mock 自身的重言式自嗨测试；缺乏断言的幽灵测试；
- **扁平化吞异常**：裸写 `catch (Exception e) return null;`，直接吃掉堆栈引发下游雪崩。

本项目基于 Google 编程风格、阿里巴巴 Java 开发手册、Clean Code 与大厂 Code Review 标准，为开发者和团队提供一套立竿见影的代码去 AI 味工程化规则。

## 核心治理维度

| 治理维度 | AI 机器坏味道 (❌ 严禁) | 大厂工业级规范 (✅ 推荐) |
| :--- | :--- | :--- |
| **代码注释** | 翻译下一行代码；写 `Step 1/2/3`；无脑轰炸 Docstring。 | 严禁复述代码；仅解释 **Why（业务背景）** 与 **Constraints（时序/魔数/并发约束）**。 |
| **架构设计** | 简单业务强行堆砌多层设计模式；抽象类只有单一实现。 | 坚守 **KISS & YAGNI**，无 3 处异构不预设抽象，追求极简清晰。 |
| **异常处理** | `catch (Exception e) { log.error(e); return null; }` 吞掉异常。 | 分类捕获具体异常，透传业务错误码，完整保留 Root Cause 堆栈。 |
| **单元测试** | 全员 Happy-Path；Mock 打桩后断言 Mock 自身；幽灵断言。 | 覆盖边界矩阵（0/null/溢出/超时）；断言真实业务状态转移与副作用。 |
| **SQL与并发** | 默认 `SELECT *`；百万大表深分页直接 LIMIT；分布式锁无续期与释放校验。 | 明确查询字段；覆盖索引延迟关联分页；Redis 锁具备 Watchdog 续期与 Lua 校验释放。 |

## 快速安装与使用

### 终端一键远程安装（推荐）

#### Windows 用户（PowerShell）
```powershell
irm https://raw.githubusercontent.com/happypig1224/clean-engineering-code-style/main/scripts/install.ps1 | iex
```

#### macOS / Linux 用户（Bash）
```bash
curl -fsSL https://raw.githubusercontent.com/happypig1224/clean-engineering-code-style/main/scripts/install.sh | bash
```

### 本地安装
克隆仓库后在本地执行安装脚本：
```powershell
powershell -ExecutionPolicy Bypass -File scripts/install.ps1
```

### 手动安装
将 `skills/clean-engineering-code-style` 目录复制至本地 `~/.gemini/config/skills/` 目录即可。

## 开源协议

本项目采用 MIT 许可证。