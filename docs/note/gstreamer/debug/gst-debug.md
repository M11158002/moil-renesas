# 4.1 GStreamer Debug

## 4.1.1 Dependencies Installation

Install the graphviz tools

```bash
sudo apt install graphviz
```

## 4.1.2 Debugging

Set the GST_DEBUG_DUMP_DOT_DIR environment variable to the directory where the dot files will be saved.

```bash
export GST_DEBUG_DUMP_DOT_DIR="$HOME/tmp/graphs"
```

Use the dot tool to convert the dot files to png files.

```bash
dot -Tpng $HOME/workspace/tmp/graphs/*.dot -o $HOME/workspace/tmp/graphs/pipeline.png
```
