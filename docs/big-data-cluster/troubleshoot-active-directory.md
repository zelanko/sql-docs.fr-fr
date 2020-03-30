---
title: Résoudre les problèmes de déploiement en mode Active Directory
titleSuffix: SQL Server Big Data Cluster
description: Résolvez les problèmes de déploiement d’un cluster Big Data SQL Server dans un domaine Active Directory.
author: rl-msft
ms.author: rafidl
ms.reviewer: mikeray
ms.date: 03/12/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5d887eadd021641241516a1478c6ac13e0d0bdec
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "79191210"
---
# <a name="troubleshoot-sql-server-big-data-cluster-active-directory-mode-deployment"></a>Résoudre les problèmes de déploiement en mode Active Directory d’un cluster Big Data SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment résoudre les problèmes de déploiement d’un cluster Big Data SQL Server en mode Active Directory.

## <a name="check-deployment-progress"></a>Vérifier la progression du déploiement

Le déploiement peut prendre plusieurs minutes. Si le cluster n’est pas prêt au bout de 15 minutes, consultez les journaux du contrôleur pour plus de détails.

Pendant le déploiement du cluster, vérifiez les pods.

```console
kubectl get pods -n mssql-cluster
```

Vérifiez que la liste de pods retournée comprend :

- `compute-`$
- `data-`
- `storage-`

Si les pods compute, data et storage ne sont pas créés, consultez les journaux pour en déterminer la raison.

## <a name="check-logs"></a>Inspecter les journaux d’activité

Pour déterminer la raison de l’arrêt du déploiement sans que les pods compute, data ou storage soient créés, consultez les journaux suivants : 

- Consultez `controller.log` (`<folderOfDebugCopyLog>\debuglogs-mssql-cluster-20200219-093941\mssql-cluster\control-<suffix>\controller\controller\<date>\controller.log`). Recherchez l’entrée suivante :

  `WARN | StatefulSet master is not ready with 0 ready pods and 3 unready pods `

- Consultez `master-0` `provisioner.log` (`<folderOfDebugCopyLog>\debuglogs-mssql-cluster-20200219-093941\mssql-cluster\master-0\mssql-server\provisioner\provisioner.log`)

  ```
  ERROR | Failed to create sql login for domain user [<domain>.<top-level-domain>\<domain-group>]
    Traceback (most recent call last):
      File "/opt/provisioner/bin/scripts/provisioningpool.py", line 214, in executeNonQueries
        connection.execute_non_query(command)
      File "src/_mssql.pyx", line 1033, in _mssql.MSSQLConnection.execute_non_query
      File "src/_mssql.pyx", line 1061, in _mssql.MSSQLConnection.execute_non_query
      File "src/_mssql.pyx", line 1634, in _mssql.check_and_raise
      File "src/_mssql.pyx", line 1683, in _mssql.maybe_raise_MSSQLDatabaseException
    _mssql.MSSQLDatabaseException: (15401, b"Windows NT user or group '<domain>.<top-level-domain>\\<domain-group>' not found. Check the name again.DB-Lib error message 20018, severity 16:\nGeneral SQL Server error: Check messages from the SQL Server\n")
  WARNING | [3/3] Provisioning exception occurred during provisioning step: ProvisioningMasterPool.
  WARNING | Failed to create sql login for domain user [<domain>.<top-level-domain>\<domain-group>]
  WARNING | Retrying.
  ```

  Dans l’exemple ci-dessus, le déploiement ne parvient pas à créer de compte de connexion pour l’utilisateur du domaine, car l’étendue du groupe de domaine est définie comme étant de type domaine local. Utilisez des groupes dont l’étendue est de type domaine global ou domaine universel. [Déployer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] en mode Active Directory](deploy-active-directory.md) explique les exigences d’étendue des groupes Active Directory.

## <a name="check-the-scope-of-domain-groups"></a>Vérifier l’étendue des groupes de domaine

Vérifiez l’étendue du groupe de domaine (<`domain-group`>). Utilisez [get-adgroup](/powershell/module/addsadministration/get-adgroup/).

Si l’étendue du groupe `<domain-group>` est de type domaine local (`DomainLocal`), le déploiement échoue. 

Le script PowerShell suivant vérifie l’étendue de deux groupes AD nommés `bdcadmins` et `bdcusers`. Remplacez les noms par les noms de vos groupes. 

