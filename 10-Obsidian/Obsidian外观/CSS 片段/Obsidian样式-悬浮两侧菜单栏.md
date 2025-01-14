---
uid: 20231029201842
title: Obsidian 样式 - 悬浮两侧菜单栏
tags: [CSS美化, 内置图片]
description: 悬浮侧边栏样式，取消了悬浮展开，单纯的以单击键展开，添加透明度，这样笔记内容不会随着侧边栏的展开而移动
author: 熊猫别熬夜
type: other
draft: false
editable: false
modified: 20231108172024
---

# Obsidian 样式 - 悬浮两侧菜单栏

灵感来源于 [[Obsidian样式-实现TiddlyWiki故事河]] 的悬浮侧边栏样式，取消了悬浮展开，单纯的以单击键展开，添加透明度，这样笔记内容不会随着侧边栏的展开而移动，同时配合 [[Obsidian样式-缩减栏宽模式下美化笔记内部背景]]，来进一步美化空白区。

> [!tip]+ 效果展示
> ![Obsidian 样式 - 悬浮两侧菜单栏](https://cdn.pkmer.cn/images/Pasted%20image%2020231027132828.png!pkmer)

> [!tip]+ Style Setting 中相关设置介绍
> ![Obsidian 样式 - 悬浮两侧菜单栏](https://cdn.pkmer.cn/images/Pasted%20image%2020231028181354.png!pkmer)

## Obsidian 的 CSS Snippets

```css
/* @settings
name: 悬浮两侧菜单栏
id: Floating-side-menu-bar
settings:

	-
		id: right-tab-float-choice
		title: 右侧侧边栏悬浮开关
		type: class-toggle
		default: true
	-
		id: left-tab-float-choice
		title: 左侧侧边栏悬浮开关
		type: class-toggle
		default: true
	-
		id: tab-top-height
		title: 菜单栏距离顶部高度
		type: variable-text
		default: 80px
	-
		id: tab-right-length
		title: 调整左侧菜单距离
		type: variable-text
		default: 44px
	-
		id: tab-opacity
		title: 菜单栏透明度
		type: variable-number-slider
		default: 0.85
		format: 
		min: 0.2
		max: 1
		step: 0.01
	-
		id: hide-tab-header-container
		title: 隐藏关闭、最小化按钮、固定侧边栏按钮
		type: class-toggle
		default: true
*/

body {
  --tab-top-height: 80px;
  --tab-right-length: 44px;
  --tab-opacity: 0.85;
}

.left-tab-float-choice .workspace-split.mod-horizontal.mod-left-split {
  position: fixed;
  display: flex;
  width: 280px;
  top: var(--tab-top-height);
  height: calc(100% - var(--tab-top-height) - 25px);
  z-index: var(--layer-popover);
  margin: 0;
  align-self: center;
  transform: translateX(var(--tab-right-length));
  /* box-shadow: 0 0 10px; */
  border: 1px solid var(--background-modifier-border);
  opacity: var(--tab-opacity);
}

.right-tab-float-choice .workspace-split.mod-horizontal.mod-right-split {
  position: fixed;
  display: flex;
  top: var(--tab-top-height);
  right: 0px;
  height: calc(100% - var(--tab-top-height) - 25px);
  z-index: var(--layer-popover);
  margin: 0;
  border: 1px solid var(--background-modifier-border);
  opacity: var(--tab-opacity);
}

.hide-tab-header-container .workspace-tab-header-tab-list {
  position: absolute;
  right: 50px;
}

.hide-tab-header-container .sidebar-toggle-button {
  position: absolute !important;
  right: 20px;
}


/* 不显示最大最小化后，使那块区域可以双击及拖动 */
.hide-tab-header-container.mod-windows .titlebar-button,
.is-hidden-frameless:not(.is-fullscreen)
  .workspace-tabs.mod-top-right-space
  .hide-tab-header-container.workspace-tab-header-container:after {
  display: none;
}
```
