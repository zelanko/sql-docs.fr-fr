---
title: "&#201;diteur de t&#226;che Lecteur de donn&#233;es WMI (page Options WMI) | Microsoft Docs"
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
  - "sql13.dts.designer.wmidatareadertask.wmiquery.f1"
helpviewer_keywords: 
  - "Éditeur de tâche Lecteur de données WMI"
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
caps.latest.revision: 40
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# &#201;diteur de t&#226;che Lecteur de donn&#233;es WMI (page Options WMI)
  Utilisez la page **Options WMI** de la boîte de dialogue **Éditeur de tâche Lecteur de données WMI** pour définir la source de la requête WQL (Windows Management Instrumentation Query Language) et la destination du résultat de la requête.  
  
 Pour en savoir plus sur cette tâche, consultez [WMI Data Reader Task](../../integration-services/control-flow/wmi-data-reader-task.md). Pour plus d’informations sur la requête WQL (WMI Query Language), consultez la rubrique [Querying with WQL](http://go.microsoft.com/fwlink/?LinkId=79045) (Interrogation avec WQL) de la documentation de Windows Management Instrumentation, dans MSDN Library.  
  
## Options statiques  
 **WMIConnectionName**  
 Sélectionnez un gestionnaire de connexions WMI dans la liste ou cliquez sur \<**Nouvelle connexion WMI...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [Gestionnaire de connexions WMI](../../integration-services/connection-manager/wmi-connection-manager.md), [Éditeur du gestionnaire de connexions WMI](../../integration-services/connection-manager/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Sélectionnez le type de la source de la requête WQL que la tâche exécute. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Entrée directe**|Définit la source d'une requête WQL. Si vous sélectionnez cette valeur, l'option dynamique **WQLQuerySourceType**s'affiche.|  
|**Connexion de fichiers**|Sélectionnez un fichier qui contient la requête WQL. Si vous sélectionnez cette valeur, l'option dynamique **WQLQuerySourceType**s'affiche.|  
|**Variable**|Définissez la source dans une variable qui définit la requête WQL. Si vous sélectionnez cette valeur, l'option dynamique **WQLQuerySourceType**s'affiche.|  
  
 **OutputType**  
 Indiquez si la sortie doit être une table de données, une valeur de propriété ou un nom et une valeur de propriété.  
  
 **OverwriteDestination**  
 Indique s'il faut conserver ou remplacer les données d'origine dans le fichier ou la variable de destination, ou leur ajouter des données.  
  
 **DestinationType**  
 Sélectionnez le type de la destination de la requête WQL que la tâche exécute. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Connexion de fichiers**|Sélectionnez un fichier pour y enregistrer le résultat de la requête WQL. Cette valeur affiche l'option dynamique **DestinationType**.|  
|**Variable**|Définissez la variable de stockage du résultat de la requête WQL. Cette valeur affiche l'option dynamique **DestinationType**.|  
  
## Options dynamiques WQLQuerySourceType  
  
### WQLQuerySourceType = Entrée directe  
 **WQLQuerySource**  
 Fournissez une requête ou cliquez sur le bouton de sélection (...) et entrez une requête en utilisant la boîte de dialogue **Requête WQL**.  
  
### WQLQuerySourceType = Connexion de fichiers  
 **WQLQuerySource**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### WQLQuerySourceType = Variable  
 **WQLQuerySource**  
 Sélectionnez une variable dans la liste ou cliquez sur \<**Nouvelle variable…**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Ajouter une variable](../Topic/Add%20Variable.md)  
  
## Options dynamiques DestinationType  
  
### DestinationType = Connexion de fichiers  
 **Destination**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### DestinationType = Variable  
 **Destination**  
 Sélectionnez une variable dans la liste ou cliquez sur \<**Nouvelle variable…**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Ajouter une variable](../Topic/Add%20Variable.md)  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche Lecteur de données WMI &#40;page Général&#41;](../../integration-services/control-flow/wmi-data-reader-task-editor-general-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)   
 [Tâche Observateur d'événement WMI](../../integration-services/control-flow/wmi-event-watcher-task.md)  
  
  