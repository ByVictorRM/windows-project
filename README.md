🛡️Admin PowerShell might be required
## System and Quick Configuration
- `systempropertiesadvanced` — Open System Properties (Advanced tab).
- `sysdm.cpl` — System Properties (general).
- `control /name Microsoft.System` — Control Panel > System.
- `optionalfeatures` — Windows Features (enable WSL, Hyper-V, etc.).
- `appwiz.cpl` — Programs and Features.
- `services.msc` — Services.
- `devmgmt.msc` — Device Manager.
- `compmgmt.msc` — Computer Management.
- `secpol.msc` — Local Security Policy.
- `gpedit.msc` — Group Policy Editor (Pro/Enterprise editions).
- `lusrmgr.msc` — Local Users and Groups.
- `msinfo32` — System Information.
- `dxdiag` — DirectX Diagnostic Tool (graphics/drivers).
- `msconfig` — System Configuration (boot/services).
- `taskmgr` — Task Manager.
- `resmon` — Resource Monitor.
- `perfmon` — Performance Monitor.
- `eventvwr` — Event Viewer.
- `regedit` 🛡️ — Registry Editor (use with care).

## Developer Settings (URI ms-settings:)
- `ms-settings:developers` — Developer mode.
- `ms-settings:appsfeatures` — Apps & Features.
- `ms-settings:optionalfeatures` — Optional Features.
- `ms-settings:windowsupdate` — Windows Update.

## Networking and Connectivity
- `ipconfig /all` — Show network configuration.
- `ipconfig /flushdns` — Flush DNS cache.
- `nslookup example.com` — DNS resolution.
- `ping 8.8.8.8` — Check latency.
- `tracert example.com` — Route trace.
- `pathping example.com` — Route + packet diagnostics.
- `netstat -ano` — Connections/ports with PID.
- `netstat -ano | findstr :8080` Find a process in a specific port
- `Get-NetTCPConnection` (PowerShell) — TCP connections.
- `ssh user@host` — SSH (Windows 10+).
- `curl https://example.com` — HTTP quick requests/downloads.
- `netsh wlan show profiles` — Wi-Fi profiles.
- `netsh interface ip show addresses` — IP addresses per interface.

## Files, Search, and Sync
- `where <exe>` — Find executable path (`where node`).
- `where /r C:\ project.json` — Recursive search.
- `dir /s /b *.csproj` — Recursive list (bare format).
- `findstr /s /n /i "TODO" *.*` — Search text in tree.
- `fc a.txt b.txt` — File diff.
- `robocopy src dst /MIR /XF *.log` 🛡️ — Robust copy (mirrors, filters).
- `xcopy src dst /E /I /Y` — Copy (legacy, prefer Robocopy).
- `mklink /J node_modules D:\cache\node_modules` 🛡️ — Symbolic/junction link.
- `tar -xf archive.tar.gz` — Extract TAR/GZ natively.
- `compact /c /s:.` — NTFS compression in folder.

## Disk and System Health
- `sfc /scannow` 🛡️ — Repair system files.
- `DISM /Online /Cleanup-Image /RestoreHealth` 🛡️ — Repair Windows image.
- `chkdsk C: /scan` 🛡️ — Check disk (online).
- `diskpart` 🛡️ — Disk partitioning (expert).
- `mountvol` — Manage mount points.
- `powercfg /batteryreport` — Battery report (laptops).
- `wmic cpu get name` — CPU model (note: WMIC deprecated, but useful).

## Services, Processes, and Boot
- `sc query type= service` — List services.
- `sc stop <ServiceName>` 🛡️ — Stop service.
- `tasklist /v` — Processes with details.
- `taskkill /PID 1234 /F` 🛡️ — Kill process.
- `bcdedit` 🛡️ — Boot configuration (use with care).

## Environments, Variables, and Sessions
- `set` — View environment variables (CMD).
- `setx KEY value` — Persist environment variable (user).  
  Example: `setx JAVA_HOME "C:\Program Files\Java\jdk-21"`
- `rundll32 sysdm.cpl,EditEnvironmentVariables` — Direct environment variables dialog.
- `whoami /groups` — Current user and groups.
- `runas /user:DOMAIN\user cmd` — Run as another user.

## WSL and Containers
- `wsl --install` 🛡️ — Install WSL (Windows 11/10).
- `wsl -l -v` — List distros and version.
- `wsl --shutdown` — Restart WSL.
- `wsl -d Ubuntu` — Enter a specific distro.
- `docker version` — Verify Docker installation.
- `docker ps -a` — List containers.
- `docker compose up -d` — Start a stack.

## .NET / Visual Studio / Node Ecosystem
- `dotnet --info` — Installed SDKs and runtimes.
- `dotnet new api -n ApiDemo` — Web API template.
- `dotnet build` / `dotnet test` — Build/Test project.
- `msbuild My.sln /m` — Multi-proc build (VS Build Tools).
- `nuget restore My.sln` — Restore packages (legacy).
- `devenv .` — Open Visual Studio (if in PATH).
- `code .` — Open VS Code in current folder.

## Package Managers (Windows)
- `winget search git` — Search for a package.
- `winget install --id Git.Git` 🛡️ — Install package.
- `winget upgrade --all` 🛡️ — Update all.
- `choco install make -y` 🛡️ — Chocolatey (if installed).

## PowerShell Basics for Automation
- `Get-ChildItem -Recurse -Filter *.cs` — List files (like `ls`).
- `Select-String -Path . -Pattern "TODO" -List` — Quick grep.
- `Get-Process | Sort CPU -Desc | Select -First 10` — Top processes.
- `Get-Service | ? Status -eq Running` — Running services.
- `Start-Process "cmd" -Verb RunAs` — Open elevated.
- `Invoke-WebRequest https://example.com -OutFile out.bin` — Download file.
- `Expand-Archive .\build.zip -DestinationPath build\` — Unzip.
- `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser` 🛡️ — Allow local scripts.
- `New-SelfSignedCertificate` 🛡️ — Generate test certificate.
- `Get-FileHash .\installer.msi -Algorithm SHA256` — Verify integrity.
- `Measure-Command { dotnet build }` — Time a command.

## Network and Web Diagnostics (Dev)
- `netsh http show urlacl` 🛡️ — Reserved URL bindings (HTTP.sys).
- `netsh http add urlacl url=http://+:5000/ user=Everyone` 🛡️ — Grant binding.
- `certmgr.msc` — Manage certificate stores.
- `fiddler` / `wireshark` — If installed, debugging traffic.

---

## Quick Tips
- Use **Windows Terminal** with tabs (PowerShell, CMD, WSL) and add aliases:  
  `New-Alias ll Get-ChildItem`
- Prefer **Robocopy** over `xcopy`; `where` over `which`.
- For repetitive tasks, create **PowerShell scripts** (`.ps1`) and add a scripts folder to your `PATH`.
- Keep `winget upgrade --all` up to date and use `wsl --update` if you work with Linux.
