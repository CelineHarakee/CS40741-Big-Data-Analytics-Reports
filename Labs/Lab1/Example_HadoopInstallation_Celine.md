**Lab:** Lab X – Hadoop Installation & Setup
**Student:** Celine Al Harake <br>
**Student ID:** S22107613 <br>
**Date:** 17/02/2026 <br>

---

## Problem Description

While installing Hadoop on Ubuntu, Hadoop services (NameNode and DataNode) failed to start after configuration. When running:

```
start-dfs.sh
```

the system showed that SSH connection to localhost was refused, and Hadoop daemons were not launching.

---

## Steps Taken

1. Installed Java using:

   ```
   sudo apt install openjdk-11-jdk
   ```

2. Verified Java installation:

   ```
   java -version
   ```

3. Downloaded and extracted Hadoop.

4. Configured:

   * `core-site.xml`
   * `hdfs-site.xml`
   * `mapred-site.xml`
   * `yarn-site.xml`

5. Set `JAVA_HOME` in:

   ```
   ~/.bashrc
   hadoop-env.sh
   ```

6. Attempted to start Hadoop using:

   ```
   start-dfs.sh
   ```

---

## Error Messages

Error shown:

```
ssh: connect to host localhost port 22: Connection refused
```

And:

```
ERROR: JAVA_HOME is not set
```

---

## Solution / Fix

### Fix SSH Issue

Installed and enabled SSH:

```
sudo apt install ssh
sudo service ssh start
```

Generated SSH key:

```
ssh-keygen -t rsa
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
```

Tested SSH connection:

```
ssh localhost
```

After confirming no password was required, Hadoop services were able to start.

---

## Notes

* Always verify `JAVA_HOME` before starting Hadoop.
* SSH must be properly configured for Hadoop to run in pseudo-distributed mode.
* Use `jps` to confirm Hadoop services are running (NameNode, DataNode, SecondaryNameNode).
* If ports are blocked, check firewall settings.