```powershell
#Administrators and users AD groups
$Cluster_admins_group='bdcadmins'
$Cluster_users_group='bdcusers'

#Performing AD Group Checks...

#AD admin group Check
$ClusterAdminGroupScope_Result = New-Object System.Collections.ArrayList
try {
    $GroupScope = Get-ADgroup -Identity $Cluster_admins_group | Select-Object -ExpandProperty GroupScope
    
    if ($GroupScope -eq 'DomainLocal') {
        [void]$ClusterAdminGroupScope_Result.Add("Misconfiguration - $Cluster_admins_group Group scope is $GroupScope, this scope is not supported, Please change group scope to either Global or Univesal") 
    }
    else {
        [void]$ClusterAdminGroupScope_Result.Add("OK - $Cluster_admins_group Group scope is $GroupScope")
    }
}
catch {
    [void]$ClusterAdminGroupScope_Result.Add("Error - " + $_.exception.message)
}
#Ad users group check
$ClusterUsersGroupScope_Result = New-Object System.Collections.ArrayList
$GroupScope = ''
try {
    $GroupScope = Get-ADgroup -Identity $Cluster_users_group | Select-Object -ExpandProperty GroupScope
    
    if ($GroupScope -eq 'DomainLocal') {
        [void]$ClusterUsersGroupScope_Result.Add("Misconfiguration - $Cluster_users_group Group scope is $GroupScope, this scope is not supported, Please change group scope to either Global or Univesal")
    } 
    else 
    { [void]$ClusterUsersGroupScope_Result.Add("OK - $Cluster_users_group Group scope is $GroupScope") }
}
catch {
    [void]$ClusterUsersGroupScope_Result.Add("Error - " + $_.exception.message)
}

#Display the results
$ClusterUsersGroupScope_Result
```

## <a name="check-security-support-container"></a>Vérifier le conteneur security-support 

Examinez les journaux du conteneur security-support.

La commande suivante collecte les journaux de security-support dans un cluster de l’espace de noms `mssql-cluster`.

```console
azdata bdc debug copy-logs -n mssql-cluster -c security-support
```

Extrayez les journaux et recherchez `\mssql-cluster\control-<identifier>\controller\control-rts5t-controller-stdout.log`.

Dans ce journal, recherchez les entrées suivantes :

```
ERROR    | Failed to create AD user account 'cntrl-controller'. Error code: 53. Message: Failed to create user object: Failed to add object 'CN=cntrl-controller,OU=bdc, DC=CONTOSO, DC=com' to '  <domain>.<top-level-domain>  ': Server is unwilling to perform. 
ERROR | Failed to create AD user account 'ldap-user'. Error code: 53. Message: Failed to create user object: Failed to add object 'CN=ldap-user,OU=bdc, DC=CONTOSO, DC=com' to '  <domain>.<top-level-domain>  ': Server is unwilling to perform. 
ERROR | Failed to create AD user account 'nginx-mgmtproxy'. Error code: 53. Message: Failed to create user object: Failed to add object 'CN=nginx-mgmtproxy,OU=bdc, DC=CONTOSO, DC=com' to '  <domain>.<top-level-domain>  ': Server is unwilling to perform.
```

La présence de ces entrées est le signe qu’il manque au serveur DNS du contrôleur de domaine l’entrée de DNS inversé (enregistrement PTR).

## <a name="verify-reverse-lookup-ptr-record"></a>Vérifier la recherche inversée (enregistrement PTR)
    
Exécutez le script PowerShell suivant pour vérifier que l’entrée de DNS inversé (enregistrement PTR) est configurée.

```powershell
#Domain Controller FQDN 'DCserver01.contoso.local'
$Domain_controller_FQDN = 'DCserver01.contoso.local'

#Performing Domain Controller DNS record, reverse PTR Checks...
$DcControllerDnsPtr_Result = New-Object System.Collections.ArrayList
try {
    $Domain_controller_DNS_Record = Resolve-DnsName $Domain_controller_FQDN -Type A -Server $Domain_DNS_IP_address -ErrorAction Stop
    foreach ($ip in $Domain_controller_DNS_Record.IPAddress) {
        #resolving hostname by IP address to make sure we have reverse PTR record 
        if ((Resolve-DnsName $ip).NameHost -eq $Domain_controller_FQDN) {
            [void]$DcControllerDnsPtr_Result.add("OK - $Domain_controller_FQDN has an A record with an IP $ip, Reverse PTR record is in place") 
        }
        else {
            [void]$DcControllerDnsPtr_Result.add("Missing - $Domain_controller_FQDN has an A record with an IP $ip, But no reverse PTR record was found for the host")
        }
    }
}
catch {
    [void]$DcControllerDnsPtr_Result.add("Error - " + $_.exception.message)
}

#show the results 
$DcControllerDnsPtr_Result
```

[Vérifier l’entrée de DNS inversé (enregistrement PTR) pour le contrôleur de domaine](deploy-active-directory.md#verify-reverse-dns-entry-for-domain-controller).