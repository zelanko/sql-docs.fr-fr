---
description: MSSQLSERVER_17204
title: MSSQLSERVER_17204 | Microsoft Docs
ms.custom: ''
ms.date: 07/25/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17204 (Database Engine error)
ms.assetid: 40db66f9-dd5e-478c-891e-a06d363a2552
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d0dafe59102083ea1cd5c675819487eb88c9ecbc
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91869484"
---
# <a name="mssqlserver_17204"></a>MSSQLSERVER_17204
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |
| :-------- | :---- |
|Nom du produit|SQL Server|  
|ID de l’événement|17204|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBLKIO_DEVOPENFAILED|  
|Texte du message|%ls : impossible d’ouvrir le fichier %ls pour le numéro de fichier %d.  Erreur de système d'exploitation : %ls.|  
  
## <a name="explanation"></a>Explication  
SQL Server n'a pas pu ouvrir le fichier spécifié en raison de l'erreur de système d’exploitation spécifiée.  

Vous pouvez voir l’erreur 17204 dans l’événement d’application Windows ou le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lorsque SQL Server ne peut pas ouvrir une base de données et/ou des fichiers journaux de transactions. Voici un exemple de ce à quoi cette erreur peut ressembler :

``` 
Error: 17204, Severity: 16, State: 1.
FCB::Open failed: Could not open file c:\Program Files\Microsoft SQL Server\MSSQL10.SQL2008\MSSQL\data\MyDB_Prm.mdf for file number 1.  OS error: 5(Access is denied.).
```

Vous pouvez voir ces erreurs pendant le processus de démarrage de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou toute opération de base de données qui tente de démarrer la base de données (par exemple ALTER DATABASE). Dans certains scénarios, vous pouvez voir les deux erreurs 17204 et 17207. Dans d’autres occasions, vous ne verrez qu’une d’entre elles.

Si une base de données utilisateur rencontre ces erreurs, cette base de données reste dans l’état RECOVERY_PENDING et les applications ne peuvent pas y accéder. Si une base de données système rencontre ces erreurs, l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne démarre pas et vous ne pouvez pas vous connecter à cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un échec avec une base de données système peut également entraîner la mise hors connexion d’une ressource de cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="cause"></a>Cause
Avant de pouvoir utiliser une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la base de données doit être démarrée. Le processus de démarrage de la base de données implique : 
1. Initialisation de diverses structures de données qui représentent la base de données et les fichiers de base de données
1. Ouverture de tous les fichiers qui appartiennent à la base de données
1. Exécution de la récupération sur la base de données 

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise la fonction d’API Windows [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilea) pour ouvrir les fichiers qui appartiennent à une base de données.
 
Les messages 17204 (et 17207) indiquent qu’une erreur s’est produite lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a tenté d’ouvrir des fichiers de base de données pendant le processus de démarrage.
 
