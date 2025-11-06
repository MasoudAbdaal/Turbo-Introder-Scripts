# README

Collection of Turbo Intruder + helper scripts. Each entry is the script filename (or goal) and a very short description of what it does.

## Scripts

* **Fuzzer - Wordlist Folder.py**
  Read every file in a folder and use each line as a payload for a single placeholder `__PAYLOAD__`. A gate for each file.

* **Fuzzer - Clustered Bomb (v5).py**
  Clustered-bomb style script: reads `usernames.txt` and `passwords.txt`, builds all user×pass combos and queues them (engine.queue(template, [user, pass])). Tunable concurrency and max combos.

* **Fuzzer - CL.py**
  Replace `Content-Length` in the request template with values in a numeric range (e.g. `1746..1800`) and queue/send them.

* **Fuzzer - Smuggled CL.py**
  For requests that contain two POSTs back-to-back: replace the **second** request’s `Content-Length` with `%s` and test a numeric range.

* **Fuzzer - XFF.py**
  Turbo Intruder script that replaces `X-Forwarded-For` with `127.0.0.1` → `127.0.0.255` and queues requests.

* **(Tuning) - CuncurrentRequests.py**
  Small test script that queues a tiny hard-coded set of combos (useful to verify Turbo Intruder environment works before large runs).


## Quick usage notes

* Placeholders: most Turbo scripts expect placeholders in the base request (e.g. `__USER__`, `__PASS__`, or `__PAYLOAD__`) — replace them before `Send to Turbo Intruder`.
* Jython compatibility: scripts are written for Turbo Intruder (Jython) — avoid f-strings and Python 3-only features.
* Tune `concurrentConnections`, `requestsPerConnection`, and batch sizes according to your machine/network and target. Start small, then increase.


## Legal and safety

Only run these scripts against systems you own or where you have explicit, written permission to test. Misuse may be illegal and unethical. Use responsibly.

---
