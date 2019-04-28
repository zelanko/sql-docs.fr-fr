---
title: Créer des requêtes Insert Values (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting values
- queries [SQL Server], types
- adding values
- row additions [SQL Server], Insert Values query
- inserting rows
- Insert Values query
- adding rows
- table values [SQL Server]
ms.assetid: 2d4b2f6d-cc09-434b-8a0e-ccce40628064
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 019c2fe96be00c6e86e0c94286770d30e7a54a9c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62676336"
---
# <a name="create-insert-values-queries-visual-database-tools"></a>Créer des requêtes Insert Values (Visual Database Tools)
  Vous pouvez créer une nouvelle ligne dans la table active à l'aide d'une requête Insert Values. Lorsque vous créez une requête Insert Values, spécifiez :  
  
-   la table de base de données à laquelle ajouter la ligne ;  
  
-   les colonnes dont vous souhaitez ajouter le contenu ;  
  
-   la valeur ou l'expression à insérer dans les colonnes individuelles.  
  
 Dans l'exemple ci-dessous, la requête ajoute une ligne à la table `titles` , précisant des valeurs pour le titre, le type, l'éditeur et le prix :  
  
```  
INSERT INTO titles  
         (title_id, title, type, pub_id, price)  
VALUES   ('BU9876', 'Creating Web Pages', 'business', '1389', '29.99')  
```  
  
 Lorsque vous créez une requête Insert Values, le volet Critères change afin de refléter les seules options d'insertion d'une nouvelle ligne disponibles : le nom de la colonne et la valeur à insérer.  
  
> [!CAUTION]  
>  Il est impossible d'annuler l'action entraînée par l'exécution d'une requête Insert Values. Par sécurité, sauvegardez vos données avant d'exécuter la requête.  
  
### <a name="to-create-an-insert-values-query"></a>Pour créer une requête Insert Values  
  
1.  Ajoutez la table à mettre à jour dans le volet Schéma.  
  
2.  Dans le menu **Concepteur de requêtes** , pointez sur **Modifier le type**, puis cliquez sur **Insérer les valeurs**.  
  
    > [!NOTE]  
    >  Si plusieurs tables apparaissent dans le volet Schéma quand vous commencez la requête Insert Values, le Concepteur de requêtes et de vues affiche la boîte de dialogue [Choisir la table cible pour Insert Values](visual-database-tools.md) qui vous invite à indiquer le nom de la table à mettre à jour.  
  
3.  Dans le volet Schéma, cliquez sur la case à cocher en regard de chaque colonne pour laquelle vous souhaitez fournir de nouvelles valeurs. Ces colonnes s'affichent dans le volet Critères. Les colonnes ne seront mises à jour que si vous les ajoutez à la requête.  
  
4.  Dans la colonne **Nouvelle valeur** du volet Critères, entrez la nouvelle valeur pour la colonne. Vous pouvez entrer des valeurs littérales, des noms de colonnes ou des expressions. La valeur doit correspondre (ou être compatible) au type de données de la colonne mise à jour.  
  
    > [!CAUTION]  
    >  Le Concepteur de requêtes et de vues ne peut pas vérifier si une valeur est adaptée à la longueur de la colonne que vous insérez. Si la valeur est trop longue, elle est susceptible d'être tronquée sans avertissement. Par exemple, si une colonne `name` possède 20 caractères mais que vous spécifiez une valeur à insérer de 25 caractères, les 5 derniers caractères risquent d'être tronqués.  
  
 Quand vous exécutez une requête Insert Values, aucun résultat n’apparaît dans le [volet Résultats](results-pane-visual-database-tools.md). En fait, un message indiquant le nombre de lignes modifiées s'affiche.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des Types de requêtes &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md)   
 [Concevoir des requêtes et des vues des rubriques de procédures &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Effectuer des opérations de base concernant les requêtes &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
