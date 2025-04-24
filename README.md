## Script: Monitor_Backup_And_Restore_Progress.sql

**Description**:
This script queries `sys.dm_exec_requests` to display **real-time progress** of any running `BACKUP DATABASE` or `RESTORE DATABASE` operations, including:
- Completion percentage
- Estimated finish time
- Duration remaining in minutes

---

### 📋 Output Columns:

| Column                   | Description                                                 |
|---------------------------|-------------------------------------------------------------|
| `session_id`              | Session executing the backup or restore                    |
| `start_time`              | When the operation began                                   |
| `status`                  | Current session status (`running`, `suspended`, etc.)       |
| `command`                 | `BACKUP DATABASE` or `RESTORE DATABASE`                    |
| `percent_complete`        | % completed so far (0.00 to 100.00)                         |
| `estimated_completion_time` | Estimated time left in milliseconds                       |
| `estimate_completion_minutes` | Estimated time left in minutes (approx.)               |
| `estimated_completion_time` (calculated) | Estimated date and time of completion       |

---



###  Use Case:
- Monitor backup/restore jobs in progress
- Estimate when operations will finish
- Troubleshoot slow or long-running backup tasks

---

### ⚠️ Notes:
- `estimated_completion_time` is **based on SQL Server’s internal estimates** — accuracy may vary.
- You can also use this for `BACKUP LOG` or `RESTORE LOG` by extending the `WHERE` clause if needed.
- Useful for DBAs to track job duration without needing Agent history.

 
