---
title: Trier des données dans une table (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fa6ad56-bf68-4aac-a226-52556173b7e2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fc53b6ccc800e2986bf7a6bfdd01c0ef3c3208df
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66066660"
---
# <a name="sort-data-in-a-table-ssas-tabular"></a>Trier des données dans une table (SSAS Tabulaire)
  Vous pouvez trier des données en fonction du texte (de A à Z ou de Z à A) ou des nombres (du plus petit au plus grand ou du plus grand au plus petit) dans une ou plusieurs colonnes.  
  
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
 [Filtrer et trier des données &#40;la&#41;tabulaire SSAS](../filter-and-sort-data-ssas-tabular.md)   
 [Perspectives &#40;&#41;tabulaire SSAS](perspectives-ssas-tabular.md)   
 [Rôles &#40;&#41;tabulaire SSAS](roles-ssas-tabular.md)  
  
  
