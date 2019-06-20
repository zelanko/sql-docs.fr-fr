---
title: Fonctionnalités dans SQL Server 2014 Analysis Services déconseillées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, backward compatibility
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
- deprecated features [Analysis Services]
ms.assetid: 2c96ecfe-a170-41d0-bee3-74503f880197
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 04d12aab677e38d17d4e869e6885eb470854d824
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66081920"
---
# <a name="deprecated-analysis-services-features-in-sql-server-2014"></a>Fonctionnalités Analysis Services déconseillées dans SQL Server 2014
  Cette rubrique décrit les fonctionnalités [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] déconseillées qui sont toujours disponibles dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Il est prévu que ces fonctionnalités soient supprimées dans une prochaine version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Les fonctions déconseillées ne doivent pas être utilisées dans de nouvelles applications.  
  
## <a name="features-not-supported-in-the-next-version-of-sql-server"></a>Fonctionnalités non prises en charge dans la prochaine version de SQL Server  
 Les fonctionnalités suivantes du [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne seront pas prises en charge dans la prochaine version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Évitez d'utiliser ces fonctionnalités dans vos nouveaux développements et modifiez dès que possible les applications qui y ont recours.  
  
|Category|Fonctionnalité déconseillée|Remplacement|  
|--------------|------------------------|-----------------|  
|Fonction MDX|Fonction CalculationPassValue|Aucun. Le moteur OLAP gère le test de calcul. Cette fonction MDX n'est plus requise.|  
|Fonction MDX|fonction CalculationCurrentPass|Aucun. Le moteur OLAP gère le test de calcul. Cette fonction MDX n'est plus requise.|  
|MDX (Multidimensional Expressions)|L'indicateur d'optimiseur de requête NON_EMPTY_BEHAVIOR a été activé par défaut.|L'indicateur d'optimiseur de requête NON_EMPTY_BEHAVIOR sera désactivé par défaut dans une version ultérieure. Il s'agit d'un indicateur d'optimisation MDX qui peut générer des résultats incorrects lorsqu'il n'est pas utilisé correctement.|  
|Autres|Propriété intrinsèque de cellule CELL_EVALUATION_LIST|Fournissait à l'origine une liste de formules évaluées qui s'appliquent à une cellule. Elle est vide dans cette version d'Analysis Services.  L'ordre de résolution est maintenant spécifié dans le script MDX. Pour plus d’informations, consultez [compréhension d’ordre de passage et d’ordre de résolution &#40;MDX&#41;](multidimensional-models/mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md)|  
|Objets|Assemblys COM|Les assemblys COM peuvent présenter un risque pour la sécurité. La prise en charge des assemblys COM sera supprimée dans une version ultérieure.|  
  
## <a name="features-not-supported-in-a-future-version-of-sql-server"></a>Fonctionnalités non prises en charge dans une future version de SQL Server  
 Les fonctions suivantes du [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] seront prises en charge dans la prochaine version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], mais seront supprimées dans une version ultérieure. La version spécifique de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] n'a pas été déterminée.  
  
|Category|Fonctionnalité déconseillée|Remplacement|  
|--------------|------------------------|-----------------|  
|Modèles multidimensionnels|Partitions distantes|Aucun. Utilisez des partitions locales à la place. Consultez [créer et gérer une Partition locale &#40;Analysis Services&#41; ](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md) pour plus d’informations.|  
|Modèles multidimensionnels|Groupes de mesures liés distants|Un groupe de mesures lié distant est un groupe de mesures lié avec une source de données sur un serveur distant. La possibilité d'utiliser une source de données distante pour un groupe de mesures lié va être abandonnée.<br /><br /> Aucun remplacement n'est prévu pour cette fonctionnalité. Nous recommandons d'utiliser des groupes de mesures liés locaux à la place. Consultez la rubrique [Linked Measure Groups](multidimensional-models/linked-measure-groups.md) (éventuellement en anglais) pour plus d'informations.|  
|Modèles multidimensionnels|Écriture différée dimensionnelle|Aucun. Utilisez l'écriture différée de partition si vous avez besoin de la fonction d'écriture différée. Consultez [Set Partition Writeback](multidimensional-models/set-partition-writeback.md) pour plus d’informations.|  
|Modèles multidimensionnels|Dimensions liées|Aucun. Envisagez de copier les dimensions dans des modèles supplémentaires plutôt que les lier à une dimension dans un autre modèle.|  
|MDX|Propriété Non_Empty_Behavior|Aucun. Si vous ne définissez pas correctement cette propriété lorsque vous créez un membre calculé, cela augmente la probabilité de retour de résultats non valides. Les optimisations qui ont récemment été apportées au moteur OLAP ont amélioré les opérations sur les jeux de données éparses, rendant cette propriété moins pertinente.|  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité descendante Analysis Services](analysis-services-backward-compatibility.md)   
 [Fonctionnalités Analysis Services interrompues dans SQL Server 2014](discontinued-analysis-services-functionality-in-sql-server-2014.md)  
  
  
