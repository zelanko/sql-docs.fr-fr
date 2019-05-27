---
title: Utiliser des Variables dans des Packages | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined variables [Integration Services]
- variables [Integration Services], use scenarios
- system variables [Integration Services]
ms.assetid: 7742e92d-46c5-4cc4-b9a3-45b688ddb787
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 96bfbf87789aa1d683b6368f210539a191f7ee95
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66054690"
---
# <a name="use-variables-in-packages"></a>Utiliser des variables dans des packages
  Les variables constituent un ajout souple et utile aux packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Elles permettent une communication entre les objets du package et entre les packages parents et enfants. Les variables peuvent également être utilisées dans les expressions et les scripts.  
  
## <a name="user-defined-variables-and-system-variables"></a>Variables définies par l'utilisateur et variables système  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fournit les variables système et prend en charge les variables définies par l'utilisateur. Quand vous créez un nouveau package, quand vous ajoutez un conteneur ou une tâche à un package ou quand vous créez un gestionnaire d'événements, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] inclut un ensemble de variables système pour le conteneur. Les variables système contiennent des informations utiles sur un package, conteneur, tâche ou gestionnaire d'événements. Par exemple, au moment de l’exécution, la variable système **MachineName** contient le nom de l’ordinateur sur lequel le package est exécuté et **StartTime** contient l’heure à laquelle le package a démarré son exécution. Les variables système sont en lecture seule. Pour plus d’informations, consultez [Variables système](system-variables.md).  
  
 Vous pouvez créer des variables définies par l'utilisateur et les utiliser ensuite dans des packages. Les variables définies par l’utilisateur peuvent être utilisées de diverses façons dans [!INCLUDE[ssIS](../includes/ssis-md.md)]: dans les scripts, les expressions utilisées par des contraintes de précédence, le conteneur de boucles For, la transformation de colonne dérivée, la transformation de fractionnement conditionnel et les expressions de propriété qui mettent à jour des valeurs de propriété.  
  
 Par exemple, vous pouvez utiliser une variable définie par l'utilisateur dans la condition d'évaluation pour le conteneur de boucles For. Vous pouvez également mapper la valeur de la collection de l'énumérateur dans un conteneur de boucles Foreach à une variable, et si une tâche d'exécution SQL utilise une instruction SQL paramétrable, vous pouvez mapper les paramètres de l'instruction à des variables. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md).  
  
## <a name="variables-usage-scenarios"></a>Scénarios d'utilisation de variables  
 Les variables sont utilisées de nombreuses manières différentes dans les packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Vous constaterez sans doute que le développement de package est limité tant que vous n'avez pas ajouté une variable définie par l'utilisateur à votre package pour mettre en œuvre la flexibilité et la gestion nécessaires à votre solution. En fonction du scénario, les variables système sont aussi couramment utilisées.  
  
 **Expressions de propriété** : les variables permettent de fournir des valeurs dans les expressions de propriété qui définissent les propriétés d’objets de package et de packages. Par exemple, l’expression `SELECT * FROM @varTableName` inclut la variable `varTableName` qui met à jour l’instruction SQL exécutée par une tâche d’exécution SQL. L’expression `DATEPART("d", GETDATE()) == 1? @[User::varPackageFirst]:@[User::varPackageOther]`met à jour le package exécuté par la tâche d’exécution de package en exécutant le package spécifié dans la variable `varPackageFirst` le premier jour du mois et en exécutant le package spécifié dans la variable `varPackageOther` les autres jours. Pour plus d’informations, consultez [Expressions de propriété dans des packages](expressions/use-property-expressions-in-packages.md).  
  
 **Expressions de flux de données** : les variables permettent de fournir des valeurs dans les expressions dont se servent les transformations de fractionnement conditionnel et de colonne dérivée pour remplir les colonnes ou diriger les lignes de données vers différentes sorties de transformation. Par exemple, l'expression `@varSalutation + LastName`concatène la valeur dans la variable `VarSalutation` et la colonne `LastName` . L’expression `Income < @HighIncome` dirige vers une sortie les lignes de données dans lesquelles la valeur de la colonne `Income` est inférieure à la valeur de la variable `HighIncome`. Pour plus d’informations, consultez [Transformation de colonne dérivée](data-flow/transformations/derived-column-transformation.md), [Transformation de fractionnement conditionnel](data-flow/transformations/conditional-split-transformation.md) et [Expressions Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).  
  
 **Expressions de contrainte de précédence** : elles fournissent les valeurs à utiliser dans des contraintes de précédence pour déterminer si un exécutable contraint s’exécute. Les expressions peuvent être utilisées avec un résultat d'exécution (succès, échec, achèvement de l'opération) ou à la place d'un résultat d'exécution. Par exemple, si l'expression `@varMax > @varMin` s'évalue à `true`, l'exécutable s'exécute. Pour plus d’informations, consultez [Ajouter des expressions aux contraintes de précédence](control-flow/precedence-constraints.md).  
  
 **Paramètres et codes de retour** : ils fournissent des valeurs aux paramètres d’entrée ou stockent les valeurs des paramètres de sortie et des codes de retour. Cette opération s'effectue en mappant les variables aux paramètres et aux valeurs de retour. Par exemple, si vous affectez à la variable `varProductId` la valeur 23 et que vous exécutez l’instruction SQL `SELECT * from Production.Product WHERE ProductID = ?`, la requête récupère le produit associé à la valeur `ProductID` 23. Pour plus d’informations, consultez [Tâche d’exécution de requêtes SQL](control-flow/execute-sql-task.md) et [Paramètres et codes de retour dans la tâche d’exécution SQL](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).  
  
 **Expressions de boucle For** : elles fournissent les valeurs à utiliser dans les expressions d’initialisation, d’évaluation et d’assignation de la boucle For. Par exemple, si la variable `varCount` a la valeur 2 et la variable `varMaxCount` la valeur 10 et que l’expression d’initialisation est `@varCount`, l’expression d’évaluation  `@varCount < @varMaxCount`et l’expression d’assignation `@varCount =@varCount +1`, la boucle se répète 8 fois. Pour plus d’informations, consultez [Conteneur de boucles For](control-flow/for-loop-container.md).  
  
 **Configurations de variable de package parent** : elles permettent de passer des valeurs des packages parents aux packages enfants. Les packages enfants peuvent accéder à des variables dans le package parent à l'aide de configurations de variable de package parent. Par exemple, si le package enfant doit utiliser la même date que le package parent, le package enfant peut définir une configuration de variable de package parent qui spécifie une variable définie par la fonction GETDATE dans le package parent. Pour plus d’informations, consultez [Tâche d’exécution de package](control-flow/execute-package-task.md) et [Configurations de package](../../2014/integration-services/package-configurations.md).  
  
 **Tâche de script et composant de script** : ils fournissent une liste de variables en lecture seule et en lecture/écriture à la tâche de script ou au composant de script, mettent à jour les variables en lecture/écriture dans le script, puis utilisent les valeurs mises à jour à l’intérieur ou à l’extérieur du script. Par exemple, dans le code `numberOfCars = CType(Dts.Variables("NumberOfCars").Value, Integer)`, la variable de script `numberOfCars` est mise à jour par la valeur dans la variable `NumberOfCars`. Pour plus d’informations, consultez [Utilisation de variables dans la tâche de script](control-flow/script-task.md).  
  
## <a name="configurations-and-variables"></a>Configurations et variables  
 Pour mettre à jour dynamiquement des variables, vous pouvez créer des configurations pour les variables, déployer les configurations dans le package, puis mettre à jour les valeurs de variable dans un fichier de configuration lorsque vous déployez les packages. À l'exécution, le package utilise les valeurs de variable mises à jour. Pour plus d’informations, consultez [Créer des configurations de package](../../2014/integration-services/create-package-configurations.md).  
  
### <a name="to-add-modify-and-delete-user-defined-variables"></a>Pour ajouter, modifier et supprimer des variables définies par l'utilisateur  
  
-   [Ajouter, supprimer, modifier l’étendue d’une variable définie par l’utilisateur dans un package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
-   [Définir les propriétés d’une variable définie par l’utilisateur](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md)  
  
  
