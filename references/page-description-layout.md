# Page Description Layout Rules

## Choosing The Prototype Form

| Situation | Prototype form in 3.4（1） |
| --- | --- |
| An HTML prototype exists | HTML component block (`html5-block`). No file attachment card, no screenshots of that HTML. |
| No HTML, only current-page screenshots or design images | Images, per the screenshot fallback rules below. |

Use the HTML as the source of truth for interactions. Never place both an HTML component block and screenshots of the same HTML in the PRD.

## HTML Component Block (Default)

### Section structure

For each prototype group (one HTML file):

1. Bold title line naming the page and what can be switched, e.g. `<p><b>原型：造旺 Web 特陈额度分配（可切换角色、额度维度）</b></p>`.
2. The component block.
3. The page descriptions for every page or state shown in that HTML, in the same order as the HTML: page heading, 页面目标, module table (PC) or list (APP).

Descriptions always follow the block. Do not put them before the block, beside it in a grid, or in a separate section.

```xml
<p>以下按页面说明需求：每组先放可交互原型（HTML 组件块），原型下方为对应的需求说明。</p>

<p><b>原型：SFA Web 特陈额度配置详情（可切换新增、查看、编辑状态）</b></p>
<html5-block path="@./prototype/config-detail.html"/>
<h4>PC 页面 1：特陈额度配置详情（新增）</h4>
<p><b>页面目标：</b>...</p>
<table>
  <thead><tr><th>模块</th><th>需求说明</th><th>规则 / 异常</th></tr></thead>
  <tbody><tr><td>筛选区</td><td>...</td><td>...</td></tr></tbody>
</table>
<h4>PC 页面 2：特陈额度配置详情（编辑）</h4>
...

<p><b>原型：造旺 APP 陈列活动（可切换角色）</b></p>
<html5-block path="@./prototype/app-views.html"/>
<h4>APP 页面 1：陈列活动</h4>
<p><b>页面目标：</b>...</p>
<ul><li>入口条件：...</li><li>展示字段：...</li><li>用户操作：...</li><li>异常状态：...</li></ul>
```

### Mixed PC and APP

Keep PC and APP in separate self-contained HTML files. Each file is its own group (title → block → descriptions). PC groups come first, then APP groups. Do not combine terminals into one HTML, and do not put component blocks inside grid columns (they become too narrow).

### Embedding the HTML

Keep the prototype source file unchanged. Generate an embed copy for the doc:

- In `<head>` add:
  - `<meta name="use-iframe" content="true">`
  - `<meta name="html-box-height-mode" content="auto">` (use `viewport` only for single-screen tools that scroll internally)
  - `<meta name="description" content="...">` — one sentence on what the prototype shows; it becomes the block's alt text.
- The doc body is about 820 px wide (wide mode about 1020 px). PC prototypes designed wider must scale to fit.
- **Do not scale the root element.** Do not put CSS `zoom` or `transform` on `html` / `body`. Feishu measures the block height from the unscaled page, so the content shrinks and a blank strip is left below it.
- Scale an inner container and give the outer container the scaled height. After the DOM loads, move the body's children into an inner wrapper and put that inside an outer wrapper (`width: 100%; overflow: hidden`). Set the inner wrapper to the design width `W`, with `transform: scale(z)` and `transform-origin: 0 0`, where `z = min(1, outer.clientWidth / W)`. Set the outer wrapper's height to `ceil(inner.offsetHeight × z)`. Re-run on `resize`, and through a `ResizeObserver` on the inner wrapper, so the height follows when a state switch makes the content taller or shorter.

  ```html
  <script>(function(){var W=1440;
  function fit(){var o=document.getElementById("__fit"),i=document.getElementById("__fitIn");if(!i)return;
  var z=Math.min(1,o.clientWidth/W);i.style.width=(z<1?W+"px":"100%");i.style.transform=z<1?"scale("+z+")":"none";
  o.style.height=Math.ceil(i.offsetHeight*z)+"px";}
  document.addEventListener("DOMContentLoaded",function(){var b=document.body,o=document.createElement("div"),i=document.createElement("div");
  o.id="__fit";o.style.cssText="width:100%;overflow:hidden;position:relative";i.id="__fitIn";i.style.transformOrigin="0 0";
  while(b.firstChild)i.appendChild(b.firstChild);o.appendChild(i);b.appendChild(o);fit();
  if(window.ResizeObserver)new ResizeObserver(fit).observe(i);window.addEventListener("resize",fit);});})();</script>
  ```

- Because the body's children are moved into the wrapper, make sure the prototype's CSS and scripts don't depend on being direct children of `body` (for example `body > .x` selectors, or `document.body.firstElementChild`).
- Override styles that break under auto height or scaling: `100vh` / `min-height: 100vh` → `0`; `max-width: calc(100vw - …)` → `none`; fixed footers → `position: static`.
- Total HTML ≤ 500 KB. No inline Base64 images, fonts, or large mock data.
- Verify before writing:
  - Render the embed copy headless at 820 px width and check that nothing is cut off or squeezed.
  - Simulate auto height: load the page in an 820 px wide frame, set the frame height to the document's `scrollHeight`, and confirm there is no blank strip below the content.
  - Switch to the tallest and the shortest state, and confirm the height follows both ways.
- After writing, fetch the doc and confirm one `html5-block` per HTML file, in the intended order.

## Screenshot Fallback (No HTML)

Use only when no HTML prototype exists.

### App or mini-program

Every APP page or major visible state requires its own screenshot, in a two-column block: screenshot left, matching description right.

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

Use multiple screenshots in the left column when one section describes a short continuous mobile flow. If screenshots were redrawn with image2/imagegen, captions may say「原型重绘图」.

### PC page

Every PC page or major visible state requires its own screenshot, in a vertical block: page heading, screenshot, then the description immediately below.

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

If a PC prototype is redrawn, keep the same viewport, module order, labels, table columns, filters, and primary/secondary actions as the original.

## Description Quality Bar

- With HTML: every page or state in the HTML has a description unit after its component block; no screenshots of that HTML.
- Without HTML: each page unit has one directly associated screenshot; PC uses screenshot above description, APP uses screenshot left and description right.
- Missing prototypes, filename placeholders, or text such as「页面截图待补」fail final publication.

Every page/module should answer:

- Who sees it.
- How they enter.
- What they need to decide or do.
- What fields are displayed and where the data comes from.
- What actions are allowed.
- What happens after each action.
- What can go wrong.
- What should be tracked.
