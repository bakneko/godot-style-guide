# Godot Style Guide

[English](./README.md) | **简体中文**

## 1 摘要

对于涉及多人团队协作的项目，Godot并没有一个完全适合的项目文件规范。本指南旨在提供组织Godot项目的建议，来简化多人协作流程。

## 2 文件命名规范

所有资产都应该有一个基本资产名称。 基本资产名称表示相关资产的逻辑分组。 任何属于这个逻辑组的资产都应该遵循：

 **基本资产名称_后缀.资产类型对应的文件扩展名**

对于资产的独特和特定的变量，基本资产名称要么是一个简短和易于识别的名称，它表示资产的逻辑分组，这些资产是资产基本名称的子集。 例如，如果Bob有多个皮肤，这些皮肤仍然应该使用bob作为基本资产名称，但包括一个可识别的变体。 一个 Evil 皮肤将被称为 bob_evil 和 retro 皮肤将被称为bob_retro。

对于唯一的资产但通用的变量，基本资产名称是从01开始的两位数。 例如，如果你有一个环境艺术家产生不寻常的岩石，他们将被命名为 rock_01，rock_02，rock_03 等。 除了罕见的例外，你不应该要求一个三位数的变体号码。 如果您有100多个资产，您应该考虑使用不同的基本名称或使用多个变体名称来组织它们。

wuling_01.gltf,   wuling_01_albedo.png,    wuling_01_normal.png

### 2.1 示例

#### 2.1.1 Bob

<table style="margin-bottom: 10px">
    <tr>
        <th style="padding: 0 180px 0 0">资产类型</th>
        <th style="padding: 0 180px 0 0 ">示例命名</th>
    </tr>
    <tr>
        <td>Scene（场景）</td>
        <td>bob.tscn</td>
    </tr>
    <tr>
        <td>Skeletal Mesh (骨骼网格体)</td>
        <td>bob_skleton.gltf</td>
    </tr>
    <tr>
        <td>Material (材质)</td>
        <td>bob_material.tres</td>
    </tr>
    <tr>
        <td>Texture (基本色 Albedo)</td>
        <td>bob_albedo.png</td>
    </tr>
    <tr>
        <td>Texture (Evil Albedo)</td>
        <td>bob_albedo_evil.png</td>
    </tr>
</table>

#### 2.1.2 Rocks

<table style="margin-bottom: 10px">
    <tr>
        <th style="padding: 0 180px 0 0">资产类型</th>
        <th style="padding: 0 180px 0 0 ">示例命名</th>
    </tr>
    <tr>
        <td>Static Mesh 01 (静态网格体)</td>
        <td>rock_01.gltf</td>
    </tr>
    <tr>
        <td>Static Mesh 02 (静态网格体)</td>
        <td>rock_02.gltf</td>
    </tr>
    <tr>
        <td>Static Mesh 03 (静态网格体)</td>
        <td>rock_03.gltf</td>
    </tr>
    <tr>
        <td>Texture (基本色 Albedo)</td>
        <td>rock_01_albedo.png</td>
    </tr>
    <tr>
        <td>Material</td>
        <td>rock_01_material.tres</td>
    </tr>
    <tr>
        <td>Material (Snow)</td>
        <td>rock_01_material_snow.tres</td>
    </tr>
</table>

#### 2.1.3 Textures

<table style="margin-bottom: 10px">
    <tr>
        <th style="padding: 0 180px 0 0">资产类型</th>
        <th style="padding: 0 180px 0 0 ">示例命名</th>
    </tr>
    <tr>
        <td>Texture (Albedo)</td>
        <td>tank_01_albedo.png</td>
    </tr>
    <tr>
        <td>Texture (Normal)</td>
        <td>tank_01_normal.png</td>
    </tr>
    <tr>
        <td>Texture (Roughness)</td>
        <td>tank_01_rough.png</td>
    </tr>
    <tr>
        <td>Texture (Alpha/Opacity)</td>
        <td>tank_01_alpha.png</td>
    </tr>
    <tr>
        <td>Texture (Ambient Occlusion)</td>
        <td>tank_01_ao.png</td>
    </tr>
    <tr>
        <td>Texture (Emissive)</td>
        <td>tank_01_emissive.png</td>
    </tr>
    <tr>
        <td>Texture (Specular)</td>
        <td>tank_01_specular.png</td>
    </tr>
    <tr>
        <td>Texture (Metallic)</td>
        <td>tank_01_metallic.png</td>
    </tr>
        <tr>
        <td>Texture (ORM)</td>
        <td>tank_01_orm.png</td>
    </tr>
