---
title: "Ajouter un attribut à une Dimension | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adding attributes
- automatic attribute creation
- attributes [Analysis Services], creating
- attributes [Analysis Services], adding
- manual attribute creation [Analysis Services]
ms.assetid: 25826ba1-2b38-4b34-bd3a-7eba116093ae
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fd1a1579a81f1728a47b217f06739b722fe226c7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="attribute-properties---add-an--attribute-to-a-dimension"></a>Attribut des propriétés - ajouter un attribut à une Dimension
  Vous pouvez ajouter un attribut à une dimension soit automatiquement, soit manuellement dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Pour créer un attribut automatiquement, dans le volet **Structure de dimension** du Concepteur de dimensions de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], sélectionnez la colonne que vous voulez mapper avec un attribut, puis faites glisser cette colonne du volet **Vue de source de données** jusqu’au volet **Attributs** . Vous créez ainsi un attribut qui est mappé avec la colonne et en reçoit le nom. S’il existe déjà un attribut de ce nom, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lui ajoute à la fin un numéro en commençant par « 1 » pour le premier nom en double.  
  
 Pour créer un attribut manuellement, affichez la grille dans le volet **Attributs** . Dans la colonne nom de la dernière ligne dans la grille, cliquez sur le  **\<nouvel attribut >** élément. Tapez le nom du nouvel attribut. Vous créez ainsi un attribut qui n'est pas mappé avec une colonne et dont toutes les propriétés ont leurs valeurs par défaut. Vous pouvez définir le mappage dans la fenêtre **Propriétés** de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] en configurant la propriété **KeyColumns** du nouvel attribut.  
  
 Pour plus d’informations, consultez [Définir un nouvel attribut automatiquement](../../analysis-services/multidimensional-models/attribute-properties-define-a-new-attribute-automatically.md), [Lier un attribut à une colonne de nom](../../analysis-services/multidimensional-models/attribute-properties-bind-an-attribute-to-a-name-column.md)et [Modifier la propriété KeyColumn d’un attribut](../../analysis-services/multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des propriétés d'attribut de dimension](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
