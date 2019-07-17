---
title: Configurer le niveau (tous) pour les hiérarchies d’attributs | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 23b00a88c8abf80045a38d0b8cc5d0c695949b0b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68178900"
---
# <a name="database-dimensions---configure-the-all-level-for-attribute-hierarchies"></a>Dimensions de base de données - Configurer le niveau (Tous) des hiérarchies d’attributs
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le niveau (Tous) est un niveau facultatif, généré par le système. Il contient un seul membre dont la valeur est l'agrégation des valeurs de tous les membres du niveau situé juste en dessous. Ce membre est appelé membre Tous. Ce membre est créé par le système et il ne figure pas dans la table de dimension. Étant donné que le membre du niveau (Tous) se trouve au sommet d'une hiérarchie, sa valeur est l'agrégation consolidée des valeurs de tous les membres de la hiérarchie. Le membre Tous sert souvent de membre par défaut d'une hiérarchie.  
  
 La présence d’un niveau (Tous) dans une hiérarchie d’attributs dépend de la valeur de la propriété **IsAggregatable** de l’attribut, et la présence d’un niveau (Tous) dans une hiérarchie définie par l’utilisateur dépend de la propriété **IsAggregatable** de l’attribut au niveau le plus élevé de la hiérarchie définie par l’utilisateur. Si la propriété **IsAggregatable** a la valeur **True**, il existera un niveau (Tous). Au contraire, une hiérarchie n’a pas de niveau (Tous) si sa propriété **IsAggregatable** a la valeur **False**.  
  
## <a name="establishing-the-topmost-level"></a>Établissement du niveau le plus élevé  
 Si la propriété **IsAggregatable** de l’attribut source d’un niveau d’une hiérarchie a la valeur **False** , aucun niveau agrégeable ne peut apparaître dans la hiérarchie au-dessus de ce niveau. Un niveau non agrégeable doit être le niveau le plus élevé d’une hiérarchie, ou la propriété **IsAggregatable** des attributs sources des niveaux qui sont au-dessus de lui doit aussi avoir la valeur **False**.  
  
## <a name="all-member-and-all-level"></a>Membre Tous et niveau (Tous)  
 Le membre unique du niveau (Tous) est appelé membre Tous. La propriété **AttributeAllMemberName**d’une dimension spécifie le nom du membre Tous pour les attributs d’une dimension. La propriété **AllMemberName** d’une hiérarchie spécifie le nom du membre Tous de cette hiérarchie.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir un membre par défaut](../../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
