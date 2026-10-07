# 导学阶段-Rust 语言基础

基于 [LearningOS 2026s Rustlings 课程模板](https://github.com/LearningOS/2026s-rustling-classroom-template)，共 **110 题，每题 1 分，总分 110 分**。

## 使用流程

1. 加入 [OpenCamp 秋冬季训练营](https://opencamp.cn/os2edu/camp/2026fall)，并绑定自己的 GitHub 账号。
2. 使用课程方提供的领取链接，点击 **Create** 提交申请；等待机器人回复，然后接受仓库邀请。
3. 安装 Git 并克隆分配的仓库，在 `main` 分支完成 `exercises/` 中的练习。
4. 提交并 push，在仓库 **Actions** 查看评测和上传结果，在 [OpenCamp 本阶段排行榜](https://opencamp.cn/os2edu/camp/2026fall/stage/2) 查看成绩。

OpenCamp 绑定的账号、领取仓库的账号和推送使用的 GitHub 账号应一致。

首次使用时，先完成下面的[环境配置](#环境配置)。

完成一部分练习后提交：

```sh
git add exercises
git commit -m "Complete Rustlings exercises"
git push origin main
```

三条命令依次保存练习改动、创建提交、推送到 `main` 并触发自动评测。

## 计分规则

每次提交都会重新运行全部题目，以本次实际通过题数计分。编译、运行或测试失败及超时的题目记 0 分；其他已通过题目正常计分并上传。计分不按提交次数累加，也不只检查注释是否删除。

评测覆盖上游的编译运行、单元测试、Clippy 和构建脚本四类题目。单题限时 20 秒；评测工具构建失败或结果不完整时不上传成绩。

Actions 中 **Test exercises and calculate score** 变红表示还有未完成的题目；**Save measured score and upload to OpenCamp** 成功表示成绩同步成功。每道题的原始日志和成绩明细保存在该次运行的附件中。

## 环境配置

进入自己的作业仓库目录，按照操作系统执行一次配置命令。

**Windows（64 位 Intel / AMD）**：在 PowerShell 中运行：

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\setup-windows.ps1
```

脚本会自动安装所需的 Microsoft C++ Build Tools、Windows SDK 和 Rust 工具链，无需手动勾选组件。出现 Windows 管理员权限提示时允许安装；如提示重启，重启后再次运行该命令。

**macOS / Linux**：在终端中运行：

```sh
bash setup.sh
```

此命令使用 Bash 执行配置脚本。macOS 需要先安装 Command Line Tools，Linux 需要系统 C 编译器。

脚本会准备课程需要的 Rust 环境，并直接启动练习。按照终端提示修改题目，完成后移除对应的 `I AM NOT DONE` 注释。输入 `quit` 退出。

### 以后继续练习

重新打开终端，进入作业仓库目录，运行：

```sh
cargo run -- watch
```

此命令启动练习检查器，保存题目后自动重新检查。

## 做题方法

### 从哪道题开始，为什么初始有 30 分

课程模板已经提供了前 **30 题**的完成代码，范围是练习列表中的 `intro2` 到 `move_semantics6`，包括变量、函数、条件表达式、基本类型、Vector、所有权练习，以及综合练习 `quiz1`。这些题已经移除了 `I AM NOT DONE` 注释，并能通过各自的编译、运行或测试检查。

每题通过得 1 分，因此这 30 道已完成的题构成模板的初始 **30 分**。

从 **`exercises/structs/structs1.rs`** 开始完成剩余 80 题。前 30 题可以作为示例阅读，不需要重新作答。

### 怎样完成一道题

1. 根据终端显示的路径打开当前题目。先读该主题目录的 `README.md` 和文件顶部的说明；有单元测试时，再看测试中的输入与 `assert!`、`assert_eq!` 等断言，明确代码需要满足什么行为。
2. 补全 `TODO`、缺失的实现或题目要求修复的代码。有些题目还要求补全测试中的实例或断言，应按题目说明修改；不要通过删除测试或绕过题目要求让检查通过。
3. 保存文件，查看运行中的检查器输出。编译失败时，按报错中的文件位置修正类型、语法或借用等问题；测试失败时，对照断言的实际值和预期值修正实现。刚开始看到未完成题目的报错是正常的。
4. 没有思路时，在运行 `watch` 的终端输入 `hint` 并按 Enter，查看当前题目的提示。
5. 确认该题编译、运行或测试通过后，删除文件中的 `// I AM NOT DONE` 注释，再保存一次。检查器会继续下一题；只删除注释、没有修好代码，仍然不能通过评测。

例如，`structs1` 要求补全普通结构体、元组结构体，并在测试中创建所需的实例。先看断言访问了哪些字段、要求什么值，再补全对应的 `TODO`，直到已有测试全部通过。

不是所有题目都采用单元测试：有的要求程序能够编译并正常运行，有的要求通过 Clippy 检查，还有构建脚本练习。以题目说明和检查器结果为准。

在 `watch` 终端输入 `quit` 并按 Enter 可以退出。完成一部分题目后，按上面的「使用流程」保存并推送代码，才会触发课程评测和成绩同步。

### 常用检查命令

以下命令均在仓库根目录运行。`cargo run` 启动本仓库的练习工具，`--` 后面的参数交给该工具：

| 命令 | 用途 |
| --- | --- |
| `cargo run -- run structs1` | 只检查 `structs1`，可换成其他题目名 |
| `cargo run -- hint structs1` | 查看该题提示 |
| `cargo run -- run next` | 运行下一道未完成的题目 |
| `cargo run -- hint next` | 查看下一道未完成题目的提示 |
| `cargo run -- list` | 查看题目列表及 `Done` / `Pending` 标记状态 |
| `cargo run -- verify` | 从头检查，遇到首个未通过或仍保留未完成标记的题目时停止 |
| `cargo run -- lsp` | 生成 `rust-project.json`，供编辑器中的 rust-analyzer 识别各个练习 |

`list` 的 `Done` / `Pending` 来自题目中的未完成注释，不代表重新测试后的结果。最终成绩以流水线实际运行的检查结果为准。

`exercises/quiz1.rs`、`quiz2.rs`、`quiz3.rs` 是阶段综合练习，用于巩固前面学过的内容。交互工具按仓库练习列表运行；下面的教材表用于安排阅读顺序。

除 [Rust Book 中文版](https://rustwiki.org/zh-CN/book/) 外，也可以配合 [Rust By Example](https://doc.rust-lang.org/rust-by-example/) 阅读示例。完成本阶段后，继续基础阶段实验，或选择一个小项目巩固 Rust 编程。

### 在浏览器中练习

打开机器人分配给自己的作业仓库，选择 **Code → Codespaces → Create codespace on main**。等待仓库的开发环境初始化，然后在终端运行 `cargo run -- watch`，编辑 `exercises/` 中的题目。完成后仍需提交并 push，才会触发课程评测。

Codespaces 使用自己账号的可用额度；环境启动失败时，按本页环境配置在本地继续练习。

使用 Nix 的同学可参考仓库保留的 [flake.nix](flake.nix) 和 [shell.nix](shell.nix) 开发环境配置。

### 遇到问题

先查看题目提示与编译器报错。push 需要使用领取仓库的 GitHub 账号，并已接受仓库邀请。若成绩上传失败，核对 OpenCamp 的训练营报名和 GitHub 绑定，再向助教提供 Actions 运行链接及错误信息。

上游贡献说明见 [CONTRIBUTING.md](CONTRIBUTING.md)，贡献者见 [AUTHORS.md](AUTHORS.md)。

## 练习顺序与教材章节

建议配合 [《Rust 程序设计语言》（Rust Book）](https://rustwiki.org/zh-CN/book/) 学习，按照下表顺序阅读教材并完成 `exercises/` 中的练习。

| 顺序 | 练习目录 | 对应教材内容 |
|---:|---|---|
| 1 | `intro` | §1.2：Hello, World! |
| 2 | `variables` | §3.1：变量与可变性 |
| 3 | `primitive_types` | §3.2：数据类型；切片部分结合 §4.3 |
| 4 | `functions` | §3.3：函数 |
| 5 | `if` | §3.5：控制流 |
| 6 | `move_semantics` | §4.1–4.2：所有权、引用与借用 |
| 7 | `structs` | 第 5 章：结构体 |
| 8 | `enums` | 第 6 章：枚举与模式匹配 |
| 9 | `options` | §6.1–6.3：`Option`、`match` 与 `if let` |
| 10 | `modules` | 第 7 章：包、Crate 与模块 |
| 11 | `vecs` | §8.1：Vector |
| 12 | `strings` | §8.2：字符串 |
| 13 | `hashmaps` | §8.3：HashMap |
| 14 | `error_handling` | 第 9 章：错误处理 |
| 15 | `generics` | §10.1：泛型数据类型 |
| 16 | `traits` | §10.2：Trait |
| 17 | `lifetimes` | §10.3：生命周期 |
| 18 | `tests` | 第 11 章：自动化测试，先完成 `tests1–4` |
| 19 | `iterators` | §13.2–13.4：迭代器 |
| 20 | `smart_pointers` | 第 15 章：智能指针；`Arc` 结合 §16.3 |
| 21 | `threads` | 第 16 章：并发编程 |
| 22 | `macros` | §19.5：宏 |
| 23 | `clippy` | 附录 D：开发工具 |
| 24 | `conversions` | 补充练习：类型转换，参考[标准库文档](https://doc.rust-lang.org/std/convert/index.html) |
| 25 | `algorithm` | 补充练习：数据结构与算法 |
