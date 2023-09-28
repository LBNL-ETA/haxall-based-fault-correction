## Introduction

This collection of Axon code and Folio records includes components needed to 
implement an AHU schedule monitoring module.

Axon and Folio are part of Haxall, an open source framework (https://haxall.io/),
however, some of the code in this package relies upon a schedule library and related
functionalities that are only available in SkySpark (https://skyfoundry.com/product), 
which requires obtaining a paid license.

The provided view will show a list of all AHUs on the cluster, and offers actions
to set up and subsequently edit a target schedule point for a selected AHU. Note
that the created schedule point counts against the server license if using
SkySpark.

Upon selecting an AHU in the view, a selection of relevant trends is
shown on the right-side panel. If a target schedule point has been set up for the
selected AHU, it also shows a comparison between observed "run" trends and the
target schedule, with a summary of deviations split into three categories:
- Target ON but observed OFF
- Target OFF but observed ON, within allowed warm-up period before scheduled start
- Target OFF but observed ON, outside of allowed warm-up

Components:
- Functions (`func`) are provided in individual text files that contain the source of
  each function. Function records, including the `func` and `dis` tags, must be
  created manually.
- Views (`view`) are provided in individual trio files that contain the entire `view`
  record, including the `src` and all other view record tags. They can be loaded
  and committed to Folio as new records.
- Templates (`template`) are provided in individual trio files that contain the entire
  `template` record, including the `tags` and all other template record tags. They
  can be loaded and committed to Folio as new records.

Tagging requirements for AHUs to be shown in the view table:
```
- ahu
```

Tagging requirements for points to be used in AHU's "Run Summary" analysis:
```
- ahu
--- run, sensor, kind:"Bool"
--- run, cmd, kind:"Bool"
```
As-written, the analysis function also excludes computed points (hisFunc).
