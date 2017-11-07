---
title: "Verrouillage et déverrouillage de bases de données (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8924b6a21a0bb815ec377072615db2efb4fa2f07
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="locking-and-unlocking-databases-xmla"></a>Verrouillage et déverrouillage de bases de données (XMLA)
  Vous pouvez verrouiller et déverrouiller des bases de données à l’aide, respectivement, la [verrou](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md) et [Unlock](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md) commandes XML for Analysis (XMLA). En règle générale, les autres commandes XMLA verrouillent et déverrouillent automatiquement les objets, selon le cas, pour faire aboutir la commande pendant l'exécution. Vous pouvez explicitement verrouiller ou déverrouiller une base de données pour exécuter plusieurs commandes dans une transaction unique, comme un [lot](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) commande, tout en empêchant d’autres applications à partir de la validation d’une transaction d’écriture à la base de données.  
  
## <a name="locking-databases"></a>Verrouillage de bases de données  
 La commande **Lock** verrouille un objet, pour un usage partagé ou exclusif, dans le contexte de la transaction actuellement active. Un verrou sur un objet empêche la validation des transactions aussi longtemps que le verrou n'est pas supprimé. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge deux types de verrous : les verrous partagés et les verrous exclusifs. Pour plus d’informations sur les types de verrous pris en charge par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez [élément Mode &#40; XMLA &#41; ](../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] autorise uniquement le verrouillage des bases de données. Le [objet](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) élément doit contenir une référence d’objet une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données. Si l'élément **Object** n'est pas spécifié ou si cet élément **Object** fait référence à un objet autre qu'une base de données, une erreur survient.  
  
> [!IMPORTANT]  
>  Seuls les administrateurs de bases de données ou de serveurs peuvent émettre une commande **Lock** de manière explicite.  
  
 Autres commandes implicitement problème un **verrou** commande sur une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données. Toute opération qui lit des données ou les métadonnées à partir d’une base de données, telles que les [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) méthode ou un [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) méthode en cours d’exécution un [instruction](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) command, émettent implicitement un verrou partagé sur la base de données. Toute transaction qui valide les modifications de données ou les métadonnées pour un objet sur un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de base de données, comme un **Execute** méthode en cours d’exécution un [Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) command, émettent implicitement un verrou exclusif sur la base de données.  
  
## <a name="unlocking-objects"></a>Déverrouillage d'objets  
 La commande **Unlock** supprime un verrou établi dans le contexte de la transaction actuellement active.  
  
> [!IMPORTANT]  
>  Seuls les administrateurs de bases de données ou de serveurs peuvent émettre une commande **Unlock** de manière explicite.  
  
 Tous les verrous sont conservés dans le contexte de la transaction en cours. Lors de la validation ou de la restauration de la transaction en cours, tous les verrous définis dans celle-ci sont libérés automatiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Verrouiller l’élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)   
 [Déverrouiller l’élément &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Développement avec XMLA dans Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

