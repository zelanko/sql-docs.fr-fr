---
title: "Fournir une requête Source OData à l’exécution | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcbba7f4-6e5d-46e6-a73a-3f17d3ff376a
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ee79d0f1b31963b7d13aa07bf4603246139c3a7c
ms.openlocfilehash: 9da1f1be0a790d01f9403d6fc05a5c1498c0ee8b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/23/2017

---
# <a name="provide-an-odata-source-query-at-runtime"></a>Fournir une requête Source OData à l’exécution
 Vous pouvez modifier la requête OData Source à l’exécution en ajoutant un *expression* à la **[OData Source]. [ Requête]** propriété de la tâche de flux de données.  
  
 Les colonnes retournées doivent être les mêmes colonnes qui ont été retournés au moment du design ; dans le cas contraire, vous obtenez une erreur lorsque le package est exécuté. Veillez à spécifier les mêmes colonnes (dans le même ordre) lorsque vous utilisez l'option de requête $select. Une alternative plus sûre à l'utilisation de l'option $select est de désélectionner les colonnes que vous ne souhaitez pas utiliser directement de l'interface utilisateur du composant source.  
  
 Il existe d'autres méthodes de définition dynamique de la valeur de la requête à l'exécution. Voici quelques-unes des méthodes plus courantes.  
  
## <a name="provide-the-query-as-a-parameter"></a>Fournir la requête en tant que paramètre  
 La procédure suivante montre comment exposer la requête utilisée par un composant OData Source en tant que paramètre du package.  
  
1.  Cliquez avec le bouton droit sur **Tâche de flux de données** et sélectionnez l’option **Paramétrer**. option.  
  
2.  Dans le **paramétrer** boîte de dialogue, sélectionnez **[\<nom du composant Source OData >]. [ Requête]** pour **propriété**.  
  
3.  Vous pouvez soit **créer un paramètre** , soit **utiliser un paramètre existant**.  
  
4.  Si vous sélectionnez **créer un nouveau paramètre**:  
  
    1.  Entrez un **nom** et une **description** pour le paramètre.  
  
    2.  Spécifiez la **valeur** par défaut du paramètre.  
  
    3.  Spécifiez l’ **étendue** (**package** ou **projet**) du paramètre.  
  
    4.  Spécifiez si le paramètre est **obligatoire** ou non.  
  
5.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
## <a name="provide-the-query-with-an-expression"></a>La requête lui fournissez une expression
 Cette méthode est utile lorsque vous souhaitez construire dynamiquement la chaîne de requête lors de l’exécution.
  
1.  Sélectionnez le **Data Flow Task** qui contient votre **OData Source**.  
  
2.  La fenêtre **Propriétés** met en surbrillance la propriété **Expressions** .  
  
3.  Cliquez sur les points de suspension (bouton) pour afficher la **Éditeur d’Expressions de propriété**.  
  
4.  Sélectionnez la propriété **[OData Source].[Query]** .  
  
5.  Cliquez sur les points de suspension (bouton) pour **Expression**.  
  
6.  Entrez l’ **expression**.  
  
7.  Cliquez sur **OK**.  
  
> [!NOTE]  
> Lorsque vous utilisez cette approche, vous devez vous assurer que les valeurs que vous définissez sont correctement encodé en URL. Lorsque vous recevez des valeurs de l'entrée utilisateur (par exemple, lorsque vous définissez des valeurs d'option de requête individuelles), vous devez vous assurer que les valeurs sont validées pour éviter des attaques potentielles par injection SQL.  
  
  

