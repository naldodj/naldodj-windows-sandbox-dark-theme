# naldodj-windows-sandbox-dark-theme

```PowerShell

# Define the path for the registry key
$registryPath = "HKCU:\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize"

# Create the registry key if it does not exist
if (-not (Test-Path $registryPath)) {
    New-Item -Path $registryPath -Force | Out-Null
}

# Set the registry values for dark mode
Set-ItemProperty -Path $registryPath -Name "AppsUseLightTheme" -Type DWord -Value 0
Set-ItemProperty -Path $registryPath -Name "SystemUsesLightTheme" -Type DWord -Value 0

# Restart Windows Explorer to apply changes
Stop-Process -Name explorer -Force
Start-Process explorer

```
