# 实验 02 数据湖与质量契约

个人政策脚本为 [student_quality_policy_personal.py](student_quality_policy_personal.py)，将输入 Token 上限从 2000 调整为 1200。教师初版与个人版本的差异见 [student-changes.diff](student-changes.diff)。

在仓库根目录使用课程虚拟环境，输入本人的实验标识。先运行仓库根 README 的环境准备和实验一基线，生成共同输入。随后执行：

```powershell
$studentId = Read-Host '请输入本人学号'
.\.venv\Scripts\python.exe -m coursekit identity --student-id $studentId --lab 02 --stage start
.\.venv\Scripts\python.exe -m coursekit lab02
.\.venv\Scripts\python.exe '.\02. 数据湖与质量契约\附件\student_quality_policy.py'
.\.venv\Scripts\python.exe .\labs\lab02\student_quality_policy_personal.py
```

教师初版与个人版本分别生成 2000 和 1200 阈值的结果。个体政策脚本读取 Raw，课程入口生成的共享 Silver 供实验三继续使用。
