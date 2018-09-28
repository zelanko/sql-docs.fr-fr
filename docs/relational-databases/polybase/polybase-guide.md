---
title: Guide de PolyBase | Microsoft Docs
ms.date: 05/31/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: polybase
ms.tgt_pltfrm: ''
ms.topic: quickstart
f1_keywords:
- PolyBase
- PolyBase, guide
helpviewer_keywords:
- PolyBase
- PolyBase, overview
- Hadoop import
- Hadoop export
- Hadoop export, PolyBase overview
- Hadoop import, PolyBase overview
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c31f9538f3429ff4ae1182ee0cd974996cc705a6
ms.sourcegitcommit: 82bb56269faf3fb5dd1420418e32a0a6476780cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43694722"
---
# <a name="polybase-guide"></a>Guide de PolyBase

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]

PolyBase permet à une instance SQL Server 2016 de traiter des requêtes Transact-SQL qui lisent des données provenant d’Hadoop. Cette même requête peut aussi accéder aux tables relationnelles SQL Server. PolyBase lui permet de joindre également les données issues de Hadoop et de SQL Server. Dans SQL Server, c’est une [table externe](../../t-sql/statements/create-external-table-transact-sql.md) ou une [source de données externe](../../t-sql/statements/create-external-data-source-transact-sql.md) qui assure la connexion à Hadoop.

PolyBase propose ces fonctionnalités pour les produits SQL de Microsoft suivants :

- SQL Server 2016 et versions ultérieures ;
- Analytics Platform System (anciennement Parallel Data Warehouse) ;
- Azure SQL Data Warehouse.

PolyBase envoie certains calculs au nœud Hadoop pour optimiser la requête globale. Toutefois, l’accès externe PolyBase n’est pas limité à Hadoop. D’autres tables non relationnelles et non structurées sont également prises en charge, comme les fichiers texte délimités.

#### <a name="data-import-and-export"></a>Importation et exportation de données

Avec l’aide sous-jacente de PolyBase, les requêtes T-SQL peuvent également importer et exporter des données dans le Stockage Blob Azure. Par ailleurs, PolyBase permet à Azure SQL Data Warehouse d’importer et d’exporter des données dans Azure Data Lake Storage et le Stockage Blob Azure.

Pour utiliser PolyBase, voir [Bien démarrer avec PolyBase](../../relational-databases/polybase/get-started-with-polybase.md).
  
![Logique de PolyBase](../../relational-databases/polybase/media/polybase-logical.png "Logique de PolyBase")

## <a name="why-use-polybase"></a>Pourquoi utiliser PolyBase ?

Il était auparavant plus difficile de joindre des données SQL Server avec des données externes. Deux possibilités existaient, mais elles n’étaient pas pratiques :

- transférer la moitié des données afin que toutes soient au même format ;
- interroger les deux sources de données, puis écrire une logique de requête personnalisée pour joindre et intégrer les données au niveau du client.

PolyBase permet d’éviter ces deux solutions contraignantes en utilisant T-SQL pour joindre les données.

En termes simples, PolyBase dispense d’installer des logiciels supplémentaires dans l’environnement Hadoop. On interroge les données externes suivant la même syntaxe T-SQL que pour une table de base de données. Toutes les actions implémentées par PolyBase se produisent en toute transparence. L’auteur de la requête n’a pas besoin de connaître Hadoop.

PolyBase offre les fonctionnalités suivantes :

- **Interrogation des données stockées dans Hadoop à partir de SQL Server ou PDW.** Les utilisateurs stockent des données dans des systèmes distribués et évolutifs économiques, tels que Hadoop. Avec PolyBase, il est facile d’interroger les données via T-SQL.

- **Interrogation des données stockées dans Stockage Blob Azure.** Pratique, Azure Blob Storage est un emplacement qui permet de stocker les données destinées à être utilisées par les services Azure.  PolyBase permet d’accéder facilement aux données à l’aide de T-SQL.

