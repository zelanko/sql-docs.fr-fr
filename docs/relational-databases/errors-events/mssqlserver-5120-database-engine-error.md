---
title: MSSQLSERVER_5228 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5120 (Database Engine error)
ms.assetid: ''
author: PijoCoder
ms.author: mathoma
ms.openlocfilehash: ff8fb262b643390f2914a4a5e6c42dcc887206f8
ms.sourcegitcommit: 66407a7248118bb3e167fae76bacaa868b134734
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81728616"
---
# <a name="mssqlserver_5120"></a>MSSQLSERVER_5120
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|5120|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DSK_FCB_FAILURE|  
|Texte du message|Erreur de table, Impossible d'ouvrir le fichier physique "%.ls". Erreur %d du système d'exploitation : "%ls".|  
  
## <a name="explanation"></a>Explication  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’a pas pu ouvrir un fichier de base de données.  L’erreur de système d’exploitation fournie dans le message pointe vers des raisons sous-jacentes plus spécifiques pour l’échec. Vous pouvez généralement voir cette erreur avec d’autres erreurs telles que [17204](mssqlserver-17204-database-engine-error.md) ou [17207](mssqlserver-17207-database-engine-error.md)
  
## <a name="user-action"></a>Action de l'utilisateur  
  
  Analysez et corrigez cette erreur de système d'exploitation, puis tentez à nouveau l'opération. Plusieurs états peuvent aider Microsoft à limiter la zone dans le produit où la partie à problème se trouve. 
  
### <a name="access-is-denied"></a>Accès refusé 
Si vous recevez l’erreur de système d’exploitation ```Access is Denied``` = 5, envisagez les méthodes suivantes :
   -  Vérifiez les autorisations définies pour le fichier en examinant les propriétés du fichier dans l’Explorateur Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des groupes Windows pour approvisionner Access Control sur les diverses ressources de fichiers. Assurez-vous que le groupe approprié [avec des noms tels que SQLServerMSSQLUser$NomOrdinateur$MSSQLSERVER ou SQLServerMSSQLUser$NomOrdinateur$NomInstance] dispose des autorisations requises sur le fichier de base de données mentionné dans le message d’erreur. Consultez [Configurer les autorisations du système de fichiers pour l'accès au moteur de base de données](../../2014/database-engine/configure-windows/configure-file-system-permissions-for-database-engine-access.md) pour plus de détails. Assurez-vous que le groupe Windows comprend réellement le compte de démarrage du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou le SID du service.
   -  Examinez le compte d’utilisateur sous lequel le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution. Vous pouvez utiliser le gestionnaire des tâches de Windows pour accéder à ces informations. Recherchez la valeur « Nom d’utilisateur » pour l’exécutable « sqlservr.exe ». En outre, si vous avez récemment modifié le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sachez que la méthode prise en charge pour effectuer cette opération consiste à utiliser l’utilitaire [Gestionnaire de configuration SQL Server](../sql-server-configuration-manager.md). 
   -  Selon le type d’opération (ouverture de bases de données au démarrage serveur, attachement d’une base de données, restauration d’une base de données, etc.), le compte utilisé pour l’emprunt d’identité et l’accès au fichier de base de données peut être différent. Passez en revue la rubrique [Sécurisation des fichiers de données et des fichiers journaux](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms189128(v=sql.105)?redirectedfrom=MSDN) pour savoir quelle opération définit quelles autorisations pour quels comptes. Utilisez un outil tel que Windows SysInternals [Process Monitor](https://docs.microsoft.com/sysinternals/downloads/procmon) pour déterminer si l’accès au fichier se produit dans le contexte de sécurité du compte de démarrage du service d’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [ou du SID de service] ou d’un compte avec emprunt d’identité.

      Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] emprunte les informations d’identification de l’utilisateur de la connexion qui exécute l’opération ALTER DATABASE ou CREATE DATABASE, vous remarquerez les informations suivantes dans l’outil Process Monitor (un exemple) :
        ```Date & Time:      3/27/2010 8:26:08 PM
        Event Class:        File System
        Operation:          CreateFile
        Result:                ACCESS DENIED
        Path:                  C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\DATA\attach_test.mdf
        TID:                   4288
        Duration:             0.0000366
        Desired Access:Generic Read/Write
        Disposition:        Open
        Options:            Synchronous IO Non-Alert, Non-Directory File, Open No Recall
        Attributes:          N
        ShareMode:       Read
        AllocationSize:   n/a
        Impersonating: DomainName\UserName```
  
  
### Attaching Files that Reside on a Network-attached storage  
If you cannot re-attach a database that resides on network-attached storage, a message like this may be logged in the Application log:

```Msg 5120, Level 16, State 101, Line 1 Unable to open the physical file "\\servername\sharename\filename.mdf". Operating system error 5: (Access is denied.).```

This problem occurs because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resets the file permissions when the database is detached. When you try to reattach the database, a failure occurs because of limited share permissions.

To resolve, follow these steps:
1. Use the -T startup option to start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Use this startup option to turn on trace flag 1802 in [SQL Server Configuration Manager](../sql-server-configuration-manager.md) (see [Trace Flags](../../t-sql/database-console-commands/dbcc-traceon-transact-sql.md) for information on 1802). For more information about how to change the startup parameters, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md)

2. Use the following command to detach the database.
```tsql
 exec sp_detach_db DatabaseName
 go 
```

3. Utilisez la commande suivante pour rattacher la base de données.
```tsql
exec sp_attach_db DatabaseName, '\\Network-attached storage_Path\DatabaseMDFFile.mdf', '\\Network-attached storage_Path\DatabaseLDFFile.ldf'
go
```
 
