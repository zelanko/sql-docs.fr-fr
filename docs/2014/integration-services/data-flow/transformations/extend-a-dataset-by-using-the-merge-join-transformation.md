---
title: Étendre un dataset à l’aide de la transformation de jointure de fusion | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- Merge Join transformation
- datasets [Integration Services], joining
- datasets [Integration Services], extending
- joining datasets [Integration Services]
ms.assetid: 9e512c3c-f89b-45f3-8281-cdb8f35a2b1f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b88d3ec75e73329f8de1e97f7b9936203e745946
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062175"
---
# <a name="extend-a-dataset-by-using-the-merge-join-transformation"></a>Étendre un dataset à l'aide de la transformation de jointure de fusion
  Pour pouvoir ajouter et configurer une transformation de jointure de fusion, le package doit inclure au moins une tâche de flux de données et deux composants de flux de données qui fournissent des entrées à la transformation de jointure de fusion.  
  
 La transformation de jointure de fusion requiert deux entrées triées. Pour plus d’informations, consultez [Trier des données pour les transformations de fusion et de jointure de fusion](sort-data-for-the-merge-and-merge-join-transformations.md).  
  
### <a name="to-extend-a-dataset"></a>Pour étendre un dataset  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de données** , puis dans la **Boîte à outils**, faites glisser la transformation de jointure de fusion vers la surface de dessin.  
  
4.  Connectez la transformation de jointure de fusion au flux de données en faisant glisser le connecteur à partir d'une source de données ou d'une transformation précédente vers la transformation de jointure de fusion.  
  
5.  Double-cliquez sur la transformation de jointure de fusion.  
  
6.  Dans la boîte de dialogue **Éditeur de transformation de jointure de fusion** , sélectionnez le type de jointure à utiliser dans la liste **Type de jointure** .  
  
    > [!NOTE]  
    >  Si vous sélectionnez **Jointure externe gauche** , vous pouvez cliquer sur **Échanger les entrées** pour échanger les entrées et convertir la jointure externe gauche en jointure externe droite.  
  
7.  Faites glisser des colonnes de l'entrée de gauche vers des colonnes de l'entrée de droite afin de spécifier les colonnes de jointure. Si les colonnes portent le même nom, vous pouvez cocher la case **Clé de jointure** afin que la transformation de jointure de fusion crée la jointure.  
  
    > [!NOTE]  
    >  Vous pouvez créer des jointures uniquement entre des colonnes ayant la même position de tri et les jointures doivent être créées dans l'ordre spécifié par la position de tri. Si vous essayez de créer des jointures dans le désordre, **l’Éditeur de transformation de jointure de fusion** vous demande de créer des jointures supplémentaires pour les positions d’ordre de tri ignorées.  
  
    > [!NOTE]  
    >  Par défaut, la sortie est triée sur les colonnes de jointure.  
  
8.  Dans les entrées de gauche et de droite, activez les cases à cocher des colonnes supplémentaires à inclure dans la sortie. Les colonnes de jointure sont incluses par défaut.  
  
9. Mettez éventuellement à jour les noms des colonnes de sortie dans la colonne **Alias de sortie** .  
  
10. Cliquez sur **OK**.  
  
11. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Transformation de jointure de fusion](merge-join-transformation.md)   
 [Transformations Integration Services](integration-services-transformations.md)   
 [Chemins Integration Services](../integration-services-paths.md)   
 [Tâche de flux de données] ((.. /.. /Control-Flow/Data-Flow-Task.MD)  
  
  
