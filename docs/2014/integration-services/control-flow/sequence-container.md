---
title: Conteneur de séquences | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sequencecontainer.f1
helpviewer_keywords:
- Sequence container
- grouping control flows
- containers [Integration Services], Sequence
- subset control flow [Integration Services]
ms.assetid: 7731f91e-b8b3-4d96-a0d9-73f568547cb3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9769eddb7c10492f867395dfc1fa69b6b1260060
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85432696"
---
# <a name="sequence-container"></a>conteneur de séquences
  Le conteneur de séquences définit un flux de contrôle représentant un sous-ensemble du flux de contrôle du package. Les conteneurs de séquences regroupent le package en plusieurs flux de contrôle distincts contenant chacun un ou plusieurs conteneurs et tâches exécutés dans le flux de contrôle global du package.  
  
 Le conteneur de séquences peut inclure plusieurs tâches et d'autres conteneurs. L'ajout de tâches et de conteneurs à un conteneur de séquences est identique à l'ajout de ces éléments à un package. La seule différence est que vous faites glisser les tâches et les conteneurs dans le conteneur de séquences au lieu de les glisser dans le conteneur de package. Si le conteneur de séquences inclut plusieurs tâches ou conteneurs, vous pouvez les connecter à l'aide de contraintes de précédence de la même manière que dans un package. Pour plus d’informations, consultez [Contraintes de précédence](precedence-constraints.md).  
  
 L'utilisation d'un conteneur de séquences présente de nombreux avantages :  
  
-   Désactivation des groupes de tâches afin de concentrer le débogage du package sur un seul sous-ensemble de son flux de contrôle  
  
-   Centralisation de la gestion des propriétés de plusieurs tâches en définissant les propriétés sur un conteneur de séquences plutôt que sur les différentes tâches  
  
     Vous pouvez ainsi affecter la valeur `Disable` à la propriété `True` du conteneur de séquences afin de désactiver toutes les tâches et tous les conteneurs du conteneur de séquences.  
  
-   Attribution d'une étendue aux variables utilisées par un groupe de tâches et de conteneurs apparentés  
  
-   Regroupement de nombreuses tâches pour vous permettre de les gérer plus facilement, en réduisant et en développant le conteneur de séquences.  
  
     Vous pouvez aussi créer des groupes de tâches, qui peuvent être réduits et développés à partir de la zone **Groupe** . Cependant, la zone **Groupe** est une fonctionnalité disponible au moment de la conception qui ne contient aucune propriété et n’affiche aucun comportement au moment de l’exécution. Pour plus d’informations, consultez [Grouper ou dissocier des composants](../group-or-ungroup-components.md)  
  
-   Configurez un attribut de transaction sur le conteneur de séquences afin de définir une transaction pour un sous-ensemble du flux de contrôle du package. Ainsi, vous pouvez gérer les transactions de façon plus précise.  
  
     Par exemple, si un conteneur de séquences comprend deux tâches apparentées, l'une supprimant des données d'une table et l'autre insérant celles-ci dans une table, vous pouvez configurer une transaction de manière à ce que l'action de suppression soit annulée en cas d'échec de l'action d'insertion. Pour plus d’informations, consultez [Transactions Integration Services](../integration-services-transactions.md).  
  
## <a name="configuration-of-the-sequence-container"></a>Configuration du conteneur de séquences  
 Le conteneur de séquences ne possède pas d’interface utilisateur personnalisée et vous ne pouvez le configurer que dans la fenêtre **Propriétés** de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou par programmation.  
  
 Pour plus d’informations sur la définition par programmation de ces propriétés, consultez la documentation relative à la classe **T:Microsoft.SqlServer.Dts.Runtime.Sequence** dans le Guide du développeur.  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la définition des propriétés du composant dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], consultez [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter ou supprimer une tâche ou un conteneur dans un flux de contrôle](add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [Connecter des tâches et des conteneurs à l’aide d’une contrainte de précédence par défaut](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [Conteneurs Integration Services](integration-services-containers.md)  
  
  
