# Page Description Layout Rules

## Image Source Order

During PRD work there may be three image layers:

1. First-pass image2/imagegen visual prototype from the clarified description.
2. Interactive HTML demo screenshots used to validate behavior.
3. Final redrawn PRD images used for polished documentation.

Use the HTML demo as the source of truth for interactions. Use final redrawn images for PRD presentation only when they preserve the HTML demo's fields, states, and flow. Keep a simple mapping in working notes or artifact manifests: `requirement -> first-pass image -> HTML screen -> final PRD image`.

## Mixed PC And APP Prototype Attachments

For a mixed PC-and-APP requirement, create and upload two independent self-contained files. Place the PC HTML attachment in the left column and the APP HTML attachment in the right column of the same prototype attachment area. Do not combine the two terminals into one HTML, do not put APP screens inside the PC file, and do not put APP content above the PC attachment. Each column contains its own title, real attachment block, and at most one short description.

## App Or Mini-Program

Every APP page or major visible state in Requirement Description requires its own screenshot and uses a two-column block: screenshot on the left, matching page description on the right. The screenshot and description must share the same row/container so readers can compare them without scrolling between separate sections. An overview image or HTML attachment does not replace the page screenshot.

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

Every PC page or major visible state in Requirement Description requires its own screenshot and uses a vertical block: page heading, matching screenshot on top, and matching page description immediately below. Do not put the description beside the screenshot, and do not reuse a general overview image as evidence for a different page.

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

- Screenshot coverage equals page/state coverage: each requirement page has one directly associated screenshot.
- PC uses screenshot above description; APP uses screenshot left and description right.
- Missing screenshots, filename placeholders, or text such as “页面截图待补” fail final publication.

Every page/module should answer:

- Who sees it.
- How they enter.
- What they need to decide or do.
- What fields are displayed and where the data comes from.
- What actions are allowed.
- What happens after each action.
- What can go wrong.
- What should be tracked.
