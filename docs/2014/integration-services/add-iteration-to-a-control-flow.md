---
title: Ajouter une itération à un flux de contrôle | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- repeating workflows
- adding iterations
- control flow [Integration Services], iterations
- expressions [Integration Services], control flow
- iterations [Integration Services]
- For Loop containers
ms.assetid: eb3a7494-88ae-4165-9d0f-58715eb1734a
caps.latest.revision: 42
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5fb691bb954b463e584cf56527b8b87b0662c6f1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273415"
---
# <a name="add-iteration-to-a-control-flow"></a>Ajouter une itération à un flux de contrôle
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] inclut le conteneur de boucles For, élément de flux de contrôle qui permet de facilement inclure un bouclage assurant la répétition conditionnelle d’un flux de contrôle dans un package. Pour plus d’informations, consultez [Conteneur de boucles For](control-flow/for-loop-container.md).  
  
 Le conteneur de boucles For évalue une condition à chaque itération de la boucle et s'arrête lorsque la condition est fausse. Il inclut des expressions pour l'initialisation de la boucle, la spécification de la condition d'évaluation qui arrête l'exécution du flux de contrôle répété et l'assignation d'une valeur à une expression qui met à jour la valeur par rapport à laquelle la condition d'évaluation est comparée. Vous devez fournir une condition d'évaluation, mais les expressions d'initialisation et d'assignation sont facultatives.  
  
 Le conteneur de boucles For n'offre aucune fonctionnalité ; il ne fournit que la structure dans laquelle vous créez le flux de contrôle répété. Pour fournir une fonctionnalité de conteneur, vous devez inclure au moins une tâche dans le conteneur de boucles For. Pour plus d’informations, consultez [Tâches Integration Services](control-flow/integration-services-tasks.md).  
  
 Le conteneur de boucles For peut inclure un flux de contrôle avec plusieurs tâches, ainsi que d'autres conteneurs. Que vous ajoutiez des tâches et des conteneurs à un conteneur de boucles For ou à un package, l'opération est la même, sauf que vous faites glisser les tâches et les conteneurs vers le conteneur de boucles For plutôt que vers le package. Si le conteneur de boucles For contient plusieurs tâches ou conteneurs, vous pouvez les connecter à l'aide de contraintes de précédence, tout comme dans un package. Pour plus d’informations, consultez [Contraintes de précédence](control-flow/precedence-constraints.md).  
  
## <a name="using-expressions-in-for-loop-configuration"></a>Utilisation d'expressions dans une configuration de boucle For  
 Lorsque vous configurez le conteneur de boucles For en spécifiant une condition d'évaluation, une valeur d'initialisation ou une valeur d'assignation, vous pouvez utiliser des littéraux ou des expressions.  
  
 Les expressions peuvent inclure des variables. Les variables présentent l'avantage de pouvoir être mises à jour au moment de l'exécution, ce qui rend les packages plus flexibles et plus faciles à gérer. La longueur maximale d'une expression est limitée à 4 000 caractères.  
  
 Lorsque vous spécifiez une variable dans une expression, vous devez préfixer le nom de la variable avec le signe arobase (@). Par exemple, pour une variable nommée `Counter`, entrez @Counter dans l’expression qui utilise le conteneur de boucles for. Si vous incluez la propriété d'espace de noms dans la variable, vous devez placer la variable et l'espace de noms entre crochets. Par exemple, pour un `Counter` variable dans le `MyNamespace` espace de noms, type [@MyNamespace::Counter].  
  
 Les variables utilisées par le conteneur de boucles For doivent être définies dans la portée du conteneur de boucles For ou dans la portée d'un conteneur situé plus haut dans la hiérarchie de conteneurs de package. Par exemple, un conteneur de boucles For peut utiliser des variables définies dans sa portée et également des variables définies dans la portée du package. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md) et [Utiliser des variables dans des packages](../../2014/integration-services/use-variables-in-packages.md).  
  
 La grammaire d'expression [!INCLUDE[ssIS](../includes/ssis-md.md)] fournit un ensemble complet d'opérateurs et de fonctions pour l'implémentation d'expressions complexes utilisées pour l'évaluation, l'initialisation ou l'assignation. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).  
  
### <a name="to-implement-a-for-loop-container-in-a-control-flow"></a>Pour implémenter un conteneur de boucles For dans un flux de contrôle  
  
1.  Ajoutez le conteneur de boucles For au package. Pour plus d’informations, consultez [ajouter ou supprimer une tâche ou un conteneur dans un flux de contrôle](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  .  
  
2.  Ajoutez des tâches et des conteneurs au conteneur de boucles For. Pour plus d’informations, consultez [ajouter ou supprimer une tâche ou un conteneur dans un flux de contrôle](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  .  
  
3.  Connectez les tâches et les conteneurs du conteneur de boucles For à l'aide de contraintes de précédence. Pour plus d’informations, consultez [Connecter des tâches et des conteneurs à l’aide d’une contrainte de précédence par défaut](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md).  
  
4.  Configurez le conteneur de boucles For. Pour plus d’informations, consultez [Configurer un conteneur de boucles For](../../2014/integration-services/configure-a-for-loop-container.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter ou supprimer une tâche ou un conteneur dans un flux de contrôle](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [Groupe ou dissocier des composants](group-or-ungroup-components.md)   
 [Connecter des tâches et des conteneurs à l’aide d’une contrainte de précédence par défaut](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [Ajouter une énumération à un flux de contrôle](../../2014/integration-services/add-enumeration-to-a-control-flow.md)   
 [Flux de contrôle](control-flow/control-flow.md)  
  
  
