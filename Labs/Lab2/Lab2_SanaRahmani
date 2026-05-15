# HDFS Replication Factor Returning 0

**Lab:** Lab 2 – HDFS Data Lake Structure (Task 6.4)  
**Student:** Sana Rahmani <br>
**Student ID:** S21107268 <br>
**Date:** 18/02/2026 <br>

---

## Problem Description

While verifying the replication factor using the command:

```bash
hdfs dfs -stat %r /datalake/raw/imaging
```

the output returned:

```bash
0
```

instead of the expected replication value (e.g., `3`).

This caused confusion because the replication factor had already been set using `setrep`.

---

## Steps Taken

1. Created the required directory structure under `/datalake/`.
2. Used the command:

```bash
hdfs dfs -setrep -R 3 /datalake/raw/imaging
```

3. Tried to verify replication using:

```bash
hdfs dfs -stat %r /datalake/raw/imaging
```

4. The output returned:

```bash
0
```

---

## Error Messages / Screenshots

No explicit error message was shown.

The command simply returned:

```bash
0
```

---

## Solution / Fix

The issue occurred because:

- `-stat %r` works on **files**, not directories.

To correctly verify replication:

1. Upload a file inside the directory:

```bash
hdfs dfs -put ~/xray.txt /datalake/raw/imaging/
```

2. Then run:

```bash
hdfs dfs -stat %r /datalake/raw/imaging/xray.txt
```

This correctly returned the expected replication factor (e.g., `3`).

---

## Notes

- Replication settings apply to files, not directories directly.
- Always verify replication using a specific file path.
- If the cluster has only one DataNode, the effective replication may be limited even if a higher replication factor is requested.

---

## Keywords

`HDFS` `Replication Factor` `Hadoop` `Big Data` `Data Lake`
