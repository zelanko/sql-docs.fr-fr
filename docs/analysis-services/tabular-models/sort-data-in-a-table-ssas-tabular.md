---
title: "Trier les données dans une Table (SSAS tabulaire) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fa6ad56-bf68-4aac-a226-52556173b7e2
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f4fff0e8e215cd9c5c656de99da221023c45c807
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="sort-data-in-a-table-ssas-tabular"></a>Trier des données dans une table (SSAS Tabulaire)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Vous pouvez trier les données en texte (de A à Z ou de Z à A) et des nombres (du plus petit au plus grand ou du plus grand au plus petit) dans une ou plusieurs colonnes.  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-text-column"></a>Pour trier les données dans une table selon une colonne de texte  
  
1.  Dans le générateur de modèles, sélectionnez une colonne de données alphanumériques, une plage de cellules dans une colonne ou assurez-vous que la cellule active se trouve dans une colonne de table qui contient des données alphanumériques, puis cliquez sur la flèche dans l'en-tête de la colonne d'après lequel effectuer le filtrage.  
  
2.  Dans le menu Filtre automatique, effectuez l'une des opérations suivantes :  
  
    -   Pour trier par ordre alphanumérique croissant, cliquez sur **Trier de A à Z**.  
  
    -   Pour trier par ordre alphanumérique décroissant, cliquez sur **Trier de Z à A**.  
  
    > [!NOTE]  
    >  Dans certains cas, les données importées à partir d'une autre application peuvent comporter des espaces de début. Vous devez supprimer ces espaces de début afin de pouvoir trier correctement les données.  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-numeric-column"></a>Pour trier les données dans une table selon une colonne numérique  
  
1.  Dans le générateur de modèles, sélectionnez une colonne de données alphanumériques, une plage de cellules dans une colonne ou assurez-vous que la cellule active se trouve dans une colonne de table qui contient des données alphanumériques, puis cliquez sur la flèche dans l'en-tête de la colonne d'après lequel effectuer le filtrage.  
  
2.  Dans le menu Filtre automatique, effectuez l'une des opérations suivantes :  
  
    -   Pour trier par ordre croissant, cliquez sur **Trier du plus petit au plus grand**.  
  
    -   Pour trier par ordre décroissant, cliquez sur **Trier du plus grand au plus petit**.  
  
    > [!NOTE]  
    >  Si les résultats ne sont pas ce attendus, il se peut que la colonne contienne des nombres stockés sous forme de texte plutôt que sous forme de nombres. Par exemple, les nombres négatifs importés à partir de certains logiciels de comptabilité ou un nombre entré avec un signe ' (apostrophe) de début sont stockés sous forme de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Filtrer et trier les données &#40;SSAS tabulaire&#41;](http://msdn.microsoft.com/library/55ebd7a6-2458-4398-911f-fcfeb2413f1b)   
 [Perspectives &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Rôles &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