</table>

## 3 内容目录结构

### 3.1 示例结构

与资产名称同样重要的是，项目的目录结构样式应该被视为规则。 资产命名约定和内容目录结构是并行不悖的，两者的违反都会造成不必要的混乱。

有多种方法来布局Godot项目的内容。 在这种风格中，我们将使用一个结构，它更多地依赖于 File System 的过滤和搜索能力来帮助那些使用资产的人找到特定类型的资产，而不是另一个将资产类型与文件夹分组的通用结构。

``` plain-text
|-- res://
    |
    |-- addons
    |   |-- terrain_3d
    |   |-- ...
    |-- waveshooter
    |   |-- meshes
    |   |   |-- industrial
    |   |   |   |-- props
    |   |   |   |   |-- standlight_01.gltf
    |   |   |   |   |-- standlight_01_albedo.png
    |   |   |   |   |-- ...
    |   |   |   |-- buildings
    |   |   |       |-- ...
    |   |   |-- nature
    |   |       |-- props
    |   |       |-- foliage
    |   |       |-- rocks
    |   |       |-- trees
    |   |-- characters
    |   |   |-- bob
    |   |   |-- common
    |   |       |-- animations
    |   |       |-- audio
    |   |-- effects
    |   |   |-- fire
    |   |   |-- weather
    |   |   |-- electrical
    |   |       |-- spark_01
    |   |           |-- spark_01_halo.png
    |   |           |-- spark_01.tscn
    |   |           |-- ...
    |   |-- maps
    |       |-- gameplay.tscn
    |-- core
    |   |-- fonts
    |   |-- images
    |   |-- singletons
    |   |-- ui
    |       |-- menu
    |       |-- pause
    |-- sandbox
```

这种结构的原因列于以下各小节。

### 3.2 文件夹名称

这些是命名内容结构中任何文件夹的常用规则：

#### 3.2.1 总是使用snake_case

snake_case 是指用小写字母开始一个名字，然后不使用空格而使用下划线，下面的每个单词也以小写字母开始。 例如，desert_eagle，rocket_pistol 和 a_series_of_words。

#### 3.2.2 不使用空格

作为3.2.2的补充：**绝不使用空格**。空格会导致各种工程工具和批处理过程出错。理想情况下，项目的根也不包含空格，并且位于这样的位置 D:\GodotProjects\ ，**而不是** C:\Users\My Name\My Documents\Godot Projects\。

#### 3.2.3 永远不要使用Unicode字符和其他符号

如果您的游戏角色之一名为“Zoe”，其文件夹名称应该是 zoe。 对于工程工具，Unicode字符可能比Spaces更糟糕，Godot的某些部分也可能不支持路径中的Unicode字符。

与此相关，如果您的项目有无法解释的问题，并且您的计算机的用户名具有 Unicode 字符(即。 您的名字是 Zoe )，位于您的“Documents”文件夹中的任何项目都将受到此问题的影响。 通常简单地将您的项目移动到 D:\Project 将解决这些问题。

使用 a-z 和 0-9 以外的其他字符，如@、-、、*和#，也会导致意外和难以跟踪其他平台、源控制和较弱的工程工具上的问题。

### 3.3 项目资产使用顶层文件夹

项目的所有资产都应该存在于以项目命名的文件夹中。 例如，如果您的项目名为“shooter”，那么它的所有内容都应该存在于 res://shooter/ 中。

这种做法有多种原因：

#### 3.3.1 DLC、子项目和补丁易于维护

