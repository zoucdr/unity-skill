---
name: unity3d-skill
description: Unified Unity MCP skill for editor control, scene hierarchy, asset management, code execution, UI layout, Figma integration, gameplay, HTTP, and more.
---

# Unity3D MCP Skill

Invoke with `func: "<function_name>"`. Pass parameters in `args`.

**Response:** Success `{ "success": true, "data": ... }` / Failure `{ "success": false, "message": "...", "error": "..." }`.

Detailed schemas for each function are in `references/<func_name>.json`.

## Function Overview

### Editor & Preferences

| func | Description | Key Param |
|------|-------------|-----------|
| `base_editor` | Manage Unity editor state and control | action: get_state, get_windows, get_selection, execute_menu, get_menu_items |
| `console_read` | Read or clear Unity Editor console logs | action: get, get_full, clear |
| `console_write` | Write log messages to Unity editor console | action: log, warning, error, assert, exception |
| `prefers` | Manage EditorPrefs and PlayerPrefs | action: get, set, delete, list, clear |

### Code Execution

| func | Description | Key Param |
|------|-------------|-----------|
| `code_runner` | Execute C# code at runtime in Unity | action: run, compile, eval |
| `python_runner` | Execute Python scripts in Unity environment | action: run, execute_file, eval |
| `cmd_tool` | Execute system CMD commands | cmd (string) |
| `async_call` | Asynchronous function call support | type: in, out |
| `batch_call` | Batch execution of multiple function calls | args (array of {func, args}) |

### Scene & Hierarchy

| func | Description | Key Param |
|------|-------------|-----------|
| `edit_scene` | Manage scene assets | action: load, save, create, get_hierarchy |
| `hierarchy_create` | Create game objects in scene hierarchy | source: primitive, prefab, copy, menu, empty |
| `hierarchy_search` | Search and find game objects in hierarchy | search_type: by_name, by_id, by_tag, by_layer, by_component, by_query |
| `hierarchy_apply` | Handle prefab apply and connection operations | action: apply |
| `object_delete` | Delete game objects or assets | path (string) |

### GameObject & Component Editing

| func | Description | Key Param |
|------|-------------|-----------|
| `edit_gameobject` | Edit GameObject properties | action: set_property, get_property, add_component, remove_component, set_transform |
| `edit_component` | Edit component properties on GameObjects | action: set_property, get_property, list_components |
| `edit_material` | Edit material properties | action: set_property, get_property, set_shader, set_color, set_texture |
| `edit_texture` | Edit texture properties | action: set_import_settings, get_info, set_wrap_mode, set_filter_mode |
| `edit_anim_clip` | Manage animation clips | action: create, modify, duplicate, delete, get_info, search, set_curve, set_events |

### Project & Asset Management

| func | Description | Key Param |
|------|-------------|-----------|
| `project_create` | Create assets in project window | source: menu, empty, template, copy |
| `project_operate` | Manage Unity assets | action: import, modify, move, duplicate, rename, get_info, create_folder, reload, select, ping, select_depends, select_usage, tree |
| `project_search` | Search assets in project window | query (string) |
| `asset_index` | Resource index management | action: add, remove, update, search, categories, locate, details, show, lost |
| `manage_package` | Manage Unity packages | action: install, remove, update, list, search |
| `source_location` | Locate resources in file explorer or Unity project | action: reveal, locate, find_references |

### UI & Layout

| func | Description | Key Param |
|------|-------------|-----------|
| `ugui_layout` | UGUI layout tools | action: set_anchor, set_pivot, set_size, apply_layout, set_anchored_position |
| `ui_rule_manage` | Manage UI creation schemes and modification records | action: record_modify, record_renames, get_renames, record_download_sprites, get_download_sprites |
| `figma_manage` | Manage Figma documents | action: fetch_document, download_images, preview, get_conversion_rules |
| `figma_data_simplifier` | Simplify Figma data for Unity UI conversion | action: simplify, export, preview |

### Gameplay & Networking

| func | Description | Key Param |
|------|-------------|-----------|
| `gameplay` | Control gameplay, simulate input, process images | action: play, pause, stop, screenshot, simulate_click, simulate_drag, set_size, get_info, compress_image |
| `request_http` | Send HTTP requests and download/upload files | action: get, post, put, delete, download, upload, ping, batch_download |
| `webpage_manage` | Manage web pages | action: add, remove, update, search, categories, open, details |

## References

See `references/` directory for JSON Schema definitions:

| File | func | Description |
|------|------|-------------|
| `references/base_editor.json` | base_editor | Manage Unity editor state and control |
| `references/console_read.json` | console_read | Read or clear Unity Editor console logs |
| `references/console_write.json` | console_write | Write log messages to Unity editor console |
| `references/prefers.json` | prefers | Manage EditorPrefs and PlayerPrefs |
| `references/code_runner.json` | code_runner | Execute C# code at runtime in Unity |
| `references/python_runner.json` | python_runner | Execute Python scripts in Unity environment |
| `references/cmd_tool.json` | cmd_tool | Execute system CMD commands |
| `references/async_call.json` | async_call | Asynchronous function call support |
| `references/batch_call.json` | batch_call | Batch execution of multiple function calls |
| `references/edit_scene.json` | edit_scene | Manage scene assets |
| `references/hierarchy_create.json` | hierarchy_create | Create game objects in scene hierarchy |
| `references/hierarchy_search.json` | hierarchy_search | Search and find game objects in hierarchy |
| `references/hierarchy_apply.json` | hierarchy_apply | Handle prefab apply and connection operations |
| `references/object_delete.json` | object_delete | Delete game objects or assets |
| `references/edit_gameobject.json` | edit_gameobject | Edit GameObject properties |
| `references/edit_component.json` | edit_component | Edit component properties on GameObjects |
| `references/edit_material.json` | edit_material | Edit material properties |
| `references/edit_texture.json` | edit_texture | Edit texture properties |
| `references/edit_anim_clip.json` | edit_anim_clip | Manage animation clips |
| `references/project_create.json` | project_create | Create assets in project window |
| `references/project_operate.json` | project_operate | Manage Unity assets |
| `references/project_search.json` | project_search | Search assets in project window |
| `references/asset_index.json` | asset_index | Resource index management |
| `references/manage_package.json` | manage_package | Manage Unity packages |
| `references/source_location.json` | source_location | Locate resources in file explorer or Unity project |
| `references/ugui_layout.json` | ugui_layout | UGUI layout tools |
| `references/ui_rule_manage.json` | ui_rule_manage | Manage UI creation schemes and modification records |
| `references/figma_manage.json` | figma_manage | Manage Figma documents |
| `references/figma_data_simplifier.json` | figma_data_simplifier | Simplify Figma data for Unity UI conversion |
| `references/gameplay.json` | gameplay | Control gameplay, simulate input, process images |
| `references/request_http.json` | request_http | Send HTTP requests and download/upload files |
| `references/webpage_manage.json` | webpage_manage | Manage web pages |
