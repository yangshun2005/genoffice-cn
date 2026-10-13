# 共享内置字体

多个应用共用的字体文件。以前每个应用各带一份副本；集中放在这里后，每个包只需下载一次，许可证只需记录一次，构建时补丁也只需写入一处。

| 字体       | 文件            | 许可证  | 使用方               |
| ---------- | --------------- | ------- | -------------------- |
| Carlito GO | `Carlito-*.ttf` | OFL 1.1 | docs、sheets、slides |

"Carlito GO" 是 Carlito 1.103（LibreOffice 的度量兼容 Calibri 替代字体），由 `tools/patch-carlito-vi.py` 重建了越南语叠置变音符号，并按 OFL 1.1 §2 重命名（"Carlito" 是保留字体名称）。完整 OFL 文本位于 `apps/docs/src/renderer/fonts/LICENSE-OFL.txt`，各字体说明位于 `apps/docs/src/renderer/fonts/README.md`。

通过包导出引用这些文件，可在 CSS 或主进程资源导入中使用：

```css
src: url('@genoffice/ui/fonts/Carlito-Regular.ttf');
```

```ts
import carlitoRegular from '@genoffice/ui/fonts/Carlito-Regular.ttf?asset'
```