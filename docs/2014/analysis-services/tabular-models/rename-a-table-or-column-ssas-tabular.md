---
title: Renommer une Table ou une colonne (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.renametableorcolumn.f1
ms.assetid: 88061a39-c5aa-403d-a52b-7fdb365fc235
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4f9a869b4a280f8df44fce4c506c5f77afc7e8f9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62756634"
---
# <a name="rename-a-table-or-column-ssas-tabular"></a>Renommer une table ou une colonne (SSAS Tabulaire)
  Vous pouvez modifier le nom d'une table pendant le processus d'importation en tapant un **Nom convivial** dans la page **Sélectionner des tables et des vues** de l' **Assistant Importation de table**. Vous pouvez également changer le nom des tables et des colonnes si vous importez des données en spécifiant une requête dans la page **Spécifier une requête SQL** de l' **Assistant Importation de table**.  
  
 Une fois que vous avez ajouté les données au modèle, le nom (ou le titre) d'une table s'affiche sous l'onglet Table, au bas du générateur de modèles. Vous pouvez changer le nom de votre table afin de lui donner un nom plus approprié. Vous pouvez également renommer une colonne après l’ajout de données au classeur. Cette option est notamment importante lorsque vous avez importé des données à partir de plusieurs sources et souhaitez vous assurer que les colonnes dans les différentes tables ont des noms qui sont faciles à distinguer.  
  
### <a name="to-rename-a-table"></a>Pour renommer une table  
  
1.  Dans le générateur de modèles, cliquez avec le bouton droit sur l’onglet contenant la table que vous souhaitez renommer, puis sélectionnez **Renommer**.  
  
2.  Tapez le nouveau nom.  
  
    > [!NOTE]  
    >  Vous pouvez modifier d'autres propriétés d'une table, notamment les mappages de colonnes et les informations de connexion, en utilisant la boîte de dialogue **Modifier les propriétés de la table** . Toutefois, vous ne pouvez pas changer son nom dans cette boîte de dialogue.  
  
### <a name="to-rename-a-column"></a>Pour renommer une colonne  
  
1.  Dans le générateur de modèles, double-cliquez sur l’en-tête de la colonne que vous souhaitez renommer ou cliquez dessus avec le bouton droit et sélectionnez **Renommer la colonne** dans le menu contextuel.  
  
2.  Tapez le nouveau nom.  
  
## <a name="naming-requirements-for-columns-and-tables"></a>Exigences concernant l'affectation de noms pour les colonnes et les tables  
 Les mots et caractères suivants ne peuvent pas être utilisés dans le nom d'une table ou d'une colonne :  
  
-   Espaces à gauche ou à droite  
  
-   Caractères de contrôle  
  
-   Les caractères suivants (qui ne sont pas valides dans les noms d’objets Analysis Services) :., ' : / \\*|? & % $! [] de () +={}<>  
  
-   Mots clés réservés Analysis Services, notamment les opérateurs et les noms de fonction MDX et DMX.  
  
## <a name="effect-of-renaming-on-existing-tables-columns-and-calculations"></a>Effet de l'attribution d'un nouveau nom sur les tables existantes, les colonnes et les calculs  
 Chaque fois que vous modifiez le nom d'une table, vous modifiez le nom de l'objet de table sous-jacente, qui peut contenir plusieurs colonnes ou mesures. Par conséquent, toutes les colonnes qui figurent dans la table, ainsi que toutes les relations qui utilisent la table, doivent être mises à jour pour utiliser le nouveau nom dans leurs définitions. Cette mise à jour se produit automatiquement dans certains cas. Les mesures ne sont pas mises à jour automatiquement.  
  
 De plus, tous les calculs qui utilisent la table renommée, ou qui utilisent des colonnes de la table que vous avez renommée, doivent également être mis à jour, et les données dérivées de ces calculs doivent être actualisées et recalculées. Selon le nombre de tables et de calculs affectés, cette opération peut prendre quelque temps. Par conséquent, le meilleur moment pour renommer des tables est soit pendant le processus d'importation, soit avant de commencer à générer des relations et des calculs complexes.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et colonnes &#40;SSAS Tabulaire&#41;](tables-and-columns-ssas-tabular.md)   
 [Importation à partir de PowerPivot &#40;SSAS tabulaire&#41;](import-from-power-pivot-ssas-tabular.md)   
 [Importer à partir d’Analysis Services &#40;SSAS Tabulaire&#41;](import-from-analysis-services-ssas-tabular.md)  
  
  
