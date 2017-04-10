---
title: "&#201;diteur de t&#226;che Observateur d&#39;&#233;v&#233;nement WMI (page Options WMI) | Microsoft Docs"
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
  - "sql13.dts.designer.wmieventwatcher.wmiquery.f1"
helpviewer_keywords: 
  - "Éditeur de tâche Observateur d'événement WMI"
ms.assetid: 525f3de7-a021-4e52-9939-3a83c88f131a
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# &#201;diteur de t&#226;che Observateur d&#39;&#233;v&#233;nement WMI (page Options WMI)
  Utilisez la page **Options WMI** de la boîte de dialogue **Éditeur de tâche Observateur d'événement WMI** pour définir la source de la requête WQL (Windows Management Instrumentation Query Language) et le mode de réponse de la tâche Observateur d'événement WMI aux événements WMI (Microsoft Windows Instrumentation).  
  
 Pour en savoir plus sur cette tâche, consultez [WMI Event Watcher Task](../../integration-services/control-flow/wmi-event-watcher-task.md). Pour plus d’informations sur la requête WQL (WMI Query Language), consultez la rubrique [Querying with WQL](http://go.microsoft.com/fwlink/?LinkId=79045) (Interrogation avec WQL) de la documentation de Windows Management Instrumentation, dans MSDN Library.  
  
## Options statiques  
 **WMIConnectionName**  
 Sélectionnez un gestionnaire de connexions WMI dans la liste ou cliquez sur \<**Nouvelle connexion WMI...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [Gestionnaire de connexions WMI](../../integration-services/connection-manager/wmi-connection-manager.md), [Éditeur du gestionnaire de connexions WMI](../../integration-services/connection-manager/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Sélectionnez le type de la source de la requête WQL que la tâche exécute. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Entrée directe**|Définit la source d'une requête WQL. Cette valeur affiche l'option dynamique **WQLQuerySource**.|  
|**Connexion de fichiers**|Sélectionnez un fichier qui contient la requête WQL. Cette valeur affiche l'option dynamique **WQLQuerySource**.|  
|**Variable**|Définit la source dans une variable qui définit la requête WQL. Cette valeur affiche l'option dynamique **WQLQuerySource**.|  
  
 **ActionAtEvent**  
 Indiquez si l’événement WMI consigne l’événement et lance l’action [!INCLUDE[ssIS](../../includes/ssis-md.md)], ou consigne uniquement l’événement.  
  
 **AfterEvent**  
 Indiquez si la tâche aboutit ou échoue lorsqu'elle reçoit l'événement WMI, ou si elle continue d'observer l'occurrence de l'événement.  
  
 **ActionAtTimeout**  
 Indiquez si la tâche consigne la temporisation d'une requête WMI et déclenche un événement [!INCLUDE[ssIS](../../includes/ssis-md.md)] en réponse, ou si elle consigne uniquement la temporisation.  
  
 **AfterTimeout**  
 Indiquez si la tâche aboutit ou échoue en réponse à une temporisation, ou si elle continue d'observer l'occurrence d'une temporisation.  
  
 **NumberOfEvents**  
 Indiquez le nombre d'événements à observer.  
  
 **Délai d'expiration**  
 Indiquez le délai en secondes avant l'occurrence de l'événement. La valeur 0 indique qu'aucun délai n'a lieu.  
  
## Options dynamiques WQLQuerySource  
  
### WQLQuerySource = Entrée directe  
 **WQLQuerySource**  
 Fournissez une requête ou cliquez sur les points de suspension (…) et entrez une requête en utilisant la boîte de dialogue **Requête WQL**.  
  
### WQLQuerySource = Connexion de fichiers  
 **WQLQuerySource**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### WQLQuerySource = Variable  
 **WQLQuerySource**  
 Sélectionnez une variable dans la liste ou cliquez sur \<**Nouvelle variable…**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Ajouter une variable](../Topic/Add%20Variable.md)  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche Observateur d’événement WMI &#40;page Général&#41;](../../integration-services/control-flow/wmi-event-watcher-task-editor-general-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)   
 [Tâche Lecteur de données WMI](../../integration-services/control-flow/wmi-data-reader-task.md)  
  
  