---
title: "&#201;diteur de t&#226;che DDL d&#39;ex&#233;cution d&#39;Analysis Services (page DDL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.asexecuteddltask.ddl.f1"
helpviewer_keywords: 
  - "Éditeur de tâche DDL d'exécution de SQL Server Analysis Services"
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# &#201;diteur de t&#226;che DDL d&#39;ex&#233;cution d&#39;Analysis Services (page DDL)
  Utilisez la page **DDL** de la boîte de dialogue **Éditeur de tâche DDL d’exécution d’Analysis Services** pour spécifier une connexion à un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou à une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et fournir des informations sur la source des instructions de langage de définition de données (DDL).  
  
 Pour en savoir plus sur cette tâche, consultez [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md).  
  
## Options statiques  
 **Connexion**  
 Sélectionnez un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou un gestionnaire de connexions [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans la liste, ou cliquez sur \<**Nouvelle connexion**> et utilisez la boîte de dialogue **Ajout d’un gestionnaire de connexions Analysis Services** pour créer une connexion.  
  
 **Rubriques connexes :** [Référence de l'interface utilisateur de la boîte de dialogue Ajout d’un gestionnaire de connexions Analysis Services](../../integration-services/connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md), [Gestionnaire de connexions Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md)  
  
 **SourceType**  
 Spécifiez le type de source des instructions DDL. Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Entrée directe**|Définissez la source de l'instruction DDL enregistrée dans la zone de texte **SourceDirect** . Sélectionnez cette valeur pour afficher l'option dynamique de la section suivante.|  
|**Connexion de fichiers**|Définissez la source par un fichier qui contient l'instruction DDL. Sélectionnez cette valeur pour afficher l'option dynamique de la section suivante.|  
|**Variable**|Définissez la source par une variable. Sélectionnez cette valeur pour afficher l'option dynamique de la section suivante.|  
  
## Options dynamiques  
  
### SourceType = Entrée directe  
 **Source**  
 Tapez les instructions DDL ou cliquez sur le bouton représentant des points de suspension **(…)**, puis tapez les instructions dans la boîte de dialogue **Instructions DDL**.  
  
### SourceType = Connexion de fichiers  
 **Source**  
 Sélectionnez une connexion de fichiers dans la liste ou cliquez sur \<**Nouvelle connexion**> et utilisez la boîte de dialogue **Gestionnaire de connexions de fichiers** pour créer une connexion.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](../../integration-services/connection-manager/file-connection-manager.md)  
  
### SourceType = Variable  
 **Source**  
 Sélectionnez une variable dans la liste ou cliquez sur \<**Nouvelle variable**> et utilisez la boîte de dialogue **Ajouter une variable** pour créer une variable.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md)  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche DDL d’exécution Analysis Services &#40;page Général&#41;](../../integration-services/control-flow/analysis-services-execute-ddl-task-editor-general-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)   
 [Flux de contrôle](../../integration-services/control-flow/control-flow.md)   
 [Langage de script Analysis Services &#40;ASSL pour XMLA&#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [Référence XML for Analysis &#40;XMLA&#41;](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  