- **Importation de données provenant d’Hadoop, du Stockage Blob Azure ou d’Azure Data Lake Storage.** Profitez de la rapidité des fonctionnalités d’analyse et de la technologie columnstore de Microsoft SQL en important les données issues d’Hadoop, du Stockage Blob Azure ou d’Azure Data Lake Storage dans des tables relationnelles. Aucun outil d’ETL ou d’importation distinct n’est nécessaire.

- **Exportation de données vers Hadoop, Stockage Blob Azure ou Azure Data Lake Store.** Archivez les données sur Hadoop, Stockage Blob Azure ou Azure Data Lake Store. Vous bénéficierez ainsi d’un mode de stockage économique et vos données resteront en ligne et donc facilement accessibles.

- **Intégration à des outils d’aide à la décision (BI).** Utilisez PolyBase avec la pile d’analyse et d’aide à la décision de Microsoft, ou n’importe quel outil tiers compatible avec SQL Server.

## <a name="performance"></a>Performances

- **Déléguer les calculs à Hadoop.** En fonction des coûts, l’optimiseur de requête prend la décision de déléguer les calculs à Hadoop lorsque cela améliore les performances des requêtes.  Il utilise pour cela des statistiques sur des tables externes. La délégation des calculs a pour effet de créer des tâches MapReduce et de tirer parti des ressources de calcul distribuées de Hadoop.

- **Mise à l’échelle des ressources de calcul.** Pour améliorer les performances des requêtes, vous pouvez utiliser des [groupes de scale-out PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md)SQL Server. Cela autorise un transfert de données en parallèle entre les instances SQL Server et les nœuds Hadoop, et cela ajoute des ressources de calcul qui permettent d’exploiter les données externes.

## <a name="polybase-guide-topics"></a>Rubriques du guide de PolyBase

Ce guide vous propose des rubriques destinées à vous aider à utiliser PolyBase avec efficacité.

|||
|-|-|
|**Rubrique**|**Description**|
|[Prise en main de PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)|Étapes de base pour installer et configurer PolyBase. Cette rubrique vous montre comment créer des objets externes qui pointent vers des données stockées dans Hadoop ou Azure Blob Storage, et propose des exemples de requêtes.|
|[Récapitulatif des fonctionnalités avec version de PolyBase](../../relational-databases/polybase/polybase-versioned-feature-summary.md)|Décrit les fonctionnalités de PolyBase qui sont prises en charge par SQL Server, Base de données SQL et SQL Data Warehouse.|
|[groupes de scale-out PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md)|Faites monter en puissance le parallélisme entre SQL Server et Hadoop au moyen de groupes de scale-out SQL Server.|
|[Installation de PolyBase](../../relational-databases/polybase/polybase-installation.md)|Informations de référence et étapes à suivre pour installer PolyBase avec l’Assistant Installation ou un outil en ligne de commande.|
|[Configuration de PolyBase](../../relational-databases/polybase/polybase-configuration.md)|Configurez les paramètres SQL Server pour PolyBase.  Par exemple, configurez la délégation des calculs et la sécurité kerberos.|
|[Objets T-SQL PolyBase](../../relational-databases/polybase/polybase-t-sql-objects.md)|Créez les objets T-SQL dont se servira PolyBase pour définir et accéder aux données externes.|
|[Requêtes PolyBase](../../relational-databases/polybase/polybase-queries.md)|Utilisez des instructions T-SQL pour interroger, importer ou exporter des données externes.|
|[Résolution des problèmes de Polybase](../../relational-databases/polybase/polybase-troubleshooting.md)|Techniques de gestion des requêtes PolyBase. Utilisez des vues de gestion dynamique (DMV) pour surveiller les requêtes PolyBase, et apprenez à lire un plan de requête PolyBase pour identifier les goulots d’étranglement.|
| &nbsp; | &nbsp; |
  
