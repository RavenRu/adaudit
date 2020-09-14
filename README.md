# adaudit
PowerShell Script to perform a quick AD audit
```
_____ ____     _____       _ _ _
|  _  |    \   |  _  |_ _ _| |_| |_
|     |  |  |  |     | | | . | |  _|
|__|__|____/   |__|__|___|___|_|_|
                 by phillips321
```

If you have any decent powershell one liners that could be used in the script please let me know. I'm trying to keep this script as a single file with no requirements on external tools (other than ntdsutil and cmd.exe)

Run directly on a DC using a DA. If you don't trust the code I suggest reading it first and you'll see it's all harmless! (But shouldn't you be doing that anyway with code you download off the net and then run as DA??)

## What this does
* Device Information
  * Get-HostDetails
* Domain Audit
  * Get-MachineAccountQuota
  * Get-SMB1Support
  * Get-FunctionalLevel
  * Get-DCsNotOwnedByDA
* Domain Trust Audit
  * Get-DomainTrusts
* User Accounts Audit
  * Get-InactiveAccounts
  * Get-DisabledAccounts
  * Get-AdminAccountChecks
  * Get-NULLSessions
  * Get-AdminSDHolders
  * Get-ProtectedUsers
* Password Information Audit
  * Get-AccountPassDontExpire
  * Get-UserPasswordNotChangedRecently
  * Get-PasswordPolicy
* Dumps NTDS.dit
  * Get-NTDSdit
* Computer Objects Audit
  * Get-OldBoxes
* GPO audit (and checking SYSVOL for passwords)
  * Get-GPOtoFile
  * Get-GPOsPerOU
  * Get-SYSVOLXMLS
* Check Generic Group AD Permissions
  * Get-OUPerms
* Check For Existence of LAPS in domain
  * Get-LAPSStatus
* Check For Existence of Authentication Polices and Silos
  * Get-AuthenticationPoliciesAndSilos

## Runtime Args
The following switches can be used in combination
* -hostdetails retrieves hostname and other useful audit info
* -domainaudit retrieves information about the AD such as functional level
* -trusts retrieves information about any doman trusts
* -accounts identifies account issues such as expired, disabled, etc...
* -passwordpolicy retrieves password policy information
* -ntds dumps the NTDS.dit file using ntdsutil
* -oldboxes identified outdated OSs like XP/2003 joined to the domain
* -gpo dumps the GPOs in XML and HTML for later analysis
* -ouperms checks generic OU permission issues
* -laps checks if LAPS is installed
* -authpolsilos checks for existenece of authentication policies and silos
* -all runs all checks, e.g. AdAudit.ps1 -all



Что он делает
Информация об устройстве
Get-HostDetails

Аудит домена
Get-MachineAccountQuota
Get-SMB1Support
Get-FunctionalLevel
Get-DCsNotOwnedByDA

Аудит доверия доменов
Get-DomainTrusts

Аудит учетных записей пользователей
Get-InactiveAccounts
Get-DisabledAccounts
Get-AdminAccountChecks
Get-NULLSessions
Get-AdminSDHolders
Get-ProtectedUsers

Аудит информации о паролях
Get-AccountPassDontExpire
Get-UserPasswordNotChangedRecently
Get-PasswordPolicy

Дампы NTDS.dit
Get-NTDSdit

Аудит объектов
Get-OldBoxes

Аудит GPO (и проверка SYSVOL паролей)
Get-GPOtoFile
Get-GPOsPerOU
Get-SYSVOLXMLS

Проверьте общие права группы AD
Get-OUPerms

Проверьте наличие LAPS в домене
Get-LAPSStatus

Проверьте наличие политик и хранилищ аутентификации
Get-AuthenticationPoliciesAndSilos

Аргументы запуска
Следующие флаги могут использоваться в комбинации запуска скрипта

-hostdetails извлекает имя хоста и другую полезную информацию аудита
-domainaudit извлекает информацию об AD, такую как функциональный уровень
-trusts извлекает информацию о любых доверительных отношениях с доменом
-accounts определяет проблемы учетной записи, такие как истек, отключен, и т. д …
-passwordpolicy возвращает информацию о политике паролей
-ntds выводит файл NTDS.dit с помощью ntdsutil
-oldbox идентифицирует устаревшие ОС, такие как XP / 2003, присоединенные к домену
-gpo выдает объекты групповой политики в XML и HTML для последующего анализа
-uperms проверяет общие проблемы с разрешениями OU
-laps проверяет, установлен ли LAPS
-authpolsilos проверяет наличие политик и хранилищ аутентификации
-all запускает все проверки, например AdAudit.ps1 -all