Ces messages d’erreur contiennent les informations suivantes :
1. Nom de la fonction [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui tente d’ouvrir le fichier. Le nom de la fonction que vous observez normalement dans ces messages d’erreur est l’un des suivants :
   - FCB::Open - le fichier a rencontré une erreur quand [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a tenté de l’ouvrir
   - FileMgr::StartPrimaryDataFiles - un fichier de données principal ou un fichier appartenant au groupe de fichiers principal
   - FileMgr::StartSecondaryDataFiles - un fichier appartenant à un groupe de fichiers secondaire
   - FileMgr::StartLogFiles - un fichier de journal des transactions
   - STREAMFCB::Startup - un conteneur FileStream SQL
   - FCB::RemoveAlternateStreams
  
      
1. Les informations d’état distinguent plusieurs emplacements au sein d’une fonction qui peuvent générer ce message d’erreur
1. Le chemin d’accès physique complet du fichier
1. ID du fichier correspondant au fichier
1. Code d’erreur du système d’exploitation et description de l’erreur. Dans certains cas, vous ne verrez que le code d’erreur.
 
Les informations sur l’erreur du système d’exploitation imprimées dans ces messages d’erreur sont la cause principale de l’erreur 17204. Les causes courantes de ces messages d’erreur sont un problème d’autorisation ou un chemin d’accès au fichier incorrect.


## <a name="user-action"></a>Action de l'utilisateur  
1. La résolution de l’erreur 17204 implique la compréhension du code d’erreur de système d’exploitation associé et le diagnostic de cette erreur. Une fois la condition d’erreur du système d’exploitation résolue, vous pouvez tenter de redémarrer la base de données (à l’aide de l’instruction ALTER DATABASE SET ONLINE, par exemple) ou de l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour mettre en ligne la base de données affectée. Dans certains cas, il se peut que vous ne puissiez pas résoudre l’erreur du système d’exploitation. Ensuite, vous devez prendre des mesures correctives spécifiques. Nous aborderons ces actions dans cette section.
1. Si le message d’erreur 17204 contient uniquement un code d’erreur et non une description d’erreur, vous pouvez essayer de résoudre le code d’erreur en utilisant la commande suivante à partir d’un interpréteur de commandes de système d’exploitation : net helpmsg <error code>. Si vous obtenez un code d’état à 8 chiffres comme code d’erreur, vous pouvez vous reporter aux sources d’informations comme [Comment convertir un HRESULT en code d’erreur Win32 ?](https://devblogs.microsoft.com/oldnewthing/20061103-07/?p=29133) afin de décoder les codes d’état en erreurs de système d’exploitation.
1. Si vous recevez l’erreur de système d’exploitation `Access is Denied` = 5, envisagez les méthodes suivantes :
   -  Vérifiez les autorisations définies pour le fichier en examinant les propriétés du fichier dans l’Explorateur Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des groupes Windows pour approvisionner Access Control sur les diverses ressources de fichiers. Assurez-vous que le groupe approprié [avec des noms tels que SQLServerMSSQLUser$NomOrdinateur$MSSQLSERVER ou SQLServerMSSQLUser$NomOrdinateur$NomInstance] dispose des autorisations requises sur le fichier de base de données mentionné dans le message d’erreur. Consultez [Configurer les autorisations du système de fichiers pour l'accès au moteur de base de données](/previous-versions/sql/2014/database-engine/configure-windows/configure-file-system-permissions-for-database-engine-access?view=sql-server-2014) pour plus de détails. Assurez-vous que le groupe Windows comprend réellement le compte de démarrage du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou le SID du service.
   -  Examinez le compte d’utilisateur sous lequel le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution. Vous pouvez utiliser le gestionnaire des tâches de Windows pour accéder à ces informations. Recherchez la valeur « Nom d’utilisateur » pour l’exécutable « sqlservr.exe ». En outre, si vous avez récemment modifié le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sachez que la méthode prise en charge pour effectuer cette opération consiste à se servir de l’utilitaire Gestionnaire de configuration SQL Server. Pour plus d’informations à ce propos, consultez [Gestionnaire de configuration SQL Server](../sql-server-configuration-manager.md). 
   -  Selon le type d’opération (ouverture de bases de données au démarrage serveur, attachement d’une base de données, restauration d’une base de données, etc.), le compte utilisé pour l’emprunt d’identité et l’accès au fichier de base de données peut être différent. Passez en revue la rubrique [Sécurisation des fichiers de données et des fichiers journaux](/previous-versions/sql/sql-server-2008-r2/ms189128(v=sql.105)) pour savoir quelle opération définit quelles autorisations pour quels comptes. Utilisez un outil tel que Windows SysInternals [Process Monitor](/sysinternals/downloads/procmon) pour déterminer si l’accès au fichier se produit dans le contexte de sécurité du compte de démarrage du service d’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [ou du SID de service] ou d’un compte avec emprunt d’identité.

      Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] emprunte les informations d’identification de l’utilisateur pour la connexion qui exécute l’opération ALTER DATABASE ou CREATE DATABASE, vous remarquerez les informations suivantes dans l’outil Process Monitor (un exemple) :
        ```Date & Time:      3/27/2010 8:26:08 PM
        Event Class:        File System
        Operation:          CreateFile
        Result:                ACCESS DENIED
        Path:                  C:\Program Files\Microsoft SQL Server\MSSQL10.SQL2008\MSSQL\DATA\attach_test.mdf
        TID:                   4288
        Duration:             0.0000366
        Desired Access:Generic Read/Write
        Disposition:        Open
        Options:            Synchronous IO Non-Alert, Non-Directory File, Open No Recall
        Attributes:          N
        ShareMode:       Read
        AllocationSize:   n/a
        Impersonating: DomainName\UserName```
  
1. If you are getting `The system cannot find the file specified` OS error = 3:
   - Review the complete path from the error message
   - Ensure the disk drive and the folder path is visible and accessible from Windows Explorer
   - Review the Windows Event log to find out if any problems exist with this disk drive
   - If the path is incorrect and if this database already exists in the system, you can change the database file paths using the methods explained in the topic [Move Database Files](../databases/move-database-files.md). You may have to use this procedure, especially for system database files that encounter 17204 or 17207 and you are working through a disaster recovery scenario where the specified disk drives are unavailable. This topic also explains how you can identify the current location of the various system databases [master, model, tempdb, msdb and mssqlsystemresource].
   - If you see this error because the database files are missing, you have to restore the database from a valid backup.
     - If the database file associated with the error belongs to a secondary filegroup, then you can optionally mark that filegroup offline, bring the database online and then perform a restore of that filegroup alone. For more information, refer to the OFFLINE section of the topic [ALTER DATABASE File and Filegroup Options (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).
     - If the file that produced the error is a transaction log file, review the information under the sections "FOR ATTACH" and "FOR ATTACH_REBUILD_LOG" of the topic [CREATE DATABASE (Transact-SQL)](../../t-sql/statements/create-database-transact-sql.md) to understand how you can recreate the missing transaction log files.
   - Ensure that any disk or network location [like iSCSI drive] is available before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attempts to access the database files on these locations. If needed create the required dependencies in Cluster Administrator or Service Control Manager.
1. If you're getting the `The process cannot access the file because it is being used by another process` operating system error = 32:
   - Use a tool like [Process Explorer](/sysinternals/downloads/process-explorer) or [Handle](/sysinternals/downloads/handle) from Windows Sysinternals to find out if another process or service has acquired exclusive lock on this database file
   - Stop that process from accessing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database files. Common examples include anti-virus programs (see guidance for file exclusions in the following [KB article](https://support.microsoft.com/help/309422/choosing-antivirus-software-for-computers-that-run-sql-server) )
   - In a cluster environment, make sure that the sqlservr.exe process from the previous owning node has actually released the handles to the database files. Normally, this doesn't occur, but misconfigurations of the cluster or I/O paths can lead to such issues.
