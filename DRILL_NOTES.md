# Drill notes

This repository is a **deliberate CI-failure sandbox**.

It exists purely to support the incident-response runbook exercise for the CI section: the
workflow in `.github/workflows/ci-drill.yml` is intentionally broken so that the team can
practice reading failed runs, identifying which job failed, and performing a targeted
failed-jobs-only re-run.

## What is here

- `.github/workflows/ci-drill.yml` — a manually triggered (`workflow_dispatch`) workflow with
  two jobs:
  - **Lint (passes)** — a trivial lint check that always succeeds.
  - **Deliberate failure (exits 1)** — a step that unconditionally runs `exit 1`, so the
    job always fails.

## How to run the drill

1. Open the **Actions** tab and select **CI Failure Drill**.
2. Choose **Run workflow** on the default branch (`main`) — it does not run on push by design.
3. Wait for the run to conclude. The overall run fails because of the failing job.
4. On the failed run, use **Re-run failed jobs** (not "Re-run all jobs") to retry only the
   broken job.

## Expected behavior

The failing job will fail again on every attempt — this is intentional and is the entire
point of the sandbox. Do not "fix" it without coordinating with the runbook owner, because
the repo needs a reproducible failure to link from the documentation.
