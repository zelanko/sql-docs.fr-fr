---
title: "T&#226;che Lecteur de donn&#233;es WMI | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.wmidatareadertask.f1"
helpviewer_keywords: 
  - "WQL [Integration Services]"
  - "Tâche Lecteur de données WMI [Integration Services]"
ms.assetid: dae57067-0275-4ac3-8f34-1b9d169f1112
caps.latest.revision: 49
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 49
---
# T&#226;che Lecteur de donn&#233;es WMI
  La tâche Lecteur de données WMI exécute des requêtes au moyen du langage de requête WMI (Windows Management Instrumentation) qui retournent des informations à partir de WMI sur un système informatique. Vous pouvez utiliser la tâche Lecteur de données WMI pour effectuer les opérations suivantes :  
  
-   Interrogation des journaux des événements Windows sur un ordinateur local ou distant et écriture des informations dans un fichier ou une variable.  
  
-   Obtention d'informations sur la présence, l'état ou les propriétés de composants matériels, puis utilisation de ces informations pour déterminer si d'autres tâches du flux de contrôle doivent être exécutées.  
  
-   Obtention d'une liste d'applications et détermination de la version de chaque application installée.  
  
 Vous pouvez configurer la tâche Lecteur de données WMI de plusieurs manières :  
  
-   Spécifiez le gestionnaire de connexions WMI à utiliser.  
  
-   Spécifiez la source de la requête WQL. La requête peut être stockée dans une propriété de tâche ou en dehors de la tâche, dans une variable ou un fichier.  
  
-   Définissez le format des résultats de requêtes WQL. La tâche prend en charge un format de table, de paire nom/valeur de propriété ou de valeur de propriété.  
  
-   Spécifiez la destination de la requête. La destination peut être une variable ou un fichier.  
  
-   Indiquez si les résultats sont ajoutés à la destination de la requête ou si celle-ci est remplacée ou conservée.  
  
 Si la source ou la destination est un fichier, la tâche Lecteur de données WMI utilise un gestionnaire de connexions de fichiers pour se connecter au fichier. Pour plus d'informations, consultez [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
 La tâche Lecteur de données WMI utilise un gestionnaire de connexions WMI pour se connecter au serveur à partir duquel elle lit les informations WMI. Pour plus d'informations, consultez [WMI Connection Manager](../../integration-services/connection-manager/wmi-connection-manager.md).  
  
## Requête WQL  
 WQL est un dialecte de SQL avec des extensions qui permettent de prendre en charge la notification d'événement WMI et d'autres fonctionnalités spécifiques à WMI. Pour plus d'informations sur WQL, consultez la documentation Windows Management Instrumentation dans [MSDN Library](http://go.microsoft.com/fwlink/?linkid=7022).  
  
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
  
## Messages de journalisation personnalisés disponibles dans la tâche Lecteur de données WMI  
 Le tableau suivant répertorie les entrées de journal personnalisées de la tâche Lecteur de données WMI. Pour plus d’informations, consultez [Journalisation Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../../integration-services/performance/custom-messages-for-logging.md).  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|**WMIDataReaderGettingWMIData**|Indique que la tâche a commencé la lecture des données WMI.|  
|**WMIDataReaderOperation**|Indique la requête WQL que la tâche a exécutée.|  
  
## Configuration de la tâche Lecteur de données WMI  
 Vous pouvez définir les propriétés par programmation ou par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche Lecteur de données WMI &#40;page Options WMI&#41;](../../integration-services/control-flow/wmi-data-reader-task-editor-wmi-options-page.md)  
  
-   [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition par programmation de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiDataReaderTask.WmiDataReaderTask>  
  
## Tâches associées  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Voir aussi  
 [Tâches Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flux de contrôle](../../integration-services/control-flow/control-flow.md)  
  
  