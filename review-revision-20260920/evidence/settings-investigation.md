# Settings reload investigation

The additional full-suite failure is reproducible on unmodified upstream commit `882151876883908915b93ed174cd8df1f5e0bd59`. It is a pre-existing timestamp-based reload weakness triggered intermittently by back-to-back writes on this Windows filesystem. The first failing full-suite log remains preserved at the local original log; its result is preserved in `final-first-pytest.json`.

`SettingsStore._write()` saves the file's floating-point `st_mtime`. `_reload_if_changed()` reloads only when a later `st_mtime` differs. The test writes settings with lookback 12, immediately overwrites the file with lookback 48, then calls `get()`. In reproduced failures the two writes receive the same timestamp, so `get()` returns the cached 12 despite the file containing 48.

The source file and test are byte-identical in the integrated checkout and clean upstream. Both use the same existing virtual environment; each run explicitly selects its own repository's `src` via `PYTHONPATH`. Diagnostic module paths are recorded. No repository or test files were edited; pytest cache and bytecode writing were disabled for these runs.

| Measurement | Integrated checkout | Clean upstream |
|---|---:|---:|
| Unchanged isolated pytest test | 10 passed, 0 failed | 8 passed, 2 failed |
| Immediate-write diagnostic | 72 failed / 500 | 66 failed / 500 |
| Same operations with 2ms before external write | 0 failed / 50 | 0 failed / 50 |
| Extra nanosecond-stat diagnostic | 9 failed / 500 | 15 failed / 500 |

Every immediate-write diagnostic failure coincided with an unchanged `st_mtime`; every run with a changed `st_mtime` reloaded successfully. The additional nanosecond diagnostic captured identical `st_mtime_ns` before and after the external edit for all 24 failures. Example clean-upstream failure: both timestamps were `1789856537609310800`, and `get()` returned 12. This demonstrates repeated filesystem timestamps, not merely loss of precision in the floating-point representation. The extra stat affects timing, so its failure frequency is not directly comparable to the first probe.

The 2ms delay is diagnostic evidence only; it was not added to any test or application code. No failures were suppressed. A passing repeat of the full suite does not remove this existing limitation, and its first failure should remain disclosed.

Raw isolated test logs, timestamp rows, scripts and counts are retained in the local preparation records. An initial harness attempt failed before test setup because the explicit temporary-directory parent did not exist. Those setup errors are preserved separately under `setup-attempt/`, excluded from all counts above.
