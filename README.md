
插件特性

---
- 移动到新集合：给选中对象生成集合，并使用该对象的名字命名集合。
- 移动到原点：将选中对象移动到原点。
- 材质重命名：用选中模型的名字为材质插槽中的材质球命名。
- 替换材质：将选中模型的材质球插槽替换为空材质插槽。
- 删除空插槽：删除没有材质球的材质插槽。

插件下载

---
立即下载获取该应用程序。
如果您想在新功能发布稳定版本之前尝试它们，可以在此处下载预览版本。

安装方法

---
1. 下载插件压缩包。
2. 在 Blender 菜单中打开 "编辑>>偏好设置" 选项卡。
3. 选择 "插件" 选项卡。
4. 点击 "安装" 按钮，选择下载的插件压缩包文件。
5. 启用插件。

联系我

---
- 作者：VINCE
- 哔哩哔哩：https://space.bilibili.com/250546761?spm_id_from=333.1007.0.0
- 个人网页：vinceofx.com

其他信息

---
- 开源许可：MIT License
- 版权说明：版权所有 (c) 2024 VINCE. 保留所有权利。
欢迎在 GitHub 上提交问题或建议。

-----------------------------------------------------------------------------------------------------------------------------------------

blender_plugin_name/
│
├── __init__.py               # 插件的入口点和注册信息
├── operators.py              # 自定义操作（Operators）
├── panels.py                 # 界面面板（Panels）
├── properties.py             # 属性（Properties）定义数据结构
│
├── utils/
│   ├── __init__.py           # 将 utils 目录作为模块
│   ├── common_utils.py       # 通用工具函数
│   └── specific_utils.py     # 特定工具函数
│
├── presets/
│   ├── __init__.py           # 将 presets 目录作为模块
│   └── some_preset.py        # 预设操作或配置
│
├── external_tools/
│   ├── __init__.py           # 将 external_tools 目录作为模块
│   └── some_external_tool.py # 外部工具接口等
│
├── icons/
│   └── some_icon.png         # 图标资源
│
├── tests/
│   ├── __init__.py           # 将 tests 目录作为模块
│   ├── test_operators.py     # 测试 operators
│   └── test_panels.py        # 测试 panels
│
└── README.md                 # 项目说明文件
```

这个结构包含的主要文件和目录含义是：

- `__init__.py`：这是每个 Blender 插件必需的文件，它定义插件的元数据、依赖、注册、注销函数等。
- `operators.py`：定义插件操作的文件。操作是在用户界面触发的功能动作，例如按钮点击。
- `panels.py`：定义插件面板的文件。面板是插件在 Blender 界面中的显示区域，用于放置工具和属性。
- `properties.py`：定义插件中使用的属性（如场景属性、对象属性）的文件。
- `utils/`：为了实现代码重用和更好的组织，将通用的或特定类型的函数库放在这个子目录下。
- `presets/`：插件的预设配置可以存放在此目录下，便于快速配置插件到特定状态。
- `external_tools/`：如果插件依赖于或与外部工具交互，这部分代码可以置于此目录。
- `icons/`：如果你的插件使用了自定义图标，可以将这些资源放在这个目录下。
- `tests/`：单元测试和其他测试代码放在这个目录下，用于确保代码质量和升级时的稳定性。
- `README.md`：项目说明文档，介绍插件功能、用法、安装说明等。

在 `__init__.py` 文件内部，每个插件都需要有一个唯一的 `bl_info` 字典定义插件信息，如下例所示：

```python
bl_info = {
    "name": "My Blender Add-on",
    "blender": (2, 80, 0),
    "category": "Object",
    # 其他的插件元数据
}
```

并且，`__init__.py` 还需要包含注册和注销插件内部所有可用类的逻辑。例如：

```python
from . import operators, panels, properties

def register():
    properties.register()
    operators.register()
    panels.register()

def unregister():
    properties.unregister()
    operators.unregister()
    panels.unregister()
``` 

每个子模块（如 `operators`, `panels`）也会具有自己的 `register()` 和 `unregister()` 函数，负责注册和注销该模块内部的类。

整个结构的目的是为了保持代码的模块化和组织性，让插件的管理和扩展都变得简单高效。
