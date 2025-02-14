#To run this type this in cmd admin // powershell -executionpolicy bypass -File ./fw_00002.ps1//
$directory = Read-Host "Enter Target Directory "  # Change this to your target directory

# Get all .exe files in the directory and subdirectories
$exeFiles = Get-ChildItem -Path $directory -Filter "*.exe" -File -Recurse

foreach ($exe in $exeFiles) {
    $ruleNameOutbound = "Block Outbound - " + $exe.Name
    $ruleNameInbound = "Block Inbound - " + $exe.Name
    $exePath = $exe.FullName
    
    # Add outbound firewall rule
    New-NetFirewallRule -DisplayName $ruleNameOutbound -Direction Outbound -Program $exePath -Action Block -Enabled True
    Write-Output "Blocked Outbound: $exePath"
    
    # Add inbound firewall rule
    New-NetFirewallRule -DisplayName $ruleNameInbound -Direction Inbound -Program $exePath -Action Block -Enabled True
    Write-Output "Blocked Inbound: $exePath"
}

Write-Output "Firewall rules added successfully."
