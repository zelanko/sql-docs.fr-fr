---
title: Trier des données pour les transformations de fusion et de jointure de fusion | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sort attributes [Integration Services]
- output columns [Integration Services]
ms.assetid: 22ce3f5d-8a88-4423-92c2-60a8f82cd4fd
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 375f268eecba7c519941f4743d7396346a863f50
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151942"
---
# <a name="sort-data-for-the-merge-and-merge-join-transformations"></a>Trier des données pour les transformations de fusion et de jointure de fusion
  Dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], les transformations de fusion et de jointure de fusion nécessitent des données triées pour leurs entrées. Les données d'entrée doivent être triés physiquement et les options de tri doivent être définies sur les sorties et les colonnes de sortie dans la source ou dans la transformation amont. Si les options de tri indiquent que les données sont triées alors qu'elles ne le sont pas en réalité, les résultats de l'opération de fusion ou de jointure de fusion sont imprévisibles.  
  
## <a name="sorting-the-data"></a>Tri des données  
 Pour trier ces données, procédez selon l'une des méthodes suivantes :  
  
-   Dans la source, utilisez une clause ORDER BY dans l'instruction utilisée pour charger les données.  
  
-   Dans le flux de données, insérez une transformation de tri avant la transformation de fusion ou de jointure de fusion.  
  
 Si les données sont des données de chaînes, les transformations de fusion ou de jointure de fusion requièrent que ces valeurs de chaîne soient triées en utilisant le classement Windows. Pour fournir des valeurs de chaîne aux transformations de fusion et de jointure de fusion triées à l'aide du classement Windows, procédez comme suit :  
  
#### <a name="to-provide-string-values-that-are-sorted-by-using-windows-collation"></a>Pour fournir des valeurs de chaîne triées à l'aide du classement Windows  
  
-   Utilisez une transformation de tri pour trier les données.  
  
     La transformation de tri utilise le classement Windows pour trier les valeurs de chaîne.  
  
     —ou—  
  
-   Utilisez l'opérateur Transact-SQL CAST pour commencer par effectuer un cast des valeurs `varchar` en valeurs `nvarchar`, puis utilisez la clause Transact-SQL ORDER BY pour trier les données.  
  
    > [!IMPORTANT]  
    >  Vous ne pouvez pas utiliser la clause ORDER BY seule parce qu'elle utilise un classement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour trier les valeurs de chaîne. L’utilisation du classement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut générer un ordre de tri différent du classement Windows, la transformation de fusion ou de jointure de fusion pouvant alors générer des résultats inattendus.  
  
## <a name="setting-sort-options-on-the-data"></a>Définition d'options de tri sur les données  
 Deux propriétés de tri importantes doivent être définies pour la source ou la transformation amont qui fournit des données aux transformations de fusion et de jointure de fusion :  
  
-   La propriété `IsSorted` de la sortie qui indique si les données ont été triées. Cette propriété doit être définie `True`.  
  
    > [!IMPORTANT]  
    >  Définition de la valeur de la `IsSorted` propriété `True` ne trie pas les données. Cette propriété indique uniquement aux composants en aval que les données ont été précédemment triées.  
  
-   Le `SortKeyPosition` propriété des colonnes de sortie qui indique si une colonne est triée, l’ordre de tri et l’ordre dans lequel plusieurs colonnes sont triées. Cette propriété doit être définie pour chaque colonne de données triées.  
  
 Si vous utilisez une transformation de tri pour trier les données, elle définit ces deux propriétés tel que requis par la transformation de fusion ou de jointure de fusion. Autrement dit, la transformation de tri définit les `IsSorted` propriété de sa sortie à `True`et définit le `SortKeyPosition` propriétés de ses colonnes de sortie.  
  
 Toutefois, si vous n'utilisez pas de transformation de tri pour trier les données, vous devez définir ces propriétés de tri manuellement sur la source ou la transformation amont. Pour définir manuellement les propriétés de tri sur la source ou la transformation en amont, appliquez la procédure suivante.  
  
#### <a name="to-manually-set-sort-attributes-on-a-source-or-transformation-component"></a>Pour définir manuellement des attributs de tri sur un composant source ou de transformation  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Sous l’onglet **Flux de données** , recherchez la source ou la transformation en amont appropriée, ou faites-la glisser de la **Boîte à outils** vers l’aire de conception.  
  
4.  Cliquez avec le bouton droit sur le composant, puis cliquez sur **Afficher l’éditeur avancé**.  
  
5.  Cliquez sur l'onglet **Propriétés d'entrée et de sortie** .  
  
6.  Cliquez sur  **\<nom du composant > sortie**et définissez la `IsSorted` propriété `True`.  
  
    > [!NOTE]  
    >  Si vous définissez manuellement la `IsSorted` propriété de la sortie à `True` et les données ne sont pas triées, il manque peut-être données ou les comparaisons de données incorrectes dans la transformation de fusion ou de jointure de fusion en aval lorsque vous exécutez le package.  
  
7.  Développez **Colonnes de sortie**.  
  
8.  Cliquez sur la colonne que vous souhaitez indiquer est triée et définissez son `SortKeyPosition` propriété à une valeur entière différente de zéro en suivant ces instructions :  
  
    -   La valeur entière doit représenter une séquence numérique, partant de 1 et incrémentée de 1.  
  
    -   Une valeur entière positive indique un ordre de tri croissant.  
  
    -   Une valeur entière négative indique un ordre de tri décroissant. (Si un nombre négatif est défini, la valeur absolue du nombre détermine la position de la colonne dans la séquence de tri.)  
  
    -   Une valeur par défaut de 0 indique que la colonne n'est pas triée. Laissez la valeur 0 pour les colonnes de sortie qui ne participent pas au tri.  
  
     Comme exemple de définition de la propriété `SortKeyPosition`, prenons l'instruction Transact-SQL suivante qui charge des données dans une source.  
  
     `SELECT * FROM MyTable ORDER BY ColumnA, ColumnB DESC, ColumnC`  
  
     Pour cette instruction, vous devez définir le `SortKeyPosition` propriété pour chaque colonne comme suit :  
  
    -   Définissez la propriété `SortKeyPosition` de ColumnA à 1. Cela indique que ColumnA est la première colonne à trier et dans l'ordre croissant.  
  
    -   Définissez la propriété `SortKeyPosition` de ColumnB à -2. Cela indique que ColumnB est la deuxième colonne à trier et dans l'ordre décroissant.  
  
    -   Définir le `SortKeyPosition` propriété de ColumnC à 3. Cela indique que ColumnC est la troisième colonne à trier et dans l'ordre croissant.  
  
9. Répétez l'étape 8 pour chaque colonne triée.  
  
10. Cliquez sur **OK**.  
  
11. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Transformation de fusion](merge-transformation.md)   
 [Transformation de jointure de fusion](merge-join-transformation.md)   
 [Transformations Integration Services](integration-services-transformations.md)   
 [Chemins Integration Services](../integration-services-paths.md)   
 [Tâche de flux de données] ((.. /.. /Control-Flow/Data-Flow-Task.MD)  
  
  