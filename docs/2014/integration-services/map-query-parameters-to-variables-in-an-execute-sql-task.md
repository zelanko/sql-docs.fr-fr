---
title: Mapper des paramètres de requête à des Variables dans une tâche d’exécution SQL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameterized SQL commands [Integration Services]
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- Execute SQL task [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 6a164349-dfcf-4995-80bc-d4e7aee52a83
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4adc96042090ee1cd184eebdb9f9ca5526312dd2
ms.sourcegitcommit: a13256f484eee2f52c812646cc989eb0ce6cf6aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803084"
---
# <a name="map-query-parameters-to-variables-in-an-execute-sql-task"></a>Mapper des paramètres de requête à des variables dans une tâche d'exécution SQL

  Cette rubrique décrit la façon d'utiliser une instruction SQL paramétrable dans la tâche d'exécution SQL et de créer des mappages entre des variables et les paramètres de l'instruction SQL.  
  
 Pour en savoir plus sur la tâche d’exécution SQL, les marqueurs de paramètres et les noms de paramètres que vous utilisez avec différents types de connexions, consultez [Tâche d’exécution de requêtes SQL](control-flow/execute-sql-task.md) et [Paramètres et codes de retour dans la tâche d’exécution SQL](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a>Pour mapper un paramètre de requête à une variable  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] que vous voulez utiliser.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de contrôle** .  
  
4.  Si le package ne contient pas déjà une tâche d'exécution SQL, ajoutez-en une au flux de contrôle du package. Pour plus d’informations, consultez [ajouter ou supprimer une tâche ou un conteneur dans un flux de contrôle](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  .  
  
5.  Double-cliquez sur la tâche d'exécution SQL.  
  
6.  Indiquez une commande SQL paramétrable de l'une des manières suivantes :  
  
    -   Utilisez l’entrée directe et tapez la commande SQL dans la propriété SQLStatement.  
  
    -   Utilisez l’entrée directe, cliquez sur **Générer la requête**, puis créez une commande SQL à l’aide des outils graphiques fournis par le Générateur de requêtes.  
  
    -   Utilisez un fichier de connexion, puis référencez le fichier contenant la commande SQL.  
  
    -   Utilisez une variable, puis référencez la variable contenant la commande SQL.  
  
     Les marqueurs de paramètres que vous utilisez dans les instructions SQL paramétrables sont liés au type de connexion que la tâche d'exécution SQL utilise.  
  
    |Type de connexion|Marqueur de paramètre|  
    |---------------------|----------------------|  
    |ADO|?|  
    |ADO.NET et SQLMOBILE|@\<nom du paramètre>|  
    |ODBC|?|  
    |EXCEL et OLE DB|?|  
  
     Le tableau suivant présente des exemples de la commande SELECT par type de gestionnaire de connexions. Les paramètres fournissent les valeurs de filtre dans les clauses WHERE. Les exemples utilisent la commande SELECT pour retourner les produits de la table **Product** dans [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)] qui ont un **ProductID** supérieur et inférieur aux valeurs spécifiées par deux paramètres.  
  
    |Type de connexion|Syntaxe SELECT|  
    |---------------------|-------------------|  
    |EXCEL, ODBC et OLEDB|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |ADO|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |[!INCLUDE[vstecado](../includes/vstecado-md.md)]|`SELECT* FROM Production.Product WHERE ProductId > @parmMinProductID AND ProductID < @parmMaxProductID`|  
  
     Pour obtenir des exemples d’utilisation des paramètres avec des procédures stockées, consultez [Paramètres et codes de retour dans la tâche d’exécution SQL](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).  
  
7.  Cliquez sur **Mappage de paramètre**.  
  
8.  Pour ajouter un mappage de paramètre, cliquez sur **Ajouter**.  
  
9. Fournissez un nom dans la zone **Nom du paramètre** .  
  
     Les noms de paramètres que vous utilisez sont liés au type de connexion que la tâche d'exécution SQL utilise.  
  
    |Type de connexion|Nom du paramètre|  
    |---------------------|--------------------|  
    |ADO|Param1, Param2, ...|  
    |ADO.NET et SQLMOBILE|@\<nom du paramètre>|  
    |ODBC|1, 2, 3, ...|  
    |EXCEL et OLE DB|0, 1, 2, 3, ...|  
  
10. Dans la liste **Nom de variable** , sélectionnez une variable. Pour plus d’informations, consultez [Ajouter, supprimer, modifier l’étendue de la variable définie par l’utilisateur dans un package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md).  
  
11. Dans la liste **Direction** , indiquez si le paramètre est une entrée, une sortie ou une valeur de retour.  
  
12. Dans la liste **Type de données** , définissez le type de données du paramètre.  
  
    > [!IMPORTANT]  
    >  Le type de données du paramètre doit être compatible avec le type de données de la variable.  
  
13. Répétez les étapes 8 à 11 pour chaque paramètre de l'instruction SQL.  
  
    > [!IMPORTANT]  
    >  L'ordre de mappage des paramètres doit être identique à leur ordre d'apparition dans l'instruction SQL.  
  
14. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de requêtes SQL, tâche](control-flow/execute-sql-task.md)   
 [Paramètres et Codes de retour dans la tâche d’exécution SQL](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)   
 [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md)  
  
  
