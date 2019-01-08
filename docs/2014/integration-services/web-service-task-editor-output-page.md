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
ms.openlocfilehash: ce05c73dadd133bafcea0f9bd505868b9dd0dc65
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52542651"
---
# <a name="web-service-task-editor-output-page"></a>Éditeur de tâche de service Web (page Sortie)
  Utilisez la page **Sortie** de la boîte de dialogue **Éditeur de tâche de service Web** pour définir l’emplacement de stockage du résultat retourné par la méthode web.  
  
 Pour en savoir plus sur cette tâche, consultez [Tâche de service Web](control-flow/web-service-task.md).  
  
## <a name="static-options"></a>Options statiques  
 **OutputType**  
 Sélectionnez le type de stockage à utiliser pour stocker le résultat. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Connexion de fichiers**|Stocke le résultat dans un fichier. Cette valeur affiche l’option dynamique **Fichier**.|  
|**Variable**|Stocke le résultat dans une variable. Cette valeur affiche l’option dynamique **Variable**.|  
  
## <a name="outputtype-dynamic-options"></a>Options dynamiques OutputType  
  
### <a name="outputtype--file-connection"></a>OutputType = Connexion de fichiers  
 **Fichier**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions file](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="outputtype--variable"></a>OutputType = Variable  
 **Variable**  
 Sélectionnez une variable dans la liste ou cliquez sur \<**Nouvelle variable...**> pour en créer une.  
  
 **Rubriques connexes :**  [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [ajouter une Variable](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche de service Web &#40;page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de tâche de service Web &#40;page Entrée&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Page Expressions](expressions/expressions-page.md)  
  
  
