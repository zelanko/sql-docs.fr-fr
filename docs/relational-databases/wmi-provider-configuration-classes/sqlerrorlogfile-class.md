---
title: Classe SqlErrorLogFile
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 186ceb700a09436ba7bc44934b28627480fa0454
ms.sourcegitcommit: 039fb38c583019b3fd06894160568387a19ba04e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2020
ms.locfileid: "87442499"
---
# <a name="sqlerrorlogfile-class"></a>Classe SqlErrorLogFile
[!INCLUDE[sqlserver](../../includes/applies-to-version/sqlserver.md)]
  Fournit des propriétés pour l'affichage des informations relatives à un fichier journal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
class SQLErrorLogFile  
{  
   uint32ArchiveNumber;  
   stringInstanceName;  
   datetimeLastModified;  
   uint32LogFileSize;  
   stringName;  
  
};  
```  
  
## <a name="properties"></a>Propriétés  
 La classe SQLErrorLogFile définit les propriétés suivantes.  
  
| Propriété | Description |
| -------- | ----------- |
|ArchiveNumber|Type de données : **UInt32**<br /><br /> Type d'accès : Lecture seule<br /><br /> <br /><br /> Numéro d'archive pour le fichier journal.|  
|InstanceName|Type de données : **chaîne**<br /><br /> Type d'accès : Lecture seule<br /><br /> Qualificateurs : Clé<br /><br /> <br /><br /> Nom de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] où le fichier journal réside.|  
|LastModified|Type de données : **DateTime**<br /><br /> Type d'accès : Lecture seule<br /><br /> <br /><br /> Date de la dernière modification du fichier journal.|  
|LogFileSize|Type de données : **UInt32**<br /><br /> Type d'accès : Lecture seule<br /><br /> <br /><br /> Taille du fichier journal, en octets.|  
|Nom|Type de données : **chaîne**<br /><br /> Type d'accès : Lecture seule<br /><br /> Qualificateurs : Clé<br /><br /> <br /><br /> Nom du fichier journal.|  
  
## <a name="remarks"></a>Remarques  
  
| Type | Nom |
| ---- | ---- |
|MOF|Sqlmgmprovider xpsp2up.mof|  
|DLL|Sqlmgmprovider.dll|  
|Espace de noms|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant extrait les informations relatives à tous les fichiers journaux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur une instance spécifiée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour exécuter l’exemple, remplacez \<*Instance_Name*> par le nom de l’instance, par exemple « Instance1 ».  
  
```  
on error resume next  
set strComputer = "."  
set objWMIService = GetObject("winmgmts:\\.\root\Microsoft\SqlServer\ComputerManagement10")  
set LogFiles = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogFile WHERE InstanceName = '<Instance_Name>'")  
  
For Each logFile in LogFiles  
  
WScript.Echo "Instance Name:  " & logFile.InstanceName & vbNewLine _  
    & "Log File Name:  " & logFile.Name & vbNewLine _  
    & "Archive Number: " & logFile.ArchiveNumber & vbNewLine _  
    & "Log File Size:  " & logFile.LogFileSize & " bytes" & vbNewLine _  
    & "Last Modified:  " & logFile.LastModified & vbNewLine _  
  
Next   
```  
  
## <a name="comments"></a>Commentaires  
 Lorsque *InstanceName* n’est pas fourni dans l’instruction WQL, la requête retourne des informations pour l’instance par défaut. Par exemple, l'instruction WQL suivante retournera les informations relatives à tous les fichiers journaux de l'instance par défaut (MSSQLSERVER).  
  
```  
"SELECT * FROM SqlErrorLogFile"  
```  
  
## <a name="security"></a>Sécurité  
 Pour vous connecter à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fichier journal via WMI, vous devez disposer des autorisations suivantes sur les ordinateurs locaux et distants :  
  
-   Accès en lecture à l’espace de noms WMI **Root\Microsoft\SqlServer\ComputerManagement10** . Par défaut, tout le monde dispose de l'accès en lecture via l'autorisation Activer le compte.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la vérification des autorisations WMI, consultez la section sécurité de la rubrique [afficher les fichiers journaux hors connexion](../../relational-databases/logs/view-offline-log-files.md).  
  
-   Autorisation en lecture sur le dossier qui contient les journaux des erreurs. Par défaut, les journaux des erreurs se trouvent dans le chemin d’accès suivant (où \<*Drive> * représente le lecteur sur lequel vous avez installé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le \<*InstanceName*> nom de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ) :  
  
     ** \<Drive> : \Program Files\Microsoft SQL Server\MSSQL11** **. \<InstanceName> \MSSQL\Log**  
  
 Si vous vous connectez via un pare-feu, vérifiez qu'une exception est définie dans le pare-feu pour WMI sur les ordinateurs cibles distants. Pour plus d’informations, consultez [connexion à WMI à distance à partir de Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>Voir aussi  
 [SqlErrorLogEvent, classe](../../relational-databases/wmi-provider-configuration-classes/sqlerrorlogevent-class.md)   
 [Afficher les fichiers journaux hors connexion](../../relational-databases/logs/view-offline-log-files.md)  
  
  
