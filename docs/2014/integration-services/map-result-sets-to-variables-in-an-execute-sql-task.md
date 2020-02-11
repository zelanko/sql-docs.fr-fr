---
title: Mapper des ensembles de résultats à des variables dans une tâche d’exécution SQL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- result sets [Integration Services]
- mapping result sets to variables [Integration Services]
- variables [Integration Services], mapping result sets to
ms.assetid: f76738b6-dc75-4ff9-a3dd-8b083d8e410e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 995afe55c1cd1b7d925c9267ba5dfa3aed038358
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057756"
---
# <a name="map-result-sets-to-variables-in-an-execute-sql-task"></a>Mapper des ensembles de résultats à des variables dans une tâche d’exécution SQL
  Cette rubrique décrit comment créer un mappage entre un jeu de résultats et une variable dans une tâche d'exécution SQL. Le mappage d'un jeu de résultats à une variable rend le jeu de résultats disponible aux autres éléments du package. Par exemple, un script dans une tâche de script peut lire la variable, puis utiliser les valeurs du jeu de résultats ou une source XML pour consommer le jeu de résultats stocké dans une variable. Si le jeu de résultats est généré par un package parent, il est possible de le rendre disponible à un package enfant appelé par une tâche d'exécution de package en mappant le jeu de résultats à une variable dans le package parent, puis en créant une configuration de variable de package parent dans le package enfant pour stocker la valeur de la variable parent.  
  
 Pour obtenir une description des différents types de jeux de résultats et les types de données de variable que vous pouvez mapper aux jeux de résultats, consultez [Ensembles de résultats dans la tâche d’exécution SQL](control-flow/execute-sql-task.md).  
  
### <a name="to-map-a-result-set-to-a-variable"></a>Pour mapper un ensemble de résultats à une variable  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans **Explorateur de solutions**, double-cliquez sur le package pour l’ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de contrôle** .  
  
4.  Si le package ne contient pas déjà une tâche d'exécution SQL, ajoutez-en une au flux de contrôle du package. Pour plus d’informations, consultez [Ajouter ou supprimer une tâche ou un conteneur dans un workflow de contrôle](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  .  
  
5.  Double-cliquez sur la tâche d'exécution SQL.  
  
6.  Dans la boîte de dialogue **Éditeur de tâche d’exécution SQL** , dans la page **Général** , sélectionnez le type de jeu de résultats **Ligne unique**, **Ensemble de résultats complet**ou **XML** .  
  
     Pour obtenir une description des jeux de résultats, consultez [Ensembles de résultats dans la tâche d’exécution SQL](result-sets-in-the-execute-sql-task.md).  
  
7.  Cliquez sur **Ensemble de résultats**.  
  
8.  Pour ajouter un mappage d’un jeu de résultats, cliquez sur **Ajouter**.  
  
9. Dans la liste **Nom de variable** , sélectionnez une variable ou créez-en une. Pour plus d’informations, consultez [Ajouter, supprimer, modifier l’étendue de la variable définie par l’utilisateur dans un package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md).  
  
     Pour obtenir une description des types de données de variable que vous pouvez mapper aux jeux de résultats, consultez [Ensembles de résultats dans la tâche d’exécution SQL](result-sets-in-the-execute-sql-task.md).  
  
     Pour plus d’informations sur la façon de mapper une variable à une colonne unique et plusieurs variables de carte à plusieurs colonnes, consultez la section **Remplissage d’une variable avec un jeu de résultats** dans [Ensembles de résultats dans la tâche d’exécution SQL](control-flow/execute-sql-task.md).  
  
10. Dans la liste **Nom de résultat** , éventuellement, modifiez le nom du jeu de résultats.  
  
     En général vous pouvez utiliser le nom de colonne comme nom de jeu de résultats, ou vous pouvez utiliser la position ordinale de la colonne dans la liste de colonnes en tant que jeu de résultats. La possibilité d'utiliser un nom de colonne comme nom du jeu de résultats dépend du fournisseur que la tâche a été configurée pour utiliser. Tous les fournisseurs ne rendent pas les noms de colonnes disponibles.  
  
11. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de requêtes SQL, tâche](control-flow/execute-sql-task.md)   
 [Jeux de résultats dans la tâche d’exécution SQL](result-sets-in-the-execute-sql-task.md)   
 [Tâche d’exécution de package](control-flow/execute-package-task.md)   
 [Configurations du package](../../2014/integration-services/package-configurations.md)   
 [Créer des configurations de package](../../2014/integration-services/create-package-configurations.md)   
 [Utiliser les valeurs des variables et des paramètres dans un package enfant](../../2014/integration-services/use-the-values-of-variables-and-parameters-in-a-child-package.md)   
 [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md)  
  
  
