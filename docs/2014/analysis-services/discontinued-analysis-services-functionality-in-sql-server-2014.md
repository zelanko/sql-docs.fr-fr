---
title: Fonctionnalités Analysis Services dans SQL Server 2014 supprimées | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Analysis Services, backward compatibility
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
- discontinued functionality [Analysis Services]
- unsupported features [Analysis Services]
ms.assetid: 39406be1-9819-4629-9c29-b32fb20bab2e
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 52b6dbe4ed746b151a6d9bae3a606c2f0e117df4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142580"
---
# <a name="discontinued-analysis-services-functionality-in-sql-server-2014"></a>Fonctionnalités Analysis Services abandonnées dans SQL Server 2014
  Cette rubrique décrit les fonctionnalités de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui ne sont plus disponibles dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
## <a name="discontinued-features-in-includesssql14includessssql14-mdmd"></a>Fonctionnalités supprimées dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
  
|Catégorie|Fonctionnalité déconseillée|Remplacement|  
|--------------|------------------------|-----------------|  
|Cube locaux|Propriété de chaîne de connexion INSERTINTO|La syntaxe de la chaîne de connexion d'origine pour le remplissage de cubes locaux est remplacée par l'instruction CREATE GLOBAL CUBE. Pour plus d’informations, consultez [CREATE GLOBAL CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube).|  
|Cube locaux|Propriété de chaîne de connexion CREATECUBE|La syntaxe de la chaîne de connexion d'origine pour le remplissage de cubes locaux est remplacée par l'instruction CREATE GLOBAL CUBE. Pour plus d’informations, consultez [CREATE GLOBAL CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube).|  
|Exploration de données|SQL Server 2000 PMML|La fonctionnalité de SQL Server 2000 PMML produisait un formulaire de PMML qui avait des extensions exclusives permettant de prendre en charge les fonctionnalités uniques fournies par les algorithmes d'exploration de données qui n'étaient pas disponibles dans la spécification PMML. Dans SQL Server 2005, Analysis Services a mis à jour la fonctionnalité PMML avec le nouveau standard PMML 2.1. Par conséquent, les extensions exclusives ajoutées dans SQL Server 2000 ne sont plus exigées, bien qu'elles soient encore prises en charge dans cette version.|  
|Instruction MDX|Instruction CREATE ACTION|Cette instruction est comprise pour des raisons de compatibilité descendante. Elle est remplacée par l'objet Action. Pour plus d’informations sur la façon de créer des actions dans les versions récentes de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], consultez [Actions &#40;Analysis Services - données multidimensionnelles&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).|  
  
## <a name="discontinued-features-in-previous-releases"></a>Fonctionnalités abandonnées dans les versions précédentes  
 L'Assistant Migration, utilisé pour migrer des bases de données SQL Server 2000 Analysis Services vers des versions plus récentes, est supprimé, car SQL Server 2000 n'est plus pris en charge.  
  
 La bibliothèque DSO (Decision Support Objects), qui assurait la compatibilité avec les bases de données SQL Server 2000 Analysis Services, est également supprimée et ne fait plus partie de SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité descendante Analysis Services](analysis-services-backward-compatibility.md)  
  
  
