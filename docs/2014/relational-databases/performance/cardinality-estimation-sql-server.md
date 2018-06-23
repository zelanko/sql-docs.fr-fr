---
title: Évaluation de la cardinalité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 11/24/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cardinality estimator
- CE (cardinality estimator)
- estimating cardinality
ms.assetid: baa8a304-5713-4cfe-a699-345e819ce6df
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.openlocfilehash: 5a81849f65e5b71acf233febb61e7725ec1e804e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042431"
---
# <a name="cardinality-estimation-sql-server"></a>Évaluation de la cardinalité (SQL Server)
  La logique d’estimation de cardinalité, appelée estimateur de cardinalité, est remodelée dans [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] pour améliorer la qualité des plans de requête et par conséquent, pour améliorer les performances des requêtes. Le nouvel estimateur de cardinalité incorpore des hypothèses et des algorithmes qui fonctionnent sur les charges de travail OLTP et de stockage de données modernes. Il repose sur la recherche détaillée des estimations de cardinalité sur les charges de travail modernes et sur nos connaissances acquises au cours des 15 dernières années sur l'amélioration de l'estimateur de cardinalité SQL Server. Les commentaires des clients indiquent que bien que la plupart des requêtes tirent parti des modifications ou demeurent inchangées, un petit nombre d'entre elles présente des régressions par rapport à l'estimateur de cardinalité précédent.  
  
> [!NOTE]  
>  Les estimations de cardinalité sont une prédiction du nombre de lignes dans le résultat de la requête. L'optimiseur de requête utilise ces estimations pour choisir un plan d'exécution de la requête. La qualité du plan de requête a un impact direct sur l'amélioration des performances des requêtes.  
  
## <a name="performance-testing-and-tuning-recommendations"></a>Recommandations pour le test des performances et le paramétrage  
 Le nouvel estimateur de cardinalité est activé pour toutes les nouvelles bases de données créées dans [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. Cependant, la mise à niveau vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] n'active pas le nouvel estimateur de cardinalité dans les bases de données existantes.  
  
 Pour obtenir les meilleures performances des requêtes, utilisez ces recommandations pour tester votre charge de travail avec le nouvel estimateur de cardinalité avant de l'activer sur votre système de production.  
  
1.  Mettez à niveau toutes les bases de données existantes pour utiliser le nouvel estimateur de la cardinalité. Pour ce faire, utilisez [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) pour définir le niveau de compatibilité de base de données à 120.  
  
2.  Exécutez votre test de charge de travail avec le nouvel estimateur de cardinalité, puis résolvez les nouveaux problèmes de performances de la même façon que les problèmes de performances.  
  
