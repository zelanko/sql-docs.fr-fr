---
title: "Compatibilité descendante de SQL Server 2017 Analysis Services | Documents Microsoft"
ms.date: 07/11/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing Analysis Services, backward compatibility
- backward compatibility [Analysis Services]
- compatibility [Analysis Services]
- Analysis Services, backward compatibility
- upgrading Analysis Services
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
ms.assetid: 
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 972ab981eccb6271dfa2f18e0b482f43020ff36b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="analysis-services-backward-compatibility-sql-2017"></a>Compatibilité descendante de Analysis Services (2017 SQL)
[!INCLUDE[ssas-appliesto-sql2017](../includes/ssas-appliesto-sql2017.md)]

Cet article décrit les modifications de la disponibilité des fonctionnalités et de comportement entre la version actuelle et la version précédente.

## <a name="deprecated-features"></a>Fonctionnalités déconseillées
A *fonctionnalité déconseillée* sera supprimé du produit dans une version ultérieure, mais est toujours pris en charge et incluse dans la version actuelle pour assurer la compatibilité descendante. Il est recommandé de que vous arrêter d’utiliser les fonctionnalités déconseillées dans les projets nouveaux et existants pour assurer la compatibilité avec les versions ultérieures.

Les fonctionnalités suivantes sont déconseillées dans cette version :
  
|||  
|-|-|  
|**En mode/une catégorie**|**Fonctionnalité**|
|Tabulaire|Groupes de mesures liés distants|
|Tabulaire|Au niveau de compatibilité 1100 et 1103 des modèles|
|Tabulaire|Propriétés du modèle d’objet tabulaires : Column.TableDetailPosition, Column.IsDefaultLabel, Column.IsDefaultImage|
|(Multidimensionnel)|Exploration de données|

## <a name="discontinued-features"></a>Fonctionnalités supprimées
A *abandonné fonctionnalité* a été déconseillée dans une version antérieure. Il peut continuer à être inclus dans la version actuelle, mais n’est plus pris en charge. Fonctionnalités supprimées peuvent être supprimées entièrement dans une future version ou mettre à jour.

Les fonctionnalités suivantes ont été déconseillées dans une version antérieure et ne sont plus prises en charge dans cette version.
  
|||  
|-|-|  
|**En mode/une catégorie**|**Fonctionnalité**|  
|Tabulaire|Valeur de la propriété mémoire VertipaqPagingPolicy (2), activer la pagination disque à l’aide de la mémoire des fichiers mappés.|
|(Multidimensionnel)|Partitions distantes|  
|(Multidimensionnel)|Groupes de mesures liés distants|  
|(Multidimensionnel)|Écriture différée dimensionnelle|  
|(Multidimensionnel)|Dimensions liées|
|Outils|SQL Server Profiler pour la capture de traces<br /><br /> La solution consiste à utiliser le Générateur de profils d’événements étendus, intégré dans SQL Server Management Studio.  <br /> Consultez [Surveiller Analysis Services avec des événements étendus SQL Server](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md).|  
|Outils|Server Profiler pour Trace Replay <br />Remplacement. Il n’existe aucune solution de remplacement.|  
|Objets de gestion de trace et API de trace|Objets Microsoft.AnalysisServices.Trace (contenant les API des objets Analysis Services de trace et de relecture). La solution de remplacement est multiple :<br /><br /> -   Configuration de trace : Microsoft.SqlServer.Management.XEvent<br />-   Lecture de trace : Microsoft.SqlServer.XEvent.Linq<br />-   Relecture de trace : Aucune|  

## <a name="breaking-changes"></a>Modifications avec rupture
A *modification avec rupture* provoque une fonctionnalité, le modèle de données, le code d’application ou le script ne fonctionne plus après la mise à niveau vers la version actuelle.

Il n’existe pas de modifications importantes dans cette version.

## <a name="behavior-changes"></a>Changements de comportement
A *changement de comportement* affecte le fonctionne de la même fonctionnalité dans la version actuelle par rapport à la version précédente. Seules les modifications de comportement importantes sont décrites. Modifications dans l’interface utilisateur ne sont pas incluses.

Il n’existe aucun changement de comportement dans cette version.


## <a name="see-also"></a>Voir aussi
[Compatibilité descendante de Analysis Services (SQL Server 2016)](analysis-services-backward-compatibility.md)
