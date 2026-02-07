Epic Games Launcher Repair Utility (EGL-R)

Copyright Joseph Peransi, two thousand twenty-six.

Be excellent to each other.

Overview

EGL-R is a production-grade Python utility engineered to resolve persistent stability issues within the Epic Games Launcher. It implements a "Soft Repair" strategy that aggressively purges corrupt Chromium web caches, temporary configurations, and log files—common culprits for "black screen," "login loop," and "stuck loading" errors—while strictly preserving game installation manifests and user data.

Key Features

Force Termination: Automatically detects and terminates hung EpicGamesLauncher.exe processes to release file locks.

Deep Cache Sanitation: Target-specific removal of webcache, webcache_4147, webcache_4430, and Logs directories in %LOCALAPPDATA%.

Manifest Integrity Check: Verifies the presence of Game Manifests in %PROGRAMDATA% to ensure installed game library index remains intact.

Audit Logging: High-performance logging provides real-time feedback on deleted assets and system checks.

System Requirements

Operating System: Windows 10 / 11 (NT Kernel required)

Runtime: Python 3.8 or higher

Permissions: Administrator privileges (Required for taskkill operations)

Installation & Usage

Clone the Repository

git clone [https://github.com/your-username/epic-launcher-repair.git](https://github.com/your-username/epic-launcher-repair.git)
cd epic-launcher-repair


Execute Repair
Open your terminal (PowerShell or CMD) as Administrator and run:

python epic_repair.py


Technical Breakdown

The script operates on the following logic path:

Privilege Check: Verifies Admin context via ctypes or os.getuid.

Process Kill: Executes tasklist to identify the launcher, followed by taskkill /F to ensure a clean slate.

Cache Iteration: Scans %LOCALAPPDATA%\EpicGamesLauncher\Saved\ for directories matching the webcache* pattern and safely removes them using shutil.

Manifest Verification: specific check on %PROGRAMDATA%\Epic\EpicGamesLauncher\Data\Manifests to confirm game tracking data is present.

Disclaimer

This tool is provided "as is" without warranty of any kind. It is designed to be non-destructive to game binaries (.egstore, game folders), but it deletes launcher-specific cache data. You may be required to log in to your Epic Games account after running this tool.