如果您的项目计划发布DLC，或者有多个与它相关的子项目，这些子项目可能被迁移出去，或者根本不在构建中煮熟，那么与这些项目相关的资产应该有自己单独的顶层内容文件夹。 这使得烹饪DLC与主要项目内容分离得更容易。 子项目也可以在最少的努力下进行进出迁移。 如果您需要更改资产的材料或在补丁中添加一些非常特定的资产覆盖行为，您可以很容易地将这些更改放在补丁文件夹中，并安全地工作，而不会破坏核心项目。

**示例:** res://dlc_01/

### 3.4 使用一个名为 sandbox 的文件夹进行本地测试

在项目开发过程中，团队成员有一种“sandbox”是非常常见的，他们可以在不冒核心项目风险的情况下自由地进行实验。 由于这项工作可能正在进行中，这些团队成员可能希望将他们的资产放在项目的源代码管理服务器上。 并不是所有的团队都需要使用 sandbox 文件夹，但是使用它们的团队经常会遇到提交给源代码管理的资产的常见问题。您应该将sandbox文件夹添加到版本控制系统中的忽略列表中，例如：

``` plain-text
    # .gitignore file

    # Sandbox folder
    [Ss]andbox/
```

团队成员很容易意外地使用尚未准备使用的资产，一旦这些资产被移除，这将导致问题。 例如，艺术家可能正在制作一组模块化的静态网格，并仍在努力使其大小和网格抓取正确。 如果一个世界建设者在主项目文件夹中看到这些资产，他们可能会在一个层次上使用它们，而不知道它们可能会受到难以置信的更改和/或删除。 这导致团队中的每个人都需要解决大量的重新工作。

如果这些模块化资产被放置在sandbox文件夹中，世界建设者就不应该有理由使用它们，整个问题就永远不会发生。

一旦资产准备好使用，艺术家只需将资产移动到项目特定文件夹并修复重定向器。 这基本上是“促进”资产从实验到生产。

**示例:** res://sandbox/

### 3.5 使用一个名为 maps 的文件夹存放所有地图文件

地图场景文件非常特殊，每个项目都有自己的地图命名系统是很常见的，特别是当它们与子级或流级一起工作时。 无论为特定项目建立了什么地图组织系统，所有级别都应该属于 res://project_name/maps。

能够告诉某人打开一个特定的地图，而不必解释它在哪里是一个伟大的节省时间和一般的“生活质量”的改进。 层次通常位于地图的子文件夹中，例如 maps/campaign1/ 或 maps/arenas ，但这里最重要的是它们都存在于 res://project_name/maps/ 中。

这也简化了工程师的工作。 如果必须为构建过程挖掘任意的文件夹，那么构建过程的摇摆级别可能非常令人沮丧。 如果一个团队的地图都在一个地方，那么不在构建中意外地绘制地图就会困难得多。 它还简化了QA过程。

**示例:** res://project_name/maps/

### 3.6 使用一个名为 core 的文件夹存放关键 GDScripts 和其他资产

使用一个单独的文件夹处理对项目工作绝对重要的资产。 例如，基本Singleton、UI/HUD, Audio Bus Layout, Event System, Splash Images 应该住在这里。

对于UI，一般情况下，core文件夹只存储主菜单，设置菜单等UI，游戏中的HUD应该存放在游戏项目文件夹下。需要确保对于游戏的更新尽量不修改core中的文件（大版本或DLC更新除外）。

这为其他团队成员创建了一个非常清晰的“不要动这些”信息。 非工程师应该没有什么理由进入 core 文件夹。 遵循良好的代码结构风格，设计师应该在公开功能的子类中进行游戏调整。 世界建筑者应该在指定的maps文件夹中使用Scenes，而不是潜在地滥用基类。

**示例:** res://core/

## 4 参考文献

[Godot文档 - 项目组织](https://docs.godotengine.org/zh_CN/stable/tutorials/best_practices/project_organization.html)

[ue4-style-guide](https://github.com/Allar/ue4-style-guide)
