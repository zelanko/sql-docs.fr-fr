---
title: Exclure les doublons de lignes (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 63ec11b8575017ffbb3a1b1468ef3150a20326e2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63028348"
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a>Exclure les doublons de lignes (Visual Database Tools)
  Si vous souhaitez afficher uniquement des valeurs uniques dans un jeu de résultats, vous pouvez spécifier qu'il faut exclure les doublons du jeu de résultats.  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a>Pour exclure les doublons du jeu de résultats  
  
1.  Cliquez avec le bouton droit sur un point de l’arrière-plan du volet Schéma, puis choisissez **Propriétés** dans le menu contextuel.  
  
2.  Dans la fenêtre Propriétés, cliquez sur **Valeurs DISTINCT** et affectez-lui la valeur **Oui**.  
  
     Le Concepteur de requêtes et de vues insère le mot clé DISTINCT devant la liste des colonnes affichées dans l'instruction SQL.  
  
    > [!NOTE]  
    >  Si vous utilisez le mot clé DISTINCT, il se peut que vous ne puissiez pas modifier le jeu de résultats dans le volet Résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifiez les critères de recherche &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Trier et regrouper des résultats de requête &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)  
  
  
