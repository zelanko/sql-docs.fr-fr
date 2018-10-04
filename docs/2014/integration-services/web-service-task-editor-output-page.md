---
title: Éditeur de tâche de Service Web (Page sortie) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.output.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2e2a0c1639352b8c5aaad9be4bd6740eceacb6cf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48132009"
---
# <a name="web-service-task-editor-output-page"></a>Éditeur de tâche de service Web (page Sortie)
  Utilisez la page **Sortie** de la boîte de dialogue **Éditeur de tâche de service Web** pour définir l’emplacement de stockage du résultat retourné par la méthode web.  
  
 Pour en savoir plus sur cette tâche, consultez [Tâche de service Web](control-flow/web-service-task.md).  
  
## <a name="static-options"></a>Options statiques  
 **OutputType**  
 Sélectionnez le type de stockage à utiliser pour stocker le résultat. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Connexion de fichiers**|Stocke le résultat dans un fichier. Cette valeur affiche l’option dynamique **Fichier**.|  
|**Variable**|Stocke le résultat dans une variable. Cette valeur affiche l’option dynamique **Variable**.|  
  
## <a name="outputtype-dynamic-options"></a>Options dynamiques OutputType  
  
### <a name="outputtype--file-connection"></a>OutputType = Connexion de fichiers  
 **Fichier**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour en créer un.  
  
 **Rubriques connexes :** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="outputtype--variable"></a>OutputType = Variable  
 **Variable**  
 Sélectionnez une variable dans la liste ou cliquez sur \<**Nouvelle variable...**> pour en créer une.  
  
 **Rubriques connexes :**  [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche de Service Web &#40;Page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de tâche de Service Web &#40;Page d’entrée&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Page Expressions](expressions/expressions-page.md)  
  
  
