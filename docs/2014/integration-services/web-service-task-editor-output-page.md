---
title: Éditeur de tâche de service Web (page sortie) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.output.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 4b8dbb9847f3591d0f26a2dc7ca6e31f1b22da83
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972449"
---
# <a name="web-service-task-editor-output-page"></a>Éditeur de tâche de service Web (page Sortie)
  Utilisez la page **Sortie** de la boîte de dialogue **Éditeur de tâche de service Web** pour définir l’emplacement de stockage du résultat retourné par la méthode web.  
  
 Pour en savoir plus sur cette tâche, consultez [Tâche de service web](control-flow/web-service-task.md).  
  
## <a name="static-options"></a>Options statiques  
 **OutputType**  
 Sélectionnez le type de stockage à utiliser pour stocker le résultat. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Connexion de fichiers**|Stocke le résultat dans un fichier. Cette valeur affiche l’option dynamique **Fichier**.|  
|**Variable**|Stocke le résultat dans une variable. Cette valeur affiche l’option dynamique **Variable**.|  
  
## <a name="outputtype-dynamic-options"></a>Options dynamiques OutputType  
  
### <a name="outputtype--file-connection"></a>OutputType = Connexion de fichiers  
 **File**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou cliquez sur \<**New Connection...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="outputtype--variable"></a>OutputType = Variable  
 **Variable**  
 Sélectionnez une variable dans la liste ou cliquez sur \<**New Variable...**> pour créer une variable.  
  
 **Rubriques connexes :**  [Integration Services &#40;les variables de&#41; SSIS](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche de service Web &#40;page général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de tâche de service Web &#40;page d’entrée&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Page Expressions](expressions/expressions-page.md)  
  
  
