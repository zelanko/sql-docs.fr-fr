---
title: Suivi
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 45823fc8-723a-49f2-9a11-94d241245cfd
author: lrtoyou1223
ms.author: lle
manager: erikre
ms.openlocfilehash: fe2c0096aecd1296f7f10ce90a1acae706f3f3af
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727848"
---
# <a name="tracing-master-data-services"></a>Suivi (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Le fichier Web.config contient une section de suivi, comme indiqué ci-dessous. Cette section est une nouveauté dans [!INCLUDE[ssSQL15](../includes/sssql15-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]  
  
```  
<sources>  
      <!-- Adjust the switch value to control the types of messages that should be logged.   
           https://msdn.microsoft.com/library/system.diagnostics.sourcelevels  
           Use the a switchValue of Verbose to generate a full log. Please be aware that   
           the trace file can get quite large very quickly -->  
      <source name="MDS" switchType="System.Diagnostics.SourceSwitch" switchValue="Warning, ActivityTracing">  
        <listeners>  
          <!-- Set a directory path where the service account you chose while setting up Master Data Services has read and write privileges.  
               Default path is Logs in WebApplication folder, for example C:\Program Files\Microsoft SQL Server\130\Master Data Services\WebApplication  
               New log file will be created every day or every 10 mb.  
               When directory size hits the 200mb limitation, the oldest file will be deleted.-->  
          <add name="FileTraceListener"  
               type="Microsoft.MasterDataServices.Core.Logging.FileTraceListener, Microsoft.MasterDataServices.Core"   
               initializeData="DirectoryPath = Logs; FileSizeInMb = 10; MaxDirectorySizeInMb = 200"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
  
```  
  
 Voici le comportement de suivi par défaut.  
  
-   Le suivi est activé pour les messages d’avertissement et de suivi d’activités.  
  
     Pour plus d’informations, voir [SourceLevels, énumération](https://msdn.microsoft.com/library/system.diagnostics.sourcelevels).  
  
-   Les journaux sont enregistrés dans le dossier Logs sous le dossier WebApplication. L’emplacement par défaut est le suivant : C:\Program Files\Microsoft SQL Server\130\Master Data Services\WebApplication\Logs.  
  
-   Un fichier est créé quotidiennement ou tous les 10 Mo.  
  
-   Lorsque la taille du répertoire atteint 200 Mo, le journal le plus ancien est supprimé.  
  
-   Le journal est au format CSV. Le tableau qui suit décrit le format du journal.  
  
    |Élément|Description|  
    |-------------|-----------------|  
    |Time|Date de l’entrée de suivi.|  
    |CorrelationID|Un ID de corrélation est affecté à chaque demande. Tous les suivis déclenchés par la demande partagent le même ID de corrélation.<br /><br /> Lorsqu’une erreur se produit dans l’interface utilisateur, l’ID de corrélation apparaît dans le message d’erreur.|  
    |Opération|Nom de l’opération de demande. Si la demande est une demande de l’interface utilisateur Web, le nom de l’opération correspond à l’URL. Si la demande est une demande API, le nom de l’opération correspond au nom du service.|  
    |Level|Niveau de cette entrée de suivi.|  
    |Message|Corps du message de suivi.|  
  
## <a name="external-resources"></a>Ressources externes  
 Billet de blog intitulé [Troubleshooting Logging Improvement](https://go.microsoft.com/fwlink/p/?LinkId=615377)(en anglais) sur msdn.com.  
  
  
