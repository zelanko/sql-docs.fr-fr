---
title: "&#201;diteur de t&#226;che de service Web (page Sortie) | Microsoft Docs"
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
  - "sql13.dts.designer.webservicestask.output.f1"
helpviewer_keywords: 
  - "Éditeur de tâche de service Web"
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# &#201;diteur de t&#226;che de service Web (page Sortie)
  Utilisez la page **Sortie** de la boîte de dialogue **Éditeur de tâche de service Web** pour définir l’emplacement de stockage du résultat retourné par la méthode web.  
  
 Pour en savoir plus sur cette tâche, consultez [Tâche de service Web](../../integration-services/control-flow/web-service-task.md).  
  
## Options statiques  
 **OutputType**  
 Sélectionnez le type de stockage à utiliser pour stocker le résultat. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Connexion de fichiers**|Stocke le résultat dans un fichier. Cette valeur affiche l’option dynamique **Fichier**.|  
|**Variable**|Stocke le résultat dans une variable. Cette valeur affiche l’option dynamique **Variable**.|  
  
## Options dynamiques OutputType  
  
### OutputType = Connexion de fichiers  
 **Fichier**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### OutputType = Variable  
 **Variable**  
 Sélectionnez une variable dans la liste ou cliquez sur \<**Nouvelle variable…**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Ajouter une variable](../Topic/Add%20Variable.md)  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche de service Web &#40;page Général&#41;](../../integration-services/control-flow/web-service-task-editor-general-page.md)   
 [Éditeur de tâche de service Web &#40;page Entrée&#41;](../../integration-services/control-flow/web-service-task-editor-input-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
  