# Godot Style Guide

**English** | [简体中文](./README.zh.md)

## 1 Summary

For projects involving multiple team collaborations, Godot does not have a complete project file specification. This guide aims to provide recommendations for organizing Godot projects to streamline multi-person collaboration processes.

## 2 File Naming

All assets should have a base asset name, indicating the logical grouping of related assets. Any asset belonging to this logical group should follow:

 **base_asset_name_suffix.type_extension**

For unique and specific variants of assets, the base asset name should either be a short and easily recognizable name that represents the logical grouping of the assets, or a subset of the base asset name. For example, if Bob has multiple skins, these skins should still use bob as the base asset name but include a recognizable variant. An Evil skin would be called bob_evil and a retro skin would be called bob_retro.

For unique assets with common variables, the base asset name should start with 01 and be two digits long. For example, if an environment artist produces unusual rocks, they would be named rock_01, rock_02, rock_03, etc. You should not require a three-digit variant number except for rare exceptions. If you have more than 100 assets, you should consider using different base names or multiple variant names to organize them.

wuling_01.gltf,   wuling_01_albedo.png,    wuling_01_normal.png

### 2.1 Examples

#### 2.1.1 Bob

<table style="margin-bottom: 10px">
    <tr>
        <th style="padding: 0 180px 0 0">Type</th>
        <th style="padding: 0 180px 0 0 ">Name</th>
    </tr>
    <tr>
        <td>Scene</td>
        <td>bob.tscn</td>
    </tr>
    <tr>
        <td>Skeletal Mesh</td>
        <td>bob_skleton.gltf</td>
    </tr>
    <tr>
        <td>Material</td>
        <td>bob_material.tres</td>
    </tr>
    <tr>
        <td>Texture</td>
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
        <th style="padding: 0 180px 0 0">Type</th>
        <th style="padding: 0 180px 0 0 ">Name</th>
    </tr>
    <tr>
        <td>Static Mesh 01 (Static Mesh)</td>
        <td>rock_01.gltf</td>
    </tr>
    <tr>
        <td>Static Mesh 02 (Static Mesh)</td>
        <td>rock_02.gltf</td>
    </tr>
    <tr>
        <td>Static Mesh 03 (Static Mesh)</td>
        <td>rock_03.gltf</td>
    </tr>
    <tr>
        <td>Texture</td>
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
        <th style="padding: 0 180px 0 0">Type</th>
        <th style="padding: 0 180px 0 0 ">Name</th>
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

## 3 Directory

### 3.1 Example Structure

The project directory structure style should be treated as a rule, just as important as asset naming conventions. There are multiple ways to layout Godot project content.

This guide recommends a structure that relies more on the file system’s filtering and search capabilities to help users find specific types of assets, rather than a common structure that groups asset types by folder.

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

The reasons for this structure are listed in the following sections:

### 3.2 Folder names

These are the common rules for naming any folders in the content structure：

#### 3.2.1 Always use snake_case

snake_case means starting a name with a lowercase letter, then using underscores instead of spaces, with each subsequent word also starting with a lowercase letter. For example, desert_eagle, rocket_pistol, and a_series_of_words.

#### 3.2.2 Never Use Spaces

As a supplement to 3.2.2: **never use spaces**. Spaces can cause various engineering tools and batch processing to error. Ideally, the root of your project also does not contain spaces and is located in such a position as D:\GodotProjects, **NOT** C:\Users\My Name\My Documents\Godot Projects.

#### 3.2.3 Never Use Unicode Characters and Other Symbols

If one of your game characters is named “Zoe”, its folder name should be zoe. For engineering tools, Unicode characters can be worse than spaces, and some parts of Godot may not support Unicode characters in paths.

Related to this, if your project has inexplicable issues and your computer’s username has Unicode characters (i.e., your name is Zoe), any projects in your “Documents” folder will be affected by this issue. Typically, simply moving your project to D:\Project will resolve these issues.

