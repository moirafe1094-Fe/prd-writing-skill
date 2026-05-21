# Page Description Layout Rules

## Image Source Order

During PRD work there may be three image layers:

1. First-pass image2/imagegen visual prototype from the clarified description.
2. Interactive HTML demo screenshots used to validate behavior.
3. Final redrawn PRD images used for polished documentation.

Use the HTML demo as the source of truth for interactions. Use final redrawn images for PRD presentation only when they preserve the HTML demo's fields, states, and flow. Keep a simple mapping in working notes or artifact manifests: `requirement -> first-pass image -> HTML screen -> final PRD image`.

## HTML Prototype Attachment

When an HTML prototype exists, include the HTML file in the Feishu PRD functional requirements section, near the section introduction and before the screenshot/requirement pairs. Prefer a standalone single-file HTML attachment when the prototype depends on separate CSS, JavaScript, or local assets; otherwise attach the original HTML file.

For Feishu writeback, use `docs +media-insert --type file` to upload the HTML file. If the command appends the file to the document end, move the attachment block into the functional requirements section so reviewers can find it before reading the detailed requirements.

## One-To-One Requirement Layout

When an HTML prototype or verified interactive demo exists, the requirement description section must be written as paired units:

1. Place the exact HTML screenshot for one requirement or state.
2. Immediately below or beside it, write the requirement description for that same screenshot only.
3. Repeat the pair for the next requirement or state.

Do not group all screenshots together and describe them later. Do not describe several unrelated screenshots in one generic table. Each screenshot should have a caption that includes the requirement number or state name, and the text next to it should cover only the fields, actions, validation, exceptions, dependencies, and tracking events visible or implied by that screenshot.

## App Or Mini-Program

Use two columns:

- Left: prototype screenshot.
- Right: requirement details.

Recommended structure:

```xml
<grid>
  <column width-ratio="0.42">
    <img src="IMAGE_TOKEN" width="260" caption="页面截图" name="screen.png"/>
  </column>
  <column width-ratio="0.58">
    <p><b>页面目标：</b>...</p>
    <ul>
      <li>入口条件：...</li>
      <li>展示字段：...</li>
      <li>用户操作：...</li>
      <li>校验规则：...</li>
      <li>异常状态：...</li>
      <li>埋点：...</li>
    </ul>
  </column>
</grid>
```

Use multiple screenshots in the left column when a single requirement section describes a short continuous mobile flow.

If screenshots were redrawn with image2/imagegen, use the redrawn images in the visible PRD layout and keep the original screenshot mapping in working notes or artifact manifests. Captions may say “原型重绘图” when the image is not a direct screenshot.

## PC Page

Use vertical layout:

1. Screenshot first.
2. Requirement details below.

Recommended structure:

```xml
<img src="IMAGE_TOKEN" width="900" caption="PC页面截图" name="pc-screen.png"/>
<p><b>页面目标：</b>...</p>
<table>
  <thead>
    <tr><th>模块</th><th>需求说明</th><th>规则/异常</th></tr>
  </thead>
  <tbody>
    <tr><td>筛选区</td><td>...</td><td>...</td></tr>
    <tr><td>列表区</td><td>...</td><td>...</td></tr>
  </tbody>
</table>
```

PC pages usually need module-level breakdown because one screen may contain navigation, filters, table, drawer, modal, and batch actions.

If a PC prototype is redrawn, keep the same viewport, module order, labels, table columns, filters, and primary/secondary actions as the original. Do not beautify by removing dense operational information.

## Description Quality Bar

Every page/module should answer:

- Who sees it.
- How they enter.
- What they need to decide or do.
- What fields are displayed and where the data comes from.
- What actions are allowed.
- What happens after each action.
- What can go wrong.
- What should be tracked.
