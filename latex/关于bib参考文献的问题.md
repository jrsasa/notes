要修改LaTeX Workshop的编译配方，使其执行`xelatex -> bibtex -> xelatex`的流程，你需要按照以下步骤在VSCode的`settings.json`中添加或修改一个配方：

1. **打开VSCode设置**：通过点击菜单栏的`文件` > `首选项` > `设置`，或者使用快捷键`Ctrl+,`（在macOS上是`Cmd+,`）打开设置。

2. **编辑settings.json**：在设置搜索框中输入`latex-workshop.latex.recipes`，找到该项设置，并点击`在 settings.json 中编辑`。

3. **添加或修改配方**：在`settings.json`文件中，找到`latex-workshop.latex.recipes`部分。你可以修改现有的配方或添加一个新配方。以下是一个添加新配方的示例，该配方包含了`xelatex -> bibtex -> xelatex`的编译流程：

   ```json
   "latex-workshop.latex.recipes": [
       {
           "name": "xelatex -> bibtex -> xelatex",
           "tools": [
               "xelatex",
               "bibtex",
               "xelatex"
           ]
       }
   ]
   ```

   如果这个配方是你唯一或首选的配方，确保它位于`latex-workshop.latex.recipes`数组的第一个位置。

4. **确保工具配置正确**：同样，在`settings.json`中，确保`latex-workshop.latex.tools`包含了`xelatex`和`bibtex`的正确配置，如：

   ```json
   "latex-workshop.latex.tools": [
       {
           "name": "xelatex",
           "command": "xelatex",
           "args": [
               "-synctex=1",
               "-interaction=nonstopmode",
               "-file-line-error",
               "%DOC%"
           ]
       },
       {
           "name": "bibtex",
           "command": "bibtex",
           "args": [
               "%DOCFILE%"
           ]
       }
   ]
   ```

5. **保存并使用新配方**：保存`settings.json`文件后，新的配方应该在LaTeX Workshop的编译菜单中可用。你现在可以使用这个配方来编译你的LaTeX项目。

通过这种方式，你可以自定义LaTeX文档的编译流程，确保文档可以根据你的需要正确编译。