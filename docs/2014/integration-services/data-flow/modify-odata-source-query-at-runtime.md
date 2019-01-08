---
title: Modifier la requête de Source OData à l’exécution | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bcbba7f4-6e5d-46e6-a73a-3f17d3ff376a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0700d2893028efea5486221906636d6c749b66bd
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52804845"
---
# <a name="modify-odata-source-query-at-runtime"></a>Modifier la requête de la source OData à l'exécution
  Vous pouvez modifier la requête de la source OData à l’exécution en ajoutant une expression à la propriété **[OData Source].[Query]** de la tâche de flux de données.  
  
 Notez que les colonnes doivent être identiques à celles utilisées au moment de la conception ; sinon vous obtiendrez une erreur lors de l'exécution du package. Veillez à spécifier les mêmes colonnes (dans le même ordre) lorsque vous utilisez l'option de requête $select. Une alternative plus sûre à l’utilisation de l’option $select est de désélectionner les colonnes que vous ne souhaitez pas utiliser directement de l’interface utilisateur du composant source.  
  
 Il existe d'autres méthodes de définition dynamique de la valeur de la requête à l'exécution. Voici quelques-unes des plus courantes.  
  
## <a name="exposing-the-query-as-a-parameter"></a>Exposer une requête en tant que paramètre  
 La procédure suivante comporte des étapes pour exposer une requête utilisée par un composant source OData comme paramètre sur le package.  
  
1.  Cliquez avec le bouton droit sur **Tâche de flux de données** et sélectionnez l’option **Paramétrer...**.  
  
2.  Dans la boîte de dialogue **Paramétrer**, sélectionnez **[\<<Nom du composant source OData].[Query]** pour **Propriété**.  
  
3.  Vous pouvez soit **créer un paramètre** , soit **utiliser un paramètre existant**.  
  
4.  Si vous sélectionnez **Créer un paramètre**, procédez comme suit :  
  
    1.  Entrez un **nom** et une **description** pour le paramètre.  
  
    2.  Spécifiez la **valeur** par défaut du paramètre.  
  
    3.  Spécifiez l’ **étendue** (**package** ou **projet**) du paramètre.  
  
    4.  Spécifiez si le paramètre est **obligatoire** ou non.  
  
5.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
## <a name="using-an-expression"></a>Utiliser une expression  
 Cette méthode est utile lorsque vous souhaitez construire dynamiquement la chaîne de requête à l'exécution. Dans cet exemple, la variable MaxRows sera définie par d'autres moyens (script, paramètre, etc.).  
  
1.  Sélectionnez la **Tâche de flux de données** qui contient votre **Source OData**.  
  
2.  La fenêtre **Propriétés** met en surbrillance la propriété **Expressions** .  
  
3.  Cliquez sur le... suspension (…) pour faire apparaître le **Éditeur d’Expressions de propriété**.  
  
4.  Sélectionnez la propriété **[OData Source].[Query]** .  
  
5.  Cliquez sur le... suspension (…) pour **Expression**.  
  
6.  Entrez l’ **expression**.  
  
7.  Cliquez sur **OK**.  
  
> [!WARNING]  
>  Notez qu'en utilisant cette approche, vous devez vous assurer que les valeurs définies sont codées correctement pour l'URL. Lorsque vous recevez des valeurs de l'entrée utilisateur (par exemple, lorsque vous définissez des valeurs d'option de requête individuelles), vous devez vous assurer que les valeurs sont validées pour éviter des attaques potentielles par injection SQL.  
  
  
