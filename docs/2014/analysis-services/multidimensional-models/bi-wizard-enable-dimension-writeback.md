---
title: Activer l’écriture différée de Dimension | Documents Microsoft
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
- modifying dimensions
- writeback [Analysis Services], setting up
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], writeback
- dimensions [Analysis Services], writeback
- writeback [Analysis Services]
- dimensions [Analysis Services], modifying
- manual dimension structure modifications
ms.assetid: a4b5eb5a-366d-4fc8-ad0d-5bdb8e7b4163
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5a05010b2f102170b64df13e4eb079dde8fbe325
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153151"
---
# <a name="enable-dimension-writeback"></a>Activer l'écriture différée de la dimension
  Ajoutez la fonctionnalité d'écriture en différé de la dimension à un cube ou à une dimension afin de permettre aux utilisateurs de modifier manuellement la structure et les membres de la dimension. Les mises à jour dans une dimension activée en écriture sont enregistrées directement dans la table de la dimension. Cette amélioration modifie la définition de la propriété `WriteEnabled` pour une dimension.  
  
 Pour ajouter l’écriture différée de la dimension, utilisez l’Assistant Business Intelligence, puis sélectionnez l’option **Activer l’écriture différée de la dimension** dans la page **Choisir des améliorations** . Cet Assistant vous guide tout au long des étapes de sélection d'une dimension à laquelle vous souhaitez appliquer l'écriture en différé et de définition de cette option pour la dimension sélectionnée.  
  
> [!NOTE]  
>  L'écriture différée est prise en charge uniquement pour les mini-Data Warehouse et les bases de données relationnelles SQL Server.  
  
## <a name="selecting-a-dimension"></a>Sélection d'une dimension  
 Dans la première page **Activer l’écriture différée de la dimension** de l’Assistant, vous spécifiez la dimension à laquelle vous souhaitez appliquer l’écriture différée. L'amélioration que constitue l'écriture différée ajoutée à cette dimension se traduit par des modifications de la dimension. Ces modifications seront héritées par tous les cubes contenant la dimension sélectionnée.  
  
## <a name="setting-dimension-writeback-capability"></a>Définition de la fonctionnalité d'écriture en différé de la dimension  
 Dans la deuxième page **Activer l’écriture différée de la dimension** de l’Assistant, vous paramétrez réellement l’option **Activer l’écriture différée de la dimension** . Cette option automatiquement définit le `WriteEnabled` propriété de la dimension à `True`. La désactivation automatique de cette option affecte à la propriété `False`.  
  
## <a name="remarks"></a>Notes  
 Lorsque vous créez un membre, vous devez inclure chaque attribut dans une dimension. Vous ne pouvez pas insérer un membre sans définir la valeur de l'attribut clé de la dimension. Par conséquent, la création de membres est soumise aux contraintes (telles que valeurs de clés non NULL) définies dans la table de dimension. Vous devez également envisager des colonnes éventuellement spécifiées par les propriétés de dimension, telles que les colonnes spécifiées dans le `CustomRollupColumn`, `CustomRollupPropertiesColumn` ou `UnaryOperatorColumn` propriétés de dimension.  
  
> [!WARNING]  
>  Si vous utilisez SQL Azure comme source de données pour effectuer une écriture différée dans une base de données Analysis Services, l'opération échoue. Il s'agit d'un comportement par défaut, car l'option de fournisseur qui active plusieurs jeux de résultats actifs MARS n'est pas activée par défaut.  
>   
>  La solution consiste à ajouter le paramètre suivant dans la chaîne de connexion, afin de prendre en charge MARS et d'activer l'écriture différée :  
>   
>  `"MultipleActiveResultSets=True"`  
>   
>  Pour plus d’informations, consultez [Utilisation de MARS &#40;Multiple Active Result Sets&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Dimensions activées en écriture](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  