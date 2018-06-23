---
title: Créer des requêtes Update (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tables [SQL Server], updating
- queries [SQL Server], types
- Update query
- updating tables
ms.assetid: 178b7b75-8078-4e61-b2a8-4719b9d8033d
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 666c467a44692db34e5996435efd7eb61b8b62bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040996"
---
# <a name="create-update-queries-visual-database-tools"></a>Créer des requêtes Update (Visual Database Tools)
  Vous pouvez modifier le contenu de plusieurs lignes en une seule opération à l'aide d'une requête Update. Dans une table `titles` par exemple, vous pouvez recourir à une requête Update pour augmenter de 10% le prix de tous les livres d'un éditeur donné.  
  
 Lorsque vous créez une requête Update, spécifiez :  
  
-   la table à mettre à jour ;  
  
-   les colonnes dont vous voulez mettre à jour le contenu ;  
  
-   la valeur ou l'expression utilisée pour mettre à jour les colonnes individuelles ;  
  
-   les conditions de recherche afin de définir les lignes à mettre à jour.  
  
 À titre d'exemple, la requête suivante met à jour la table `titles` en augmentant de 10% le prix de tous les titres d'un éditeur :  
  
```  
UPDATE titles  
SET price = price * 1.1  
WHERE (pub_id = '0766')  
```  
  
> [!CAUTION]  
>  Il est impossible d'annuler l'action entraînée par l'exécution d'une requête Update. Par sécurité, sauvegardez vos données avant d'exécuter la requête.  
  
### <a name="to-create-an-update-query"></a>Pour créer une requête Update  
  
1.  Ajoutez la table à mettre à jour dans le volet Schéma.  
  
2.  Dans le menu **Concepteur de requêtes** , pointez sur **Modifier le type**, puis cliquez sur **Mettre à jour**.  
  
    > [!NOTE]  
    >  Si plusieurs tables apparaissent dans le volet Schéma quand vous commencez la requête Update, le Concepteur de requêtes et de vues affiche la boîte de dialogue [Choisir la table cible pour Insert Values](visual-database-tools.md) qui vous invite à indiquer le nom de la table à mettre à jour.  
  
3.  Dans le volet Schéma, cliquez sur la case à cocher en regard de chaque colonne pour laquelle vous souhaitez fournir de nouvelles valeurs. Ces colonnes s'affichent dans le volet Critères. Les colonnes ne seront mises à jour que si vous les ajoutez à la requête.  
  
4.  Dans la colonne **Nouvelle valeur** du volet Critères, entrez la valeur mise à jour de la colonne. Vous pouvez entrer des valeurs littérales, des noms de colonnes ou des expressions. La valeur doit correspondre (ou être compatible) au type de données de la colonne mise à jour.  
  
    > [!CAUTION]  
    >  Le Concepteur de requêtes et de vues ne peut pas vérifier si une valeur est adaptée à la longueur de la colonne que vous mettez à jour. Si la valeur est trop longue, elle est susceptible d'être tronquée sans avertissement. Par exemple, si une colonne `name` possède 20 caractères mais que vous spécifiez une valeur de mise à jour de 25 caractères, les derniers 5 caractères risquent d'être tronqués.  
  
5.  Définissez les lignes à mettre à jour en entrant des conditions de recherche dans la colonne **Filtre**. Pour plus d’informations, consultez [Spécifier des critères de recherche &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).  
  
     Si vous ne spécifiez pas de condition de recherche, toutes les lignes de la table spécifiée sont mises à jour.  
  
    > [!NOTE]  
    >  Quand vous ajoutez une colonne dans le volet Critères afin de l'utiliser dans une condition de recherche, le Concepteur de requêtes et de vues l'ajoute aussi à la liste des colonnes à mettre à jour. Si vous souhaitez utiliser une colonne dans une condition de recherche sans toutefois la mettre à jour, désactivez la case à cocher en regard du nom de la colonne dans le rectangle représentant la table ou l'objet table.  
  
 Quand vous exécutez une requête Update, aucun résultat n’apparaît dans le [volet Résultats](results-pane-visual-database-tools.md). En fait, un message indiquant le nombre de lignes modifiées s'affiche.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des Types de requêtes &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md)   
 [Rubriques de procédures de requêtes et les vues de conception &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Effectuer des opérations de base concernant les requêtes &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  