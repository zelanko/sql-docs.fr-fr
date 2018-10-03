---
title: Variables Integration Services (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], passing between packages
- user-defined variables [Integration Services]
- scope [Integration Services]
- system variables [Integration Services]
- variables [Integration Services]
- variables [Integration Services], about variables
- values [Integration Services]
ms.assetid: c1e81ad6-628b-46d4-9b09-d2866517b6ca
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5b30ae5c49ec66b5612e1472c896084ebb92991d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069739"
---
# <a name="integration-services-ssis-variables"></a>Variables Integration Services (SSIS)
  Les variables stockent des valeurs qu'un package [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et ses conteneurs, tâches et gestionnaires d'événements peuvent utiliser au moment de l'exécution. Les scripts de la tâche de script et du composant Script peuvent également utiliser des variables. Les contraintes de précédence qui séquencent les tâches et les conteneurs dans un flux de travail peuvent utiliser des variables lorsque leurs définitions de contraintes incluent des expressions.  
  
 Vous pouvez utiliser des variables dans des packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pour les opérations suivantes :  
  
-   Mise à jour de propriétés d'éléments de package au moment de l'exécution. Par exemple, vous pouvez dynamiquement définir le nombre d'exécutables simultanés qu'un conteneur de boucles Foreach autorise.  
  
-   Inclusion d'une table de recherche en mémoire. Par exemple, un package peut exécuter une tâche d'exécution SQL qui charge une variable avec des valeurs de données.  
  
-   Chargement de variables avec des valeurs de données, puis utilisation de ces variables pour spécifier une condition de recherche dans une clause WHERE. Par exemple, le script dans une tâche de script peut mettre à jour la valeur d'une variable qui est utilisée par une instruction Transact-SQL dans une tâche d'exécution SQL.  
  
-   Chargement d'une variable avec un entier, puis utilisation de la valeur pour contrôler le bouclage au sein d'un flux de contrôle de package. Par exemple, vous pouvez utiliser une variable dans l'expression d'évaluation d'un conteneur de boucles For pour contrôler l'itération.  
  
-   Remplissage de valeurs de paramètres pour des instructions Transact-SQL au moment de l'exécution. Par exemple, un package peut exécuter une tâche d'exécution SQL, puis utiliser des variables pour définir dynamiquement les paramètres d'une instruction Transact-SQL.  
  
-   Création d'expressions qui incluent des valeurs de variables. Par exemple, la transformation de colonnes dérivées peut remplir une colonne avec le résultat obtenu suite à la multiplication d'une valeur de variable par une valeur de colonne.  
  
## <a name="system-and-user-defined-variables"></a>Variables système et variables définies par l'utilisateur  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] prend en charge deux types de variables : les variables définies par l’utilisateur et les variables système. Les variables définies par l'utilisateur sont définies par les développeurs de packages, tandis que les variables système sont définies par [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Vous pouvez créer autant de variables définies par l'utilisateur qu'un package l'exige, mais vous ne pouvez pas créer de variables système supplémentaires.  
  
 Toutes les variables (système et définies par l'utilisateur) peuvent être utilisées dans les liaisons de paramètres que la tâche d'exécution SQL utilise pour mapper des variables à des paramètres dans des instructions SQL. Pour plus d’informations, consultez [Tache d’exécution de requêtes SQL](control-flow/execute-sql-task.md) et [Paramètres et codes de retour dans la tâche d’exécution SQL](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).  
  
> [!NOTE]  
>  Les noms des variables définies par l’utilisateur et des variables système respectent la casse.  
  
 Vous pouvez créer des variables définies par l’utilisateur pour tous les types de conteneurs [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] : packages, conteneurs de boucles Foreach, conteneurs de boucles For, conteneurs de séquences, tâches et gestionnaires d’événements. Les variables définies par l'utilisateur sont des membres de la collection Variables du conteneur.  
  
 Si vous créez le package à l'aide du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , vous pouvez afficher les membres de la collection Variables dans le dossier **Variables** sous l'onglet **Explorateur de package** du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] . Les dossiers répertorient les variables définies par l'utilisateur et les variables système.  
  
 Vous pouvez configurer les variables définies par l'utilisateur de plusieurs manières :  
  
-   Spécifiez un nom et une description pour la variable.  
  
-   Spécifiez un espace de noms pour la variable.  
  
-   Indiquez si la variable déclenche un événement lorsque sa valeur change.  
  
-   Indiquez si la variable est en lecture seule ou accessible en lecture/écriture.  
  
-   Utilisez le résultat de l'évaluation d'une expression pour définir la valeur de la variable.  
  
-   Créez la variable dans la portée du package ou un objet de package tel qu'une tâche.  
  
-   Spécifiez la valeur et le type de données de la variable.  
  
 La seule option configurable des variables système est le déclenchement d'un événement lorsque leur variable change.  
  
 Un ensemble de variables système différent est disponible pour différents types de conteneurs. Pour plus d'informations sur les variables système utilisées par les packages et leurs éléments, consultez [System Variables](system-variables.md).  
  
 Pour plus d’informations sur les scénarios d’utilisation concrète des variables, consultez [Utiliser des variables dans des packages](../../2014/integration-services/use-variables-in-packages.md).  
  
## <a name="variable-properties"></a>Propriétés des variables  
 Vous pouvez configurer les variables définies par l’utilisateur en définissant les propriétés suivantes dans la fenêtre **Variables** ou la fenêtre **Propriétés** . Certaines propriétés sont disponibles uniquement dans la fenêtre Propriétés.  
  
> [!NOTE]  
>  La seule option configurable des variables système est le déclenchement d'un événement lorsque leur variable change.  
  
 Description  
 Spécifie la description de la variable.  
  
 EvaluateAsExpression  
 Lorsque la propriété est définie `True`, l’expression fournie est utilisée pour définir la valeur de la variable.  
  
 Expression  
 Spécifie l'expression affectée à la variable.  
  
 Nom     
 Spécifie le nom de la variable.  
  
 Espace de noms  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fournit deux espaces de noms, **User** et **System**. Par défaut, les variables personnalisées se trouvent dans l’espace de noms **User** et les variables système se trouvent dans l’espace de noms **System** . Vous pouvez créer des espaces de noms supplémentaires pour les variables définies par l’utilisateur et changer le nom de l’espace de noms **User**, mais vous ne pouvez pas modifier le nom de l’espace de noms **System**, ajouter des variables à l’espace de noms **System**, ni affecter des variables système à un autre espace de noms.  
  
 RaiseChangedEvent  
 Lorsque la propriété est définie sur `True`, l'événement `OnVariableValueChanged` est déclenché lorsque la valeur de la variable change.  
  
 En lecture seule  
 Lorsque la propriété est définie sur `False`, la variable est en lecture-écriture.  
  
 Portée  
 > [!NOTE]  
>  Vous pouvez modifier ce paramètre de propriété uniquement en cliquant sur **Déplacer la variable** dans la fenêtre **Variables** .  
  
 Une variable est créée dans la portée d'un package ou dans la portée d'un conteneur, d'une tâche ou d'un gestionnaire d'événements dans le package. Le conteneur de packages se trouvant au sommet de la hiérarchie de conteneurs, les variables avec une portée de package fonctionnent comme les variables globales et peuvent être utilisées par tous les conteneurs du package. De même, les variables définies dans la portée d'un conteneur tel qu'un conteneur de boucles For peuvent être utilisées par toutes les tâches ou les conteneurs situés dans le conteneur de boucles For.  
  
 Si un package exécute d'autres packages par le biais de la tâche d'exécution de package, les variables définies dans la portée du package appelant ou de la tâche d'exécution de package peuvent être mises à disposition du package appelé à l'aide du type de configuration Variable de package parent. Pour plus d’informations, consultez [Package Configurations](../../2014/integration-services/package-configurations.md).  
  
 IncludeInDebugDump  
 Indiquez si la valeur variable est incluse dans les fichiers de vidage de débogage.  
  
 Pour les variables système et les variables définies par l’utilisateur, la valeur par défaut pour le **InclueInDebugDump** option est `true`.  
  
 Toutefois, pour les variables définies par l’utilisateur, le système réinitialise le **IncludeInDebugDump** option `false` lorsque les conditions suivantes sont remplies :  
  
-   Si le **EvaluateAsExpression** a la valeur de propriété de variable `true`, le système réinitialise le **IncludeInDebugDump** option `false`.  
  
     Pour inclure le texte de l’expression en tant que valeur de la variable dans les fichiers de vidage du débogage, définissez le **IncludeInDebugDump** option `true`.  
  
-   Si le type de données de variable est changé en une chaîne, le système réinitialise le **IncludeInDebugDump** option `false`.  
  
 Lorsque le système réinitialise le **IncludeInDebugDump** option `false`, cela peut remplacer la valeur sélectionnée par l’utilisateur.  
  
 Valeur  
 La valeur d'une variable définie par l'utilisateur peut être un littéral ou une expression. Une variable inclut des options permettant de définir la valeur de la variable et le type de données de la valeur. Les deux propriétés doivent être compatibles : par exemple, l'utilisation d'une valeur de chaîne avec un type de données Integer n'est pas valide.  
  
 Si la variable est configurée de façon à correspondre à une expression, vous devez fournir une expression. Au moment de l'exécution, l'expression est évaluée et le résultat de l'évaluation est affecté comme valeur de la variable. Par exemple, si une variable utilise l'expression `DATEPART("month", GETDATE())` , la valeur de la variable est l'équivalent numérique du mois de la date actuelle. L'expression doit être une expression valide qui utilise la syntaxe de grammaire d'expression [!INCLUDE[ssIS](../includes/ssis-md.md)] . Lorsqu'une expression est utilisée avec des variables, elle peut utiliser des littéraux et les opérateurs et fonctions fournis par la grammaire d'expression, mais elle ne peut pas faire référence aux colonnes d'un flux de données du package. La longueur maximale d'une expression est limitée à 4 000 caractères. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).  
  
 ValueType  
 > [!NOTE]  
>  La valeur de la propriété apparaît dans la colonne **Type de données** de la fenêtre **Variables** .  
  
 Spécifie le type de données de la valeur de la variable.  
  
## <a name="configuring-variables"></a>Configuration des variables  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)], consultez [Fenêtre Variables](../../2014/integration-services/variables-window.md).  
  
 Pour en savoir plus sur les propriétés de la variable et pour plus d’informations sur la définition par programmation de ces propriétés, consultez <xref:Microsoft.SqlServer.Dts.Runtime.Variable>.  
  
## <a name="related-tasks"></a>Tâches associées  
 [Ajouter, supprimer, modifier l’étendue d’une variable définie par l’utilisateur dans un package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
 [Définir les propriétés d’une variable définie par l’utilisateur](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md)  
  
 [Utiliser les valeurs des variables et des paramètres dans un package enfant](../../2014/integration-services/use-the-values-of-variables-and-parameters-in-a-child-package.md)  
  
 [Mapper des paramètres de requête à des variables dans un composant de flux de données](data-flow/map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
  
