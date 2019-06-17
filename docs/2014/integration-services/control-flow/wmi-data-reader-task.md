---
title: Lecteur de données WMI, tâche | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Data Reader task [Integration Services]
ms.assetid: dae57067-0275-4ac3-8f34-1b9d169f1112
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 12340ae2ba13bf6219cf9940a56eeaa8b995f3e8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62829492"
---
# <a name="wmi-data-reader-task"></a>Tâche Lecteur de données WMI
  La tâche Lecteur de données WMI exécute des requêtes au moyen du langage de requête WMI (Windows Management Instrumentation) qui retournent des informations à partir de WMI sur un système informatique. Vous pouvez utiliser la tâche Lecteur de données WMI pour effectuer les opérations suivantes :  
  
-   Interrogation des journaux des événements Windows sur un ordinateur local ou distant et écriture des informations dans un fichier ou une variable.  
  
-   Obtention d'informations sur la présence, l'état ou les propriétés de composants matériels, puis utilisation de ces informations pour déterminer si d'autres tâches du flux de contrôle doivent être exécutées.  
  
-   Obtention d'une liste d'applications et détermination de la version de chaque application installée.  
  
 Vous pouvez configurer la tâche Lecteur de données WMI de plusieurs manières :  
  
-   Spécifiez le gestionnaire de connexions WMI à utiliser.  
  
-   Spécifiez la source de la requête WQL. La requête peut être stockée dans une propriété de tâche ou en dehors de la tâche, dans une variable ou un fichier.  
  
-   Définissez le format des résultats de requêtes WQL. La tâche prend en charge un format de table, de paire nom/valeur de propriété ou de valeur de propriété.  
  
-   Spécifiez la destination de la requête. La destination peut être une variable ou un fichier.  
  
-   Indiquez si les résultats sont ajoutés à la destination de la requête ou si celle-ci est remplacée ou conservée.  
  
 Si la source ou la destination est un fichier, la tâche Lecteur de données WMI utilise un gestionnaire de connexions de fichiers pour se connecter au fichier. Pour plus d'informations, consultez [Flat File Connection Manager](../connection-manager/file-connection-manager.md).  
  
 La tâche Lecteur de données WMI utilise un gestionnaire de connexions WMI pour se connecter au serveur à partir duquel elle lit les informations WMI. Pour plus d'informations, consultez [WMI Connection Manager](../connection-manager/wmi-connection-manager.md).  
  
## <a name="wql-query"></a>Requête WQL  
 WQL est un dialecte de SQL avec des extensions qui permettent de prendre en charge la notification d'événement WMI et d'autres fonctionnalités spécifiques à WMI. Pour plus d'informations sur WQL, consultez la documentation Windows Management Instrumentation dans [MSDN Library](https://go.microsoft.com/fwlink/?linkid=7022).  
  
> [!NOTE]  
>  Les classes WMI varient d'une version de Windows à l'autre.  
  
 La requête WQL suivante retourne des entrées dans le journal des événements d'application.  
  
```  
SELECT * FROM Win32_NTLogEvent WHERE LogFile = 'Application' AND (SourceName='SQLISService' OR SourceName='SQLISPackage') AND TimeGenerated > '20050117'  
```  
  
 La requête WQL suivante retourne des informations sur les disques logiques.  
  
```  
SELECT FreeSpace, DeviceId, Size, SystemName, Description FROM Win32_LlogicalDisk  
```  
  
 La requête WQL suivante retourne une liste des mises à jour QFE (Quick Fix Engineering) du système d'exploitation.  
  
```  
Select * FROM Win32_QuickFixEngineering  
```  
  
## <a name="custom-logging-messages-available-on-the-wmi-data-reader-task"></a>Messages de journalisation personnalisés disponibles dans la tâche Lecteur de données WMI  
 Le tableau suivant répertorie les entrées de journal personnalisées de la tâche Lecteur de données WMI. Pour plus d’informations, consultez [Journalisation d’Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../custom-messages-for-logging.md).  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`WMIDataReaderGettingWMIData`|Indique que la tâche a commencé la lecture des données WMI.|  
|`WMIDataReaderOperation`|Indique la requête WQL que la tâche a exécutée.|  
  
## <a name="configuration-of-the-wmi-data-reader-task"></a>Configuration de la tâche Lecteur de données WMI  
 Vous pouvez définir les propriétés par programmation ou par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche Lecteur de données WMI &#40;page Options WMI&#41;](../wmi-data-reader-task-editor-wmi-options-page.md)  
  
-   [Page Expressions](../expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition par programmation de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiDataReaderTask.WmiDataReaderTask>  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches Integration Services](integration-services-tasks.md)   
 [Flux de contrôle](control-flow.md)  
  
  
