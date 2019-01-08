---
title: Sous-expression commune est expliqué dans Analytique Platform System | Microsoft Docs
description: Amélioration de requête d’exemple affiche qui a été introduite dans CU7.3 de système de plateforme Analytique
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 12/17/2018
ms.author: murshedz
ms.reviewer: martinle
monikerRange: '>= aps-pdw-2016-au7 || = sqlallproducts-allversions'
ms.openlocfilehash: 2dd02bed55f3d3781428eae3ec4bc2d0655819ab
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53597303"
---
# <a name="common-subexpression-elimination-explained"></a>Élimination de sous-expressions communes expliquée

APS CU7.3 améliore les performances de requête avec élimination de sous-expressions communes dans l’optimiseur de requête SQL. L’amélioration améliore les requêtes de deux manières. Le premier, c’est la capacité à identifier et éliminer ces expressions permettent de réduire le temps de compilation SQL. L’avantage de la deuxième et le plus important est les opérations de déplacement de données pour ces sous-expressions redondantes sont éliminées ainsi les temps d’exécution de requêtes devient plus rapide.

```sql
select top 100 asceding.rnk, i1.i_product_name best_performing, i2.i_product_name worst_performing
  from(select *
       from (select item_sk,rank() over (order by rank_col asc) rnk
             from (select ss_item_sk item_sk,avg(ss_net_profit) rank_col
                   from store_sales ss1
                   where ss_store_sk = 8
                   group by ss_item_sk
                   having avg(ss_net_profit) > 0.9*(select avg(ss_net_profit) rank_col
                                                    from store_sales
                                                    where ss_store_sk = 8
                                                      and ss_hdemo_sk is null
                                                    group by ss_store_sk))V1)V11
       where rnk  < 11) asceding,
      (select *
       from (select item_sk,rank() over (order by rank_col desc) rnk
             from (select ss_item_sk item_sk,avg(ss_net_profit) rank_col
                   from store_sales ss1
                   where ss_store_sk = 8
                   group by ss_item_sk
                   having avg(ss_net_profit) > 0.9*(select avg(ss_net_profit) rank_col
                                                    from store_sales
                                                    where ss_store_sk = 8
                                                      and ss_hdemo_sk is null
                                                    group by ss_store_sk))V2)V21
       where rnk  < 11) descending,
  item i1,
  item i2
  where asceding.rnk = descending.rnk
    and i1.i_item_sk=asceding.item_sk
    and i2.i_item_sk=descending.item_sk
  order by asceding.rnk
  ;
```
Considérez la requête ci-dessus à partir des outils de banc d’essai TPC-DS.  Dans la requête ci-dessus, la sous-requête est identique, mais la clause order by avec rank() sur la fonction est triée de deux manières différentes. Antérieures à CU7.3, cette sous-requête obtient évaluée et exécutée à deux reprises, une fois pour l’ordre croissant et qu’une seule fois pour l’ordre décroissant, encourir deux opérations de déplacement de données. Après avoir installé CU7.3 de points d’accès, la partie de la sous-requête sera évaluée une seule fois par conséquent, ce qui réduit le déplacement des données et la fin de la requête plus rapide.

Nous avons introduit un [commutateur de fonctionnalité](appliance-feature-switch.md) appelé « OptimizeCommonSubExpressions » qui permettra de vous testez la fonctionnalité même après une migration vers CU7.3 de points d’accès. La fonctionnalité est activée par défaut mais peut être désactivée. 

> [!NOTE] 
> Modifications apportées aux valeurs de commutateur de fonctionnalité requièrent un redémarrage du service.

Vous pouvez essayer l’exemple de requête en créant les tables suivantes dans votre environnement de test et en évaluant le plan explain pour la requête mentionnée ci-dessus. 

```sql
CREATE TABLE [dbo].[store_sales] (
    [ss_sold_date_sk] int NULL, 
    [ss_sold_time_sk] int NULL, 
    [ss_item_sk] int NOT NULL, 
    [ss_customer_sk] int NULL, 
    [ss_cdemo_sk] int NULL, 
    [ss_hdemo_sk] int NULL, 
    [ss_addr_sk] int NULL, 
    [ss_store_sk] int NULL, 
    [ss_promo_sk] int NULL, 
    [ss_ticket_number] int NOT NULL, 
    [ss_quantity] int NULL, 
    [ss_wholesale_cost] decimal(7, 2) NULL, 
    [ss_list_price] decimal(7, 2) NULL, 
    [ss_sales_price] decimal(7, 2) NULL, 
    [ss_ext_discount_amt] decimal(7, 2) NULL, 
    [ss_ext_sales_price] decimal(7, 2) NULL, 
    [ss_ext_wholesale_cost] decimal(7, 2) NULL, 
    [ss_ext_list_price] decimal(7, 2) NULL, 
    [ss_ext_tax] decimal(7, 2) NULL, 
    [ss_coupon_amt] decimal(7, 2) NULL, 
    [ss_net_paid] decimal(7, 2) NULL, 
    [ss_net_paid_inc_tax] decimal(7, 2) NULL, 
    [ss_net_profit] decimal(7, 2) NULL
)
WITH (CLUSTERED COLUMNSTORE INDEX, DISTRIBUTION = HASH([ss_item_sk]),  PARTITION ([ss_sold_date_sk] RANGE RIGHT FOR VALUES (2450815, 2451180, 2451545, 2451911, 2452276, 2452641, 2453006)));

CREATE TABLE [dbo].[item] (
    [i_item_sk] int NOT NULL, 
    [i_item_id] char(16) COLLATE Latin1_General_100_CI_AS_KS_WS NOT NULL, 
    [i_rec_start_date] date NULL, 
    [i_rec_end_date] date NULL, 
    [i_item_desc] varchar(200) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_current_price] decimal(7, 2) NULL, 
    [i_wholesale_cost] decimal(7, 2) NULL, 
    [i_brand_id] int NULL, 
    [i_brand] char(50) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_class_id] int NULL, 
    [i_class] char(50) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_category_id] int NULL, 
    [i_category] char(50) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_manufact_id] int NULL, 
    [i_manufact] char(50) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_size] char(20) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_formulation] char(20) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_color] char(20) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_units] char(10) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_container] char(10) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_manager_id] int NULL, 
    [i_product_name] char(50) COLLATE Latin1_General_100_CI_AS_KS_WS NULL
)
WITH (CLUSTERED INDEX ( [i_item_sk] ASC ), DISTRIBUTION = REPLICATE);
```
Si vous examinez le plan explain de la requête, vous verrez qu’avant CU7.3 (ou lorsque le commutateur de fonctionnalité est désactivée) la requête a 17 nombre total d’opérations et après CU7.3 (ou avec le commutateur de fonctionnalité activée) la même requête montre 9 nombre total d’opérations. Si vous ne comptez que les opérations de déplacement des données, vous verrez que le plan précédent a quatre opérations de déplacement et deux opérations de déplacement dans le nouveau plan. Le nouvel optimiseur de requête a été en mesure de réduire les deux opérations de déplacement de données en réutilisant la table temporaire, il est déjà créé avec le nouveau plan, ce qui réduit le runtime de requête. 


