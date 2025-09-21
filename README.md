# 📌 GitHub Actions Workflow Components

When you create a workflow file inside:

```
.github/workflows/file_name.yml
```

it follows 4 key concepts: **Event → Job → Step → Runner**.

---
---

## Four Components:
1)Event->
2)Job
3)Step
4)Runner


## 1) **Event** (Trigger 🔔)

* **What starts the workflow?**
* Defined under `on:` in YAML.
* Examples:

  * `push` → runs when you push code.
  * `pull_request` → runs on PRs.
  * `schedule` → run on cron (timed).

👉 Example:

```yaml
on:
  push:
    branches: [ main ]
```

✅ Means: run this workflow whenever code is pushed to `main`.

---

## 2) **Job** (Work unit 📦)

* A **collection of steps**.
* Each job runs on a **runner** (separate VM or container).
* Jobs can run **in parallel** or **sequentially**.

👉 Example:

```yaml
jobs:
  demo:
    runs-on: ubuntu-latest
```

✅ `demo` is the job name, and it runs on an Ubuntu VM.

---

## 3) **Step** (Instructions 📜)

* A **single task inside a job**.
* Can run **shell commands** (`run`) or use **pre-built actions** (`uses`).
* Steps run **in order** inside a job.

👉 Example:

```yaml
steps:
  - name: Greetings
    run: echo "This is my first GitHub Actions file"
```

✅ Step prints a message to the logs.

---

## 4) **Runner** (Executor 🖥️)

* The **machine** where jobs run.
* GitHub provides **hosted runners**:

  * `ubuntu-latest` (Linux)
  * `windows-latest` (Windows)
  * `macos-latest` (Mac)
* You can also use **self-hosted runners** (your own machine/server).

👉 Example:

```yaml
runs-on: ubuntu-latest
```

✅ Job will run on GitHub’s Ubuntu runner.

---

✅ Flow:

1. You **push** code → Event triggers.
2. GitHub spins up a **runner** (Ubuntu VM).
3. Inside it, the **demo job** starts.
4. It executes the **steps** one by one (here: printing a message).

---
---
