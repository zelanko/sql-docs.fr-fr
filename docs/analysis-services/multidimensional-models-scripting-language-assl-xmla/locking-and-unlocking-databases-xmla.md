---
title: Verrouillage et déverrouillage de bases de données (XMLA) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1f827221a6334b0ff1daf523460562527c3a3f66
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63262069"
---
# <a name="locking-and-unlocking-databases-xmla"></a>Verrouillage et déverrouillage de bases de données (XMLA)
  Vous pouvez verrouiller et déverrouiller des bases de données à l’aide, respectivement, la [verrou](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) et [Unlock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) commandes XML for Analysis (XMLA). En règle générale, les autres commandes XMLA verrouillent et déverrouillent automatiquement les objets, selon le cas, pour faire aboutir la commande pendant l'exécution. Vous pouvez explicitement verrouiller ou déverrouiller une base de données pour exécuter plusieurs commandes dans une transaction unique, comme un [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) commande, tout en empêchant les autres applications à partir de la validation d’une transaction d’écriture à la base de données.  
  
## <a name="locking-databases"></a>Verrouillage de bases de données  
 La commande **Lock** verrouille un objet, pour un usage partagé ou exclusif, dans le contexte de la transaction actuellement active. Un verrou sur un objet empêche la validation des transactions aussi longtemps que le verrou n'est pas supprimé. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge deux types de verrous : les verrous partagés et les verrous exclusifs. Pour plus d’informations sur les types de verrou pris en charge par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez [élément Mode &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/mode-element-xmla).  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] autorise uniquement le verrouillage des bases de données. La commande [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) doit contenir une référence d'objet à une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Si l'élément **Object** n'est pas spécifié ou si cet élément **Object** fait référence à un objet autre qu'une base de données, une erreur survient.  
  
> [!IMPORTANT]  
>  Seuls les administrateurs de bases de données ou de serveurs peuvent émettre une commande **Lock** de manière explicite.  
  
 D'autres commandes permettent d'émettre une commande **Lock** dans une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Toutes les opérations permettant de lire les données ou les métadonnées d'une base de données (par exemple, n'importe quelle méthode [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) ou une méthode [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) exécutant une commande [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) ) émettent implicitement un verrou partagé dans la base de données. Toutes les transactions qui valident des modifications apportées aux données ou aux métadonnées d'un objet dans une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (par exemple, une méthode **Execute** exécutant une commande [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) ) émettent implicitement un verrou exclusif dans la base de données.  
  
## <a name="unlocking-objects"></a>Déverrouillage d'objets  
 La commande **Unlock** supprime un verrou établi dans le contexte de la transaction actuellement active.  
  
> [!IMPORTANT]  
>  Seuls les administrateurs de bases de données ou de serveurs peuvent émettre une commande **Unlock** de manière explicite.  
  
 Tous les verrous sont conservés dans le contexte de la transaction en cours. Lors de la validation ou de la restauration de la transaction en cours, tous les verrous définis dans celle-ci sont libérés automatiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Verrouiller l’élément &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)   
 [Élément Unlock &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)   
 [Développement avec XMLA dans Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
