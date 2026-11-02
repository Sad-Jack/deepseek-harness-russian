# DeepSeek Harness Russian

[English](README.md) · **简体中文** · [Русский](README.ru.md)

适用于 **DeepSeek Harness 0.2.1-rc.5** 的俄语界面语言包，基于 DeepSeek 官方翻译。

**2,909 条文本 · 64 个命名空间 · 无运行时依赖 · 不修改应用归档文件。**

本项目是将官方翻译回移到旧版 Harness 的独立语言包，**不是 DeepSeek 官方插件**。如果你的 Harness 已内置俄语，则不需要安装本包。

## 为什么创建这个项目

已安装的桌面版 **0.2.1-rc.5** 只提供英语和中文，但官方 **0.2.2-alpha.2** 源码中已经包含俄语翻译。

在 **2026 年 11 月 3 日** 检查时，应用内更新和 DeepSeek 官方 Mac 下载仍提供 **0.2.1-rc.5**；所检查的 **0.2.2-alpha.2** GitHub 发布中没有现成的 Mac 安装程序，因此无法通过更新桌面应用启用俄语。

本包通过 Harness 支持的语言包 API 将这些翻译移植到已安装版本，无需自行构建 Harness，也不修改 `app.asar`。后续桌面版本可能不再需要这个回移包。

来源：[DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness)、[0.2.2-alpha.2 发布说明](https://github.com/deepseek-ai/deepseek-harness/releases/tag/dsh-v0.2.2-alpha.2)、[语言包 API](https://github.com/deepseek-ai/deepseek-harness/blob/dsh-v0.2.2-alpha.2/packages/client/locale/README.md)。

## 兼容性

| 项目 | 支持或已验证的范围 |
| --- | --- |
| Harness 版本 | **0.2.1-rc.5**，在 `engines.dsh` 中明确声明 |
| 已手动验证的平台 | **macOS，Apple silicon** |
| 其他平台和版本 | 未手动验证，不声明更广泛的兼容性 |
| 已存在俄语语言项 | 如果 `ru` 已注册，本包跳过注册 |

安装其他俄语语言包前，请先停用本包。本包不会覆盖已有语言，也不会尝试为未经验证的新版本提供翻译。

## 安装

### 在应用内通过 GitHub 安装

1. 打开 **Plugins → Add plugin**。
2. 输入：

   ```text
   https://github.com/Sad-Jack/deepseek-harness-russian
   ```

3. 点击 **Install**，等待完成后点击 **Enable now**。
4. 打开 **Account menu → Settings → General → Language → Русский**，明确选择俄语。

如果系统语言偏好包含俄语，插件启用后界面可能立即切换。仍建议在设置中明确选择俄语，以保存偏好。如应用提示，请重启 Harness。

仓库公开，无需获得作者账号的访问权限，也无需手动安装依赖或本地构建。如果 GitHub 安装失败，可使用下方经过验证的本地目录安装方式。

### 通过命令行安装

如果已安装 `dsh` CLI：

```sh
dsh plugin --profile desktop add github:Sad-Jack/deepseek-harness-russian
```

Web 配置使用 `--profile web`。如有需要，在 **Plugins** 中启用包，然后在语言设置中选择 **Русский**。[Releases](https://github.com/Sad-Jack/deepseek-harness-russian/releases) 还提供预构建归档包。从 GitHub 安装不要求先发布到 npm。

### 通过内置 Discover 标签页安装

1. 在 **Plugins → Experimental plugins → More** 中启用 **Custom plugin markets**。较新的 Harness 版本将该组件称为 **Custom plugin indexes**。
2. 打开 **Discover**，添加以下索引源：

   ```text
   https://raw.githubusercontent.com/Sad-Jack/deepseek-harness-russian/main/plugin-index.json
   ```

3. 打开语言包卡片，核对安装来源，然后点击 **Install**。
4. 启用包，并在常规设置中选择 **Русский**。

这是作者维护的索引，不是 DeepSeek 官方目录。索引固定到不可变的 Git 提交，仅声明经过验证的 Harness 版本。社区目录的收录需要单独审核：[申请 #11494](https://github.com/awesome-dsh-plugin/awesome-dsh-plugin/pull/11494)。

### 从本地目录安装

下载并解压[仓库 ZIP](https://github.com/Sad-Jack/deepseek-harness-russian/archive/refs/heads/main.zip)，或克隆仓库：

```sh
git clone https://github.com/Sad-Jack/deepseek-harness-russian.git
```

选择一个固定目录，其根目录应包含 `package.json`、`client.js` 和 `cordis.patch.yml`。无需安装 Node.js、运行 `npm install` 或进行构建。

在 **Plugins → Add plugin → Package name or address** 中输入该目录的绝对路径，例如：

```text
/Users/your-name/Projects/deepseek-harness-russian
```

请替换为你电脑上的实际路径。安装并启用 **Russian · official translations**，然后在 **Settings → General → Language** 中选择 **Русский**。切换后，对应的俄语路径为 **Меню аккаунта → Настройки → Общие → Язык → Русский**。

**本地安装后，请保留原目录。** Harness 会直接链接该目录。如需移动，请先通过应用移除包，再移动目录并重新安装。

### 如果一直停留在 Checking…

在经过验证的 Mac 上，首次检查本地目录时曾出现停滞。关闭安装对话框、正常重启 Harness 后重试，问题得到解决。对话框停滞不代表安装成功；请检查已安装列表和启用开关。

## 翻译覆盖范围与适配

64 个词典覆盖了从**已安装构建中直接提取的全部 2,909 个英文键**，而不是假定其公开源码标签包含完全相同的键。覆盖聊天、设置、侧边栏、模型、权限、计划、自动化、工具、子代理和插件管理等客户端界面。

大部分文本直接来自官方 `dsh-v0.2.2-alpha.2` 翻译。已记录的差异包括：

- **16 项兼容性适配**：保留模型标识 `1017`，补充新版中已移除的旧键，并使功能说明符合 0.2.1-rc.5 的行为。
- **15 项术语修正**：修正两处将 Shell 直译为“贝壳”的错误，以及 13 处将运行状态译成“跑步”的错误，改用符合上下文的俄语命令解释器和执行状态术语。

`{count}`、`{path}` 等具名占位符保持不变。缺少的键使用 Harness 正常的英语回退。精确的源码提交见 [provenance.json](provenance.json)；所有改动见 [translations/compatibility.json](translations/compatibility.json)。

## 不会翻译的内容

- **macOS 原生菜单**及独立的登录、更新窗口：该版本由桌面外壳维护它们自己的词典。
- 从应用自身元数据读取的部分实验插件名称和描述。
- 模型回复、终端输出、代码、文件名及用户编写的内容。

本包不修改应用布局。较长的俄语标签可能在窄控件中被截短。本包不增加代理工具、安装脚本、运行时依赖或翻译服务请求；它通过 `ctx.locale` 注册词典。

## 验证与要求

全部 2,909 个键均使用已安装 0.2.1-rc.5 的本地化运行时检查：键覆盖、占位符及参数替换、英语回退、语言偏好持久化、清理、重新启用、注册失败后的回滚，以及保留已存在的俄语语言项。

已在应用中检查主界面、侧边栏、常规设置、自动化页面、插件列表和包详情。完整退出并重启后仍保留俄语。这不代表已经手动遍历所有可能的界面或错误状态。

详见 [verification.json](verification.json)、[UI-VERIFICATION.md](UI-VERIFICATION.md) 以及注明检查日期的[要求检查记录](REQUIREMENTS.md)。满足技术条件或检查通过，并不保证社区目录审核通过或合并。

## 包内文件

| 文件 | 用途 |
| --- | --- |
| `client.js` | 可直接安装的客户端模块，内嵌词典 |
| `index.js` | 最小宿主模块，不添加工具或服务 |
| `cordis.patch.yml` | 在 Harness 组合中注册包 |
| `package.json` | 包清单、导出、打包文件及兼容性 |
| [translations/ru.json](translations/ru.json) | 完整俄语词典 |
| [translations/target-en.json](translations/target-en.json) | 从已验证安装构建中提取的英文键 |
| [translations/compatibility.json](translations/compatibility.json) | 相对于官方翻译的已记录差异 |
| `locale/*.json`、`icon.svg` | 包自身的多语言元数据和原创图标 |
| [provenance.json](provenance.json) | 源码版本、提交和文件路径 |
| [CHANGELOG.md](CHANGELOG.md) | 包的发布历史 |

`client.js` 已经构建完成。只修改 `translations/ru.json` **不会**自动更新嵌入 `client.js` 的词典。

## 反馈

欢迎[提交 issue](https://github.com/Sad-Jack/deepseek-harness-russian/issues)，请注明 Harness 版本、操作系统、受影响的界面及预期翻译。发布截图前请移除个人信息。

## 停用或卸载

先在 **Settings → General → Language** 选择其他语言，再在 **Plugins** 中停用或移除包。停用会释放本包的词典和语言定义。通过应用移除包之前，请保留本地目录。

升级到内置俄语的 Harness 版本后，请停用本包并使用内置语言。

## 许可证

官方翻译采用 **MIT**，Copyright (c) 2026 DeepSeek。原始版权声明保留在 [LICENSE](LICENSE) 中。本地打包代码和原创图标也以 MIT 提供。本仓库不是 DeepSeek 官方项目。
