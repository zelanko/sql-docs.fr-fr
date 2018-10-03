---
title: Sqlerrorlogfile, classe | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 1cd24b1717bca086bf1419a2df3b44b57104d1f7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48226609"
---
# <a name="sqlerrorlogfile-class"></a>Classe SqlErrorLogFile
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
  
## <a name="properties"></a>Properties  
 La classe SQLErrorLogFile définit les propriétés suivantes.  
  
|||  
|-|-|  
|ArchiveNumber|Type de données : `uint32`<br /><br /> Type d'accès : Lecture seule<br /><br /> <br /><br /> Numéro d'archive pour le fichier journal.|  
|InstanceName|Type de données : `string`<br /><br /> Type d'accès : Lecture seule<br /><br /> Qualificateurs : Clé<br /><br /> <br /><br /> Nom de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] où le fichier journal réside.|  
|LastModified|Type de données : `datetime`<br /><br /> Type d'accès : Lecture seule<br /><br /> <br /><br /> Date de la dernière modification du fichier journal.|  
|LogFileSize|Type de données : `uint32`<br /><br /> Type d'accès : Lecture seule<br /><br /> <br /><br /> Taille du fichier journal, en octets.|  
|Nom   |Type de données : `string`<br /><br /> Type d'accès : Lecture seule<br /><br /> Qualificateurs : Clé<br /><br /> <br /><br /> Nom du fichier journal.|  
  
## <a name="remarks"></a>Notes  
  
|||  
|-|-|  
|MOF|Sqlmgmprovider xpsp2up.mof|  
|DLL|Sqlmgmprovider.dll|  
|Espace de noms|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant extrait les informations relatives à tous les fichiers journaux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur une instance spécifiée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour exécuter l’exemple, remplacez \< *nom_instance*> par le nom de l’instance, par exemple, « Instance1 ».  
  
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
 Lorsque *InstanceName* n’est fourni dans l’instruction WQL, la requête retournera les informations pour l’instance par défaut. Par exemple, l'instruction WQL suivante retournera les informations relatives à tous les fichiers journaux de l'instance par défaut (MSSQLSERVER).  
  
```  
"SELECT * FROM SqlErrorLogFile"  
```  
  
## <a name="security"></a>Sécurité  
 Pour vous connecter à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fichier journal via WMI, vous devez disposer des autorisations suivantes sur les ordinateurs locaux et distants :  
  
-   Accès en lecture à la **Root\Microsoft\SqlServer\ComputerManagement10** espace de noms WMI. Par défaut, tout le monde dispose de l'accès en lecture via l'autorisation Activer le compte.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la façon de vérifier les autorisations WMI, consultez la section sécurité de la rubrique [afficher hors connexion les fichiers journaux](../logs/view-offline-log-files.md).  
  
-   Autorisation en lecture sur le dossier qui contient les journaux des erreurs. Par défaut, l’erreur journaux sont situés dans le chemin d’accès suivant (où \< *lecteur >* représente le lecteur où vous avez installé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et \< *InstanceName*> est le nom de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) :  
  
     **\<Lecteur > : \Program Files\Microsoft SQL Server\MSSQL11** **.\< Nom_instance > \MSSQL\Log**  
  
 Si vous vous connectez via un pare-feu, vérifiez qu'une exception est définie dans le pare-feu pour WMI sur les ordinateurs cibles distants. Pour plus d’informations, consultez [connexion à WMI à distance avec Windows Vista](http://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>Voir aussi  
 [Sqlerrorlogevent, classe](sqlerrorlogevent-class.md)   
 [Afficher les fichiers journaux hors connexion](../logs/view-offline-log-files.md)  
  
  
