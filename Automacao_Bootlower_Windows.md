# Debloat Windows Tool
Remove lixo, remove tranqueira, remove o que não deveria existir no Windows.

## 🤔 Por que eu fiz esse código?

## Porque o Windows vem cheio de coisas que:

✔ Não servem pra nada

✔ Ficam rodando sem motivo

✔ Consomem memória e CPU

✔ Só atrapalham quem quer um sistema leve

Então eu pensei:

“E se eu fizer um debloater meu, do meu jeito, sem frescura?”

## ⚙️ O que o script faz?
## 1️⃣ Debloat Hardcore (sem dó, mas sem quebrar o Spooler)

Remove / desativa:

Serviços inúteis

OneDrive

Widgets

Xbox

Telemetria

Mapas, 3D Viewer, Whiteboard, GetHelp, FeedbackHub…

Loja (Windows Store)

Apps UWP inúteis

Coisas que nem a Microsoft lembra que existem 😅

## 2️⃣ Restaura apenas o essencial

Microsoft Store

Calculadora

Fotos

Qualquer coisa essencial pro Windows funcionar direito

```bash
# =========================================================
#    Windows Tools
#   Menu + Debloat Hardcore (mantém Spooler)
# =========================================================

$ErrorActionPreference = "SilentlyContinue"

function Show-Menu {
    Clear-Host
    Write-Host "============================================="
    Write-Host "        HYDRO RS - WINDOWS TOOLKIT"
    Write-Host "============================================="
    Write-Host "1) Debloat Windows (Hardcore)"
    Write-Host "2) Restaurar Apps Essenciais"
    Write-Host "3) Sair"
    Write-Host "============================================="
}

# =========================================================
# 1) FUNÇÃO DEBLOAT HARDCORE
# =========================================================
function Debloat-Windows {

    Write-Host "`n[1/4] Desativando serviços inúteis...`n"

    $servicesToDisable = @(
      "DiagTrack","dmwappushservice",
      "WMPNetworkSvc",
      "XblAuthManager","XblGameSave","XboxGipSvc","XboxNetApiSvc",
      "OneSyncSvc","DoSvc",
      "WerSvc","Fax","WSearch"
    )

    foreach ($s in $servicesToDisable) {
        Stop-Service -Name $s -Force
        Set-Service -Name $s -StartupType Disabled
        Write-Host "   Serviço desativado: $s"
    }

    Write-Host "`n[2/4] Removendo OneDrive...`n"

    taskkill /F /IM OneDrive.exe | Out-Null
    $odExe = "$env:SystemRoot\System32\OneDriveSetup.exe"
    if (Test-Path "$env:SystemRoot\SysWOW64\OneDriveSetup.exe") {
        $odExe = "$env:SystemRoot\SysWOW64\OneDriveSetup.exe"
    }
    if (Test-Path $odExe) { & $odExe /uninstall }

    Start-Sleep 2
    Remove-Item -Recurse -Force "$env:UserProfile\OneDrive"
    Remove-Item -Recurse -Force "$env:LocalAppData\Microsoft\OneDrive"
    Remove-Item -Recurse -Force "$env:ProgramData\Microsoft OneDrive"

    reg add "HKLM\Software\Policies\Microsoft\Windows\OneDrive" /v DisableFileSync /t REG_DWORD /d 1 /f | Out-Null


    Write-Host "`n[3/4] Removendo Bloatware UWP (inclusive Store, Widgets, Xbox)...`n"

    $appsToRemove = @(
      "Microsoft.Bing*","Microsoft.WindowsMaps","Microsoft.MicrosoftNews","Microsoft.News",
      "Microsoft.Xbox*","Microsoft.GamingApp",
      "Microsoft.ZuneMusic","Microsoft.ZuneVideo",
      "Microsoft.3DBuilder","Microsoft.Print3D","Microsoft.Microsoft3DViewer",
      "Microsoft.Whiteboard","Microsoft.MicrosoftOfficeHub","Microsoft.SkypeApp",
      "Microsoft.GetHelp","Microsoft.WindowsFeedbackHub","Microsoft.YourPhone",
      "Microsoft.Getstarted","Microsoft.Windows.Photos","Microsoft.WindowsCamera",
      "Microsoft.549981C3F5F10",
      "MicrosoftWindows.Client.WebExperience",
      "Microsoft.WindowsStore",
      "Microsoft.MSPaint","Microsoft.Todos","Microsoft.OneConnect"
    )

    foreach ($p in $appsToRemove) {
        Get-AppxPackage -AllUsers $p | Remove-AppxPackage
        Get-AppxProvisionedPackage -Online |
          Where-Object { $_.DisplayName -like $p } |
          ForEach-Object {
            Remove-AppxProvisionedPackage -Online -PackageName $_.PackageName | Out-Null
            Write-Host "   Removido: $($_.DisplayName)"
          }
    }


    Write-Host "`n[4/4] Desabilitando tarefas de telemetria...`n"

    $tasksToDisable = @(
      "\Microsoft\Windows\Application Experience\Microsoft Compatibility Appraiser",
      "\Microsoft\Windows\Application Experience\ProgramDataUpdater",
      "\Microsoft\Windows\Customer Experience Improvement Program\Consolidator",
      "\Microsoft\Windows\Customer Experience Improvement Program\UsbCeip",
      "\Microsoft\Windows\Feedback\Siuf\DmClient",
      "\Microsoft\Windows\Feedback\Siuf\DmClientOnScenarioDownload",
      "\Microsoft\Windows\Maps\MapsUpdateTask",
      "\Microsoft\Windows\Windows Error Reporting\QueueReporting",
      "\Microsoft\XblGameSave\XblGameSaveTask"
    )

    foreach ($t in $tasksToDisable) {
        schtasks /Change /TN $t /Disable | Out-Null
        Write-Host "   Tarefa desativada: $t"
    }

    Write-Host "`n================================================"
    Write-Host "   ✅ Debloat Hardcore concluído!"
    Write-Host "   🔁 Reinicie o PC para aplicar tudo."
    Write-Host "================================================"
}

# =========================================================
# 2) Função Restaurar Apps Essenciais
# =========================================================
function Restore-Apps {
    Write-Host "`nRestaurando Microsoft Store e aplicações essenciais...`n"
    Get-AppxPackage -AllUsers Microsoft.WindowsStore | Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppxManifest.xml"
    Get-AppxPackage -AllUsers Microsoft.WindowsCalculator | Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppxManifest.xml"
    Get-AppxPackage -AllUsers Microsoft.Windows.Photos | Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppxManifest.xml"
    Write-Host "`n✔ Restauração concluída.`n"
}

# =========================================================
# LOOP DO MENU
# =========================================================
do {
    Show-Menu
    $choice = Read-Host "Escolha uma opção"

    switch ($choice) {
        "1" { Debloat-Windows; Pause }
        "2" { Restore-Apps; Pause }
        "3" { Write-Host "Saindo..."; break }
        default { Write-Host "Opção inválida"; Pause }
    }

} while ($true)

````
