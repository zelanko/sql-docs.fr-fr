---
title: Éditeur de tâche de Service Web (Page entrée) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.input.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 93529c88-f540-47f2-a10a-12c87318ed6f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 29ca581697231a3aa70aa6f4342fcea3408d6c99
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926251"
---
# <a name="web-service-task-editor-input-page"></a>Éditeur de tâche de service Web (page Entrée)
  Utilisez la page **Entrée** de l' **Éditeur de tâche de service Web** pour définir le service Web, la méthode Web et les valeurs à fournir à la méthode Web comme entrée. Vous pouvez fournir les valeurs en tapant des chaînes directement dans la colonne Valeur ou en y sélectionnant des variables.  
  
 Pour en savoir plus sur cette tâche, consultez [Tâche de service web](control-flow/web-service-task.md).  
  
## <a name="options"></a>Options  
 **Service**  
 Sélectionnez un service Web dans la liste pour l'utiliser afin d'exécuter la méthode Web.  
  
 **Méthode**  
 Dans la liste, sélectionnez la méthode Web que doit exécuter la tâche.  
  
 **WebMethodDocumentation**  
 Entrez la description de la méthode web ou cliquez sur le bouton Parcourir **(...)** et entrez la description dans la boîte de dialogue **Documentation de la méthode Web**.  
  
 **Nom**  
 Contient la liste des noms des entrées dans la méthode Web.  
  
 **Type**  
 Indique le type des données des entrées.  
  
> [!NOTE]  
>  La tâche de service Web prend uniquement en charge les paramètres des types de données suivants : les types de primitives tels que les entiers et les chaînes ; les tableaux et séquences de types de primitives, ainsi que les énumérations.  
  
 **Variable**  
 Activez les cases à cocher afin d'utiliser des variables pour fournir les entrées.  
  
 **Valeur**  
 Si les cases Variable sont cochées, sélectionnez les variables dans la liste pour fournir les entrées ; sinon, tapez les valeurs à utiliser en guise d’entrées.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche de service Web &#40;page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de tâche de service Web &#40;page Sortie&#41;](../../2014/integration-services/web-service-task-editor-output-page.md)   
 [Page Expressions](expressions/expressions-page.md)  
  
  
