# 实验 03 分布式批处理与性能分析

个人脚本为 [student_latency_aggregate.py](student_latency_aggregate.py)。它以 2000 ms 为慢请求阈值，按服务聚合错误数和错误率，使用独立 DuckDB 查询核对。原样教师附件到个人版本的修改见 [完整 diff](student-changes.diff)，仅调整阈值的阶段见 [阈值 diff](slow-threshold-1000-to-2000.diff)。

在仓库根目录使用 Python 3.12 的课程虚拟环境。依次运行实验一、二的课程基线以生成 Silver，核对 `data/silver/events.parquet` 的 SHA-256 与 `data/manifests/silver.json` 一致。然后执行：

```powershell
$studentId = Read-Host '请输入本人学号'
.\.venv\Scripts\python.exe -m coursekit identity --student-id $studentId --lab 03 --stage start
.\.venv\Scripts\python.exe -m coursekit lab03 --workers 1 --partitions 8
.\.venv\Scripts\python.exe -m coursekit lab03 --workers 2 --partitions 8
.\.venv\Scripts\python.exe -m coursekit lab03 --workers 2 --partitions 4
.\.venv\Scripts\python.exe '.\03. 分布式批处理与性能分析\附件\student_latency_aggregate.py'
.\.venv\Scripts\python.exe .\labs\lab03\student_latency_aggregate.py
.\.venv\Scripts\python.exe '.\03. 分布式批处理与性能分析\附件\check_error_extension.py' --threshold 2000
```

教师初版产生 1000 ms 基线，个人脚本产生 2000 ms 扩展结果。专项核验器从 Silver 独立核对错误数和错误率。运行记录由本地课程程序生成。

教师实验说明核对版本为 Gitee `ryukinkou/BDP` 的 `7ffdf1ebc71a62693eabb6f548687194d132135d`。Diff 中保留实验时的原始源码路径。