3.  Une fois que votre charge de travail est en cours d’exécution avec le nouvel estimateur de cardinalité (niveau de compatibilité de la base de données (SQL Server 2014) de 120) et une requête spécifique a régressé, vous pouvez exécuter la requête avec l’indicateur de trace 9481 pour utiliser la version de l’estimateur de cardinalité utilisé dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]et les versions antérieures. Pour exécuter une requête avec un indicateur de trace, consultez l'article de la Base de connaissances [Activer un plan affectant le comportement de l'optimiseur de requête SQL Server qui peut être contrôlé par des indicateurs de trace différents à un niveau spécifique à une requête](http://support.microsoft.com/kb/2801413).  
  
4.  Si vous ne pouvez pas modifier toutes les bases de données à la fois pour utiliser le nouvel estimateur de cardinalité, vous pouvez utiliser l’estimateur de cardinalité précédent pour toutes les bases de données à l’aide de [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) à définir le niveau de compatibilité de base de données à 110.  
  
5.  Si votre charge de travail s’exécute avec le niveau de compatibilité de la base de données 110 et que vous voulez tester ou exécuter une requête spécifique avec le nouvel estimateur de cardinalité, exécutez la requête avec l’indicateur de trace 2312 pour utiliser la version SQL Server 2014 de l’estimateur de cardinalité.  Pour exécuter une requête avec un indicateur de trace, consultez l'article de la Base de connaissances [Activer un plan affectant le comportement de l'optimiseur de requête SQL Server qui peut être contrôlé par des indicateurs de trace différents à un niveau spécifique à une requête](http://support.microsoft.com/kb/2801413).  
  
## <a name="new-xevents"></a>Nouveaux XEvents  
 Il y a deux nouveaux XEvents query_optimizer_estimate_cardinality pour prendre en charge les nouveaux plans de requête.  
  
-   *query_optimizer_estimate_cardinality* se produit lorsque l'optimiseur de requête estime la cardinalité sur une expression relationnelle.  
  
-   *query_optimizer_force_both_cardinality_estimation*_behaviors se produit lorsque les deux indicateurs de trace 2312 et 9481 sont activés, tentant de forcer l'ancien et le nouveau comportement d'estimation de cardinalité en même temps.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants illustrent certaines des modifications apportées aux nouvelles estimations de cardinalité. Le code d'estimation de la cardinalité a été réécrit. La logique est complexe et il est impossible de fournir une liste exhaustive de toutes les modifications.  
  
> [!NOTE]  
>  Ces exemples sont fournis en tant qu'informations conceptuelles. Aucune action n'est requise de votre part pour modifier la manière dont vous concevez les bases de données et les requêtes.  
  
### <a name="example-a-new-cardinality-estimates-use-an-average-cardinality-for-recently-added-ascending-data"></a>Exemple A. Les nouvelles estimations de cardinalité utilisent une cardinalité moyenne pour les données croissantes ajoutées récemment.  
 Cet exemple montre comment le nouvel estimateur de cardinalité peut améliorer les estimations de cardinalité pour les données croissantes qui dépassent la valeur maximale dans la table pendant la mise à jour des statistiques la plus récente.  
  
```  
SELECT item, category, amount FROM dbo.Sales AS s WHERE Date = '2013-12-19';  
```  
  
 Dans cet exemple, de nouvelles lignes sont ajoutées à la table Ventes chaque jour, la requête demande les données des ventes qui se sont produites le 19/12/2013, et la dernière mise à jour des statistiques a été effectuée le 18/12/2013. L'estimateur de cardinalité précédent suppose que les valeurs du 19/12/2013 n'existent pas, car la date dépasse la date maximale et les statistiques n'ont pas été mises à jour pour inclure les valeurs du 19/12/2013. Cette situation, appelée problème de clé croissante, se produit lorsque vous chargez des données au cours de la journée, puis exécutez des requêtes sur les données avant de mettre à jour les statistiques.  
  
 Ce comportement a changé. Maintenant, même si les statistiques n'ont pas été mises à jour pour les données croissantes les plus récentes ajoutées depuis la dernière mise à jour des statistiques, le nouvel estimateur de cardinalité suppose que les valeurs existent et utilise la cardinalité moyenne de chaque valeur dans la colonne comme estimation de la cardinalité.  
  
### <a name="example-b-new-cardinality-estimates-assume-filtered-predicates-on-the-same-table-have-some-correlation"></a>Exemple B. Les nouvelles estimations de cardinalité supposent que les prédicats filtrés sur la même table ont une certaine corrélation.  
 Pour cet exemple, supposons que la table Cars contient 1 000 lignes, la colonne Make contient 200 correspondances pour « Honda », la colonne Model contient 50 correspondances pour « Civic » et que tous les modèles Civic sont de marque Honda. Par conséquent, 20 % des valeurs de la colonne Make correspondent à « Honda », 5 % des valeurs de la colonne Model correspondent à « Civic » et le nombre réel de Civic honda est 50. Les estimations de cardinalité précédentes supposent que les valeurs des colonnes Make et Model sont indépendantes. L’optimiseur de requête précédent estime il n’y a 10 Honda Civic (.05 *.20 \* 1000 lignes = 10 lignes).  
  
```  
SELECT year, purchase_price FROM dbo.Cars WHERE Make = 'Honda' AND Model = 'Civic';  
```  
  
 Ce comportement a changé. Maintenant, les nouvelles estimations de cardinalité supposent que les colonnes Make et Model ont une *certaine* corrélation. L'optimiseur de requête estime une cardinalité plus élevée en ajoutant un composant exponentiel à l'équation d'estimation. L’optimiseur de requête estime maintenant que 22,36 lignes (.05 * SQRT(.20) \* 1000 lignes = 22,36 lignes) correspondent au prédicat. Pour ce scénario et cette distribution de données spécifique, 22,36 lignes est le résultat le proche des 50 lignes réelles qui sera retourné par la requête.  
  
 Notez que la logique du nouvel estimateur de cardinalité trie les sélectivités de prédicat et augmente l'exposant. Par exemple, si les sélectivités de prédicats sont. 05,.20 et.25, l’estimation de cardinalité est (.05 * SQRT(.20) \* SQRT(SQRT(.25))).  
  
### <a name="example-c-new-cardinality-estimates-assume-filtered-predicates-on-different-tables-are-independent"></a>Exemple C. Les nouvelles estimations de cardinalité supposent que les prédicats filtrés sur les tables sont indépendants.  
 Pour cet exemple, l'estimateur de cardinalité précédent suppose que les filtres de prédicat s.type et r.date sont corrélés. Toutefois, les résultats du test sur les charges de travail modernes indiquent que les filtres de prédicat sur les colonnes de différentes tables ne sont généralement pas corrélés.  
  
```  
SELECT s.ticket, s.customer, r.store FROM dbo.Sales AS s CROSS JOIN dbo.Returns AS r  
WHERE s.ticket = r.ticket AND s.type = 'toy' AND r.date = '2013-12-19';  
```  
  
 Ce comportement a changé. Maintenant, la logique du nouvel estimateur de cardinalité suppose que s.type n'est pas mis en corrélation avec r.date. En pratique, l'hypothèse est que les jouets sont retournés tous les jours et non un seul jour spécifique. Dans ce cas, les nouvelles estimations de cardinalité sont un nombre inférieur aux estimations de cardinalité précédentes.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller et régler les performances](monitor-and-tune-for-performance.md)  
  
  
