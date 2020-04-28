---
title: Partitions activées en écriture | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- write-enabled partitions [Analysis Services]
- partitions [Analysis Services], write-enabled
- partitions [Analysis Services], storage
- writeback [Analysis Services], partitions
- storing data [Analysis Services], partitions
ms.assetid: 46e7683f-03ce-4af2-bd99-a5203733d723
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 13864dba5cac0274204050a8c78730de29f3321e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62727173"
---
# <a name="write-enabled-partitions"></a>Partitions activées en écriture
  Dans un cube, les données sont généralement en lecture seule. Cependant, dans certains scénarios, vous pouvez activer l'écriture sur une partition. Les partitions activées en écriture permettent aux utilisateurs professionnels d'explorer différents scénarios en changeant les valeurs des cellules et en analysant les effets de ces modifications sur les données de cube. Si vous activez une partition en écriture, les applications clientes peuvent enregistrer les modifications des données de la partition. Ces modifications, qu'il est convenu d'appeler données d'écriture différée, sont stockées dans une table séparée et ne remplacent pas de données existantes d'un groupe de mesures. Toutefois, elles sont incorporées dans les résultats des requêtes comme si elles faisaient partie des données de cube.  
  
 Vous pouvez activer en écriture la totalité d'un cube ou uniquement certaines de ces partitions. Les dimensions activées en écriture sont différentes mais complémentaires. Une partition activée en écriture permet aux utilisateurs de mettre à jour les cellules de partition, tandis qu'une dimension activée en écriture leur permet de mettre à jour les membres de dimension. Vous pouvez également utiliser ces deux fonctionnalités conjointement. Par exemple, un cube activé en écriture ou une partition activée en écriture ne doit pas inclure les dimensions activées en écriture. **Rubrique connexe :**[Dimensions activées en écriture](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).  
  
> [!NOTE]  
>  Si vous souhaitez activer en écriture un cube dont la source de données est une base de données Microsoft Access, n'utilisez pas le fournisseur Microsoft OLE DB pour pilotes ODBC dans les définitions de la source de données du cube, ses partitions ou ses dimensions. Utilisez à la place Microsoft Jet 4.0 OLE DB Provider ou n'importe quelle version du Jet Service Pack qui comprend Jet 4.0 OLE. Pour plus d’informations, consultez l’article de la base de connaissances Microsoft [Comment obtenir les Service Pack les plus récents pour Microsoft Jet 4,0 moteur de base de données](https://support.microsoft.com/?kbid=239114).  
  
 Un cube ne peut être activé en écriture que si toutes ses mesures utilisent la fonction d'agrégation `Sum`. Les groupes de mesures liés et les cubes locaux ne peuvent pas être activés en écriture.  
  
## <a name="writeback-storage"></a>Mode de stockage des données d'écriture différée  
 Toute modification apportée par l'utilisateur professionnel est stockée dans la table d'écriture différée sous la forme de différence par rapport à la valeur actuellement affichée. Par exemple, si un utilisateur final fait passer la valeur d'une cellule de 90 à 100, la valeur `+10` est stockée dans la table d'écriture différée, avec l'heure de la modification et des informations concernant l'utilisateur professionnel qui l'a effectuée. L'effet net du cumul des modifications est affiché aux applications clientes. La valeur initiale contenue dans le cube est préservée et un suivi des modifications est enregistré dans la table d'écriture différée.  
  
 Les modifications apportées aux cellules feuilles et non-feuilles sont traitées différemment. Une cellule feuille représente une intersection d'une mesure et d'un membre feuille de toutes les dimensions référencées par le groupe de mesures. La valeur d'une cellule feuille est tirée directement de la table de faits et ne peut pas être divisée davantage en descendant dans la hiérarchie. Si un cube ou une partition est activé en écriture, il est possible de modifier une cellule feuille. Des modifications peuvent être apportées à une cellule non-feuille uniquement si l'application cliente offre un moyen de les diffuser parmi les cellules feuilles qui composent la cellule non-feuille. Ce processus, appelé allocation, est géré dans MDX (Multidimensional Expressions) à l'aide de l'instruction UPDATE CUBE. Les développeurs de solutions Business intelligence peuvent utiliser l'instruction UPDATE CUBE pour inclure la fonctionnalité d'allocation. Pour plus d’informations, consultez [instruction UPDATE CUBE &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube).  
  
> [!IMPORTANT]  
>  Lorsque les cellules mises à jour ne se chevauchent pas, la propriété de chaîne de connexion `Update Isolation Level` peut être utilisée pour améliorer les performances pour UPDATE CUBE. Pour plus d’informations, consultez <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>.  
  
 Qu'une application cliente diffuse ou non les modifications apportées aux cellules non-feuilles, à chaque évaluation des requêtes, les modifications figurant dans la table d'écriture différée sont appliquées aux valeurs des cellules feuilles aussi bien qu'à celles des cellules non-feuilles, de sorte que les utilisateurs professionnels peuvent voir l'impact des modifications sur l'ensemble du cube.  
  
 Les modifications apportées par l'utilisateur professionnel sont conservées dans une table en écriture différée séparée que vous pouvez utiliser de la façon suivante :  
  
-   Effectuez une conversion en partition afin d'incorporer les modifications de façon permanente dans le cube. Cette action rend le groupe de mesures accessible en lecture seule. Vous pouvez spécifier une expression de filtre pour sélectionner les modifications à convertir.  
  
-   Ignorer la table d'écriture différée pour replacer la partition dans son état initial. Cette action rend la partition accessible en lecture seule.  
  
## <a name="security"></a>Sécurité  
 Un utilisateur professionnel est autorisé à enregistrer des modifications dans la table d'écriture différée d'un cube uniquement s'il appartient à un rôle ayant un accès en lecture/écriture aux cellules du cube. Pour chaque rôle, vous pouvez déterminer les cellules de cube qui peuvent être mises à jour et celles qui ne le peuvent pas. Pour plus d’informations, consultez [Grant cube or Model permissions &#40;Analysis Services&#41;](../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Dimensions activées en écriture](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)   
 [Agrégations et conceptions d’agrégation](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)   
 [Partitions &#40;Analysis Services-données multidimensionnelles&#41;](../multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Dimensions activées en écriture](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
