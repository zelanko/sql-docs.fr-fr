---
title: Hiérarchies (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services]
- hierarchies [Master Data Services], about hierarchies
ms.assetid: 70dbb1fc-ead7-45be-9552-a45e3ccd8d21
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 45dcd47ff6804bc83e4f1c97c5aefa72ea5e8da8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37259025"
---
# <a name="hierarchies-master-data-services"></a>Hiérarchies (services de données de référence)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], une hiérarchie est une arborescence qui vous permet d'effectuer les opérations suivantes :  
  
-   regrouper des membres semblables à des fins d'organisation ;  
  
-   consolider et synthétiser des membres pour la création de rapports et l'analyse.  
  
## <a name="what-hierarchies-contain"></a>Les hiérarchies contiennent  
 Chaque hiérarchie contient les membres d'une ou de plusieurs entités. Lorsqu'un membre est ajouté, modifié ou supprimé, toutes les hiérarchies sont mises à jour. Cela garantit l'exactitude de vos données dans toutes les hiérarchies. Les hiérarchies permettent aussi de garantir que chaque membre est compté une seule fois.  
  
 Si vous souhaitez créer un regroupement d'un sous-ensemble de membres, envisagez d'utiliser une collection. Pour plus d’informations, consultez [Collections &#40;Master Data Services&#41;](collections-master-data-services.md).  
  
## <a name="kinds-of-hierarchies"></a>Types de hiérarchies  
 Vous pouvez créer plusieurs hiérarchies pour afficher et organiser vos membres de différentes façons. Vous pouvez créer :  
  
-   Des hiérarchies déséquilibrées d'une entité unique, appelées hiérarchies explicites. Pour plus d’informations, consultez [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).  
  
-   Des hiérarchies basées sur le niveau à partir de plusieurs entités selon les relations existantes entre les entités et leurs attributs, appelées hiérarchies dérivées. Pour plus d’informations, consultez [Derived Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md).  
  
> [!NOTE]  
>  Tous les membres dans une hiérarchie doivent figurer dans le même modèle.  
  
## <a name="hierarchies-are-not-taxonomies"></a>Les hiérarchies ne sont pas des taxonomies  
 Une hiérarchie est différente d'une taxonomie. Une taxonomie classe des membres selon plusieurs attributs en même temps, alors qu'une hiérarchie les organise selon un attribut à la fois. Une taxonomie peut inclure le même membre plusieurs fois, alors qu'une hiérarchie inclut un membre une seule fois.  
  
 Par exemple, le même vélo peut être inclus deux fois dans une taxonomie : une fois parce qu'il est de couleur rouge et une fois parce que sa taille est égale à 38. Dans une hiérarchie, le vélo n’étant inclus qu’une seule fois, vous devez décider de l’afficher en fonction de sa couleur ou de sa taille.  
  
## <a name="hierarchy-example"></a>Exemple de hiérarchie  
 Dans l'exemple suivant, les membres de produit sont regroupés par membres de sous-catégorie.  
  
 ![Exemple de hiérarchie regroupée par sous-catégorie](../../2014/master-data-services/media/mds-conc-hierarchy.gif "Exemple de hiérarchie regroupée par sous-catégorie")  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Activer une entité pour les hiérarchies explicites et les collections.|[Activer une entité pour les hiérarchies et Collections explicites &#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|  
|Créer une hiérarchie explicite.|[Créer une hiérarchie explicite &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|  
|Créer une hiérarchie dérivée.|[Créer une hiérarchie dérivée &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)|  
|Masquer ou supprimer des niveaux dans une hiérarchie dérivée existante.|[Masquer ou supprimer des niveaux dans une hiérarchie dérivée &#40;Master Data Services&#41;](../../2014/master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Hiérarchies explicites &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [Hiérarchies dérivées &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
-   [Hiérarchies récursives &#40;Master Data Services&#41;](../../2014/master-data-services/recursive-hierarchies-master-data-services.md)  
  
-   [Hiérarchies avec un niveau supérieur explicite dérivées &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)  
  
-   [Collections &#40;Master Data Services&#41;](collections-master-data-services.md)  
  
  
