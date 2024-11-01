---
sidebar_position: 3
---
# 4.2.3 Usage Guide

## Use GStreamer API calls interception

Set the `LD_PRELOAD` environment variable

```bash
export LD_PRELOAD="/usr/local/lib/x86_64-linux-gnu/libgsttracer.so:$LD_PRELOAD"
```

Set the `GST_DEBUG_DUMP_TRACE_DIR` environment variable

```bash
export GST_DEBUG_DUMP_TRACE_DIR="$HOME/workspace/tmp/gst-trace"
```

## Use GStreamer Plugin

Set the `GST_PLUGIN_PATH` environment variable

```bash
export GST_PLUGIN_PATH="/usr/local/lib/x86_64-linux-gnu/gstreamer-1.0/:$GST_PLUGIN_PATH"
```

Set the `GST_TRACERS` environment variable

```bash
export GST_TRACERS="instruments"
```

Set the `GST_DEBUG_DUMP_TRACE_DIR` environment variable

```bash
export GST_DEBUG_DUMP_TRACE_DIR="$HOME/workspace/tmp/gst-trace"
```

## Usage GStreamer Instruments

Run the GStreamer Pipeline

```bash
gst-launch-1.0 videotestsrc ! autovideosink
```

Check the trace files

```bash
ls $GST_DEBUG_DUMP_TRACE_DIR
```

Use the `gst-report` tool to report the trace files

```bash
gst-report $GST_DEBUG_DUMP_TRACE_DIR/playbin.gsttrace
```

Use "gst-report" to graph the trace files

```bash
gst-report-1.0 --dot playbin.gsttrace | dot -Tpng > perf.png
```

Use "gst-instruments-1.0" to display the trace files

```bash
gst-instruments-1.0 playbin.gsttrace
```