Using other characters beyond a-z and 0-9, such as @, -, *, and #, can also lead to unexpected and difficult-to-trace issues on other platforms, source control systems, and weaker engineering tools.

### 3.3 Use Top-Level Folders for Project Assets

All assets of the project should exist within a folder named after the project. For example, if your project is named “shooter”, then all of its content should exist within res://shooter/.

There are several reasons for this practice:

#### 3.3.1 DLC, Sub-Projects, and Patches Are Easy to Maintain

If your project plans to release DLC, or has multiple related sub-projects, which may be moved out or not cooked with the main project, then the assets related to these projects should have their own separate top-level content folders. This makes it easier to separate cooking DLC from the main project content. Sub-projects can also be migrated in and out with minimal effort. If you need to change the materials of assets or add some very specific asset override behaviors in patches, you can easily put these changes in a patch folder and work safely without breaking the core project.

**Example:** res://dlc_01/

### 3.4 Use a Folder Named "sandbox" for Local Testing

It is very common during project development for team members to have a “sandbox” where they can experiment freely without risking the core project. Since this work may be in progress, these team members may want to put their assets on the project’s source code management server. Not all teams need to use a sandbox folder, but teams that do often encounter common issues with assets being committed to source control. You should add the sandbox folder to the ignore list in your version control system, for example:

``` plain-text
    # .gitignore file

    # Sandbox folder
    [Ss]andbox/
```

Team members can easily accidentally use assets that are not yet ready for use, and once these assets are removed, it will cause issues. For example, an artist may be working on a set of modular static meshes and is still working to get their sizes and mesh grabbing correct. If a world builder sees these assets in the main project folder, they might use them on a level without knowing they may be subject to incredible changes and/or deletion. This leads to a lot of rework for everyone on the team. 

If these modular assets were placed in the sandbox folder, the world builder would have no reason to use them, and the whole issue would never occur.

Once the assets are ready for use, the artist simply moves the assets to the project-specific folder and fixes the redirectors. This is essentially “promoting” the assets from experimental to production.

**Example:** res://sandbox/

### 3.5 Use a Folder Named "maps" to Store All Map Files

Map scene files are very special, and it's common for each project to have its own map naming system, especially when they work with sub-levels or stream levels. Whatever map organization system is established for a specific project, all levels should belong to res://project_name/maps.

Being able to tell someone to open a specific map without having to explain where it is is a great time saver and a general QoL improvement. Levels are usually located in sub-folders of maps, such as maps/campaign1/ or maps/arenas, but the most important thing here is that they all exist within res://project_name/maps/.

This also simplifies the engineer's work. If you have to dig through arbitrary folders for the build process, the swinger level of the build process can be very frustrating. If a team's maps are all in one place, it is much more difficult to accidentally omit maps from the build. It also simplifies the QA process.


**Example:** res://project_name/maps/

### 3.6 Use a Folder Named "core" for Key GDScripts and Other Assets

Use a separate folder to handle assets that are absolutely critical to the project’s operation. For example, basic Singletons, UI/HUD, Audio Bus Layout, Event System, and Splash Images should reside here.

For UI, generally, the core folder should only store UIs such as the main menu, settings menu, etc., while the HUD within the game should be stored under the game project folder. It’s important to ensure that files within the core are not modified as much as possible during game updates (except for major version updates or DLC updates).

This creates a very clear “do not touch these” message for other team members. Non-engineers should have little reason to enter the core folder. Following good coding structure practices, designers should make game adjustments in subclasses that expose functionality. World builders should use Scenes in the specified maps folder, rather than potentially misusing base classes.

**Example:** res://core/

## 4 References

[Godot Documentation - Project Management](https://docs.godotengine.org/en/stable/tutorials/best_practices/project_organization.html)

[ue4-style-guide](https://github.com/Allar/ue4-style-guide)
