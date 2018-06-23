---
title: Ajouter une énumération à un flux de contrôle | Documents Microsoft
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adding enumerations
- Foreach Loop containers
- control flow [Integration Services], enumerations
- repeating workflows
- enumerations [Integration Services]
ms.assetid: f212b5fb-3cc4-422e-9b7c-89eb769a812a
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 10d30541be42331b544882f8a8b85f75db7f230d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045009"
---
# <a name="add-enumeration-to-a-control-flow"></a>Ajouter une énumération à un flux de contrôle
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] inclut le conteneur de boucles Foreach, un élément de flux de contrôle qui permet de facilement inclure une construction de boucle énumérant les fichiers et objets du flux de contrôle d’un package. Pour plus d’informations, consultez [Conteneur de boucles Foreach](control-flow/foreach-loop-container.md).  
  
 Le conteneur de boucles Foreach n'offre aucune fonctionnalité ; il ne fournit que la structure dans laquelle vous créez le flux de contrôle répété, spécifiez un type d'énumérateur et configurez l'énumérateur. Pour fournir une fonctionnalité de conteneur, vous devez inclure au moins une tâche dans le conteneur de boucles Foreach. Pour plus d’informations, consultez [Tâches Integration Services](control-flow/integration-services-tasks.md).  
  
 Le conteneur de boucles Foreach peut inclure un flux de contrôle avec plusieurs tâches, ainsi que d'autres conteneurs. Que vous ajoutiez des tâches et des conteneurs à un conteneur de boucles Foreach ou à un package, l'opération est la même, sauf que vous faites glisser les tâches et les conteneurs vers le conteneur de boucles Foreach plutôt que vers le package. Si le conteneur de boucles Foreach contient plusieurs tâches ou conteneurs, vous pouvez les connecter à l'aide de contraintes de précédence, tout comme dans un package. Pour plus d’informations, consultez [Contraintes de précédence](control-flow/precedence-constraints.md).  
  
### <a name="to-implement-a-foreach-loop-container-in-a-control-flow"></a>Pour implémenter un conteneur de boucles Foreach dans un flux de contrôle  
  
1.  Ajoutez le conteneur de boucles Foreach au package. Pour plus d’informations, consultez [ajouter ou supprimer une tâche ou un conteneur dans un flux de contrôle](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  .  
  
2.  Ajoutez des tâches et des conteneurs au conteneur de boucles Foreach. Pour plus d’informations, consultez [ajouter ou supprimer une tâche ou un conteneur dans un flux de contrôle](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  .  
  
3.  Connectez les tâches et les conteneurs du conteneur de boucles Foreach à l'aide de contraintes de précédence. Pour plus d’informations, consultez [Connecter des tâches et des conteneurs à l’aide d’une contrainte de précédence par défaut](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md).  
  
4.  Configurez le conteneur de boucles Foreach. Pour plus d’informations, consultez [Configurer un conteneur de boucles Foreach](../../2014/integration-services/configure-a-foreach-loop-container.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter ou supprimer une tâche ou un conteneur dans un flux de contrôle](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [Groupe ou dissocier des composants](group-or-ungroup-components.md)   
 [Contraintes de précédence](control-flow/precedence-constraints.md)   
 [Ajouter une itération à un flux de contrôle](add-iteration-to-a-control-flow.md)   
 [Flux de contrôle](control-flow/control-flow.md)  
  
  