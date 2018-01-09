---
title: "Activer l’écriture différée de Dimension | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying dimensions
- writeback [Analysis Services], setting up
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], writeback
- dimensions [Analysis Services], writeback
- writeback [Analysis Services]
- dimensions [Analysis Services], modifying
- manual dimension structure modifications
ms.assetid: a4b5eb5a-366d-4fc8-ad0d-5bdb8e7b4163
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 69390faf39311c3b7072e06aff2b64fcafd9a62c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="bi-wizard---enable-dimension-writeback"></a>Assistant BI - Enable écriture différée de Dimension
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Ajoutez l’amélioration de l’écriture différée de dimension dans un cube ou une dimension afin de permettre aux utilisateurs de modifier manuellement la structure de dimension et les membres. Les mises à jour dans une dimension activée en écriture sont enregistrées directement dans la table de la dimension. Cette amélioration modifie la définition de la propriété **WriteEnabled** pour une dimension.  
  
 Pour ajouter l’écriture différée de la dimension, utilisez l’Assistant Business Intelligence, puis sélectionnez l’option **Activer l’écriture différée de la dimension** dans la page **Choisir des améliorations** . Cet Assistant vous guide tout au long des étapes de sélection d'une dimension à laquelle vous souhaitez appliquer l'écriture en différé et de définition de cette option pour la dimension sélectionnée.  
  
> [!NOTE]  
>  L'écriture différée est prise en charge uniquement pour les mini-Data Warehouse et les bases de données relationnelles SQL Server.  
  
## <a name="selecting-a-dimension"></a>Sélection d'une dimension  
 Dans la première page **Activer l’écriture différée de la dimension** de l’Assistant, vous spécifiez la dimension à laquelle vous souhaitez appliquer l’écriture différée. L'amélioration que constitue l'écriture différée ajoutée à cette dimension se traduit par des modifications de la dimension. Ces modifications seront héritées par tous les cubes contenant la dimension sélectionnée.  
  
## <a name="setting-dimension-writeback-capability"></a>Définition de la fonctionnalité d'écriture en différé de la dimension  
 Dans la deuxième page **Activer l’écriture différée de la dimension** de l’Assistant, vous paramétrez réellement l’option **Activer l’écriture différée de la dimension** . Quand cette option est automatiquement sélectionnée, la propriété **WriteEnabled** de la dimension a la valeur **True**. Quand cette option est automatiquement désactivée, la propriété a la valeur **False**.  
  
## <a name="remarks"></a>Notes   
 Lorsque vous créez un membre, vous devez inclure chaque attribut dans une dimension. Vous ne pouvez pas insérer un membre sans définir la valeur de l'attribut clé de la dimension. Par conséquent, la création de membres est soumise aux contraintes (telles que valeurs de clés non NULL) définies dans la table de dimension. Vous devez également tenir compte des colonnes éventuellement spécifiées par les propriétés de dimension, telles que les colonnes spécifiées dans les propriétés de dimension **CustomRollupColumn**, **CustomRollupPropertiesColumn** ou **UnaryOperatorColumn** .  
  
> [!WARNING]  
>  Si vous utilisez SQL Azure comme source de données pour effectuer une écriture différée dans une base de données Analysis Services, l'opération échoue. Il s'agit d'un comportement par défaut, car l'option de fournisseur qui active plusieurs jeux de résultats actifs MARS n'est pas activée par défaut.  
>   
>  La solution consiste à ajouter le paramètre suivant dans la chaîne de connexion, afin de prendre en charge MARS et d'activer l'écriture différée :  
>   
>  `"MultipleActiveResultSets=True"`  
>   
>  Pour plus d’informations, consultez [Utilisation de MARS &#40;Multiple Active Result Sets&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Dimensions activées en écriture](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
