---
title: Guide de PolyBase | Microsoft Docs
ms.date: 12/08/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-polybase
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- PolyBase
- PolyBase, guide
helpviewer_keywords:
- PolyBase
- PolyBase, overview
- "Hadoop import ×"
- Hadoop export
- Hadoop export, PolyBase overview
- Hadoop import, PolyBase overview
ms.assetid: b42b7d48-328a-4046-abe9-f73fd83212dc
caps.latest.revision: 26
author: barbkess
ms.author: barbkess
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 627fdce2e1c294343680b119e9b0c36fc3d8665d
ms.lasthandoff: 04/11/2017

---
# <a name="polybase-guide"></a>Guide de PolyBase
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  PolyBase est une technologie qui accède aux données aussi bien relationnelles que non relationnelles et les combine dans SQL Server.  Dans SQL Server 2016, elle permet d’exécuter des requêtes sur des données externes dans Hadoop ou Stockage Blob Azure. Les requêtes sont optimisées pour déléguer les calculs à Hadoop. Dans Azure SQL Data Warehouse, vous pouvez importer des données depuis Stockage Blob Azure et Azure Data Lake Store.
  
Utilisez des instructions Transact-SQL (T-SQL) pour importer et exporter des données entre des tables relationnelles SQL Server et des données non relationnelles stockées dans Hadoop ou Stockage Blob Azure. Vous pouvez aussi interroger les données externes à partir d’une requête T-SQL et les joindre à des données relationnelles.  
  
 Pour utiliser PolyBase, consultez [Prise en main de PolyBase](../../relational-databases/polybase/get-started-with-polybase.md).  
  
 ![Logique de PolyBase](../../relational-databases/polybase/media/polybase-logical.png "Logique de PolyBase")  
  
## <a name="why-use-polybase"></a>Pourquoi utiliser PolyBase ?  
Pour prendre de bonnes décisions, il est nécessaire d’analyser des données relationnelles et d’autres données qui ne sont pas structurées dans des tables, telles que les données Hadoop. Il s’agit d’une tâche délicate si vous n’avez pas les moyens de transférer les données entre les différents types de magasins de données. PolyBase comble cette lacune en fonctionnant avec des données externes à SQL Server.  
  
Pour plus de simplicité, PolyBase vous dispense d’installer des logiciels supplémentaires dans votre environnement Azure ou de Hadoop. La syntaxe utilisée pour interroger des données externes est la même que celle utilisée pour interroger une table de base de données. Cela s’effectue en toute transparence. PolyBase gère tous les détails en arrière-plan et son utilisation ne nécessite aucune connaissance de Hadoop ni d’Azure. 
  
 PolyBase offre les fonctionnalités suivantes :  
  
-   **Interrogation des données stockées dans Hadoop.** Les utilisateurs stockent des données dans des systèmes distribués et évolutifs économiques, tels que Hadoop. Avec PolyBase, il est facile d’interroger les données via T-SQL.  
  
-   **Interrogation des données stockées dans Stockage Blob Azure.** Pratique, le service Stockage Blob Azure est un emplacement qui permet de stocker les données destinées à être utilisées par les services Azure.  PolyBase permet d’accéder facilement aux données à l’aide de T-SQL.  
  
-   **Importation des données depuis Hadoop, Stockage Blob Azure ou Azure Data Lake Store.** Profitez de la rapidité des fonctionnalités d’analyse et de la technologie columnstore de Microsoft SQL en important les données de Hadoop, de Stockage Blob Azure ou d’Azure Data Lake Store dans des tables relationnelles. Vous n’avez pas besoin d’un outil ETL ou d’importation distinct.  

  
-   **Exportation de données vers Hadoop, Stockage Blob Azure ou Azure Data Lake Store.** Archivez les données sur Hadoop, Stockage Blob Azure ou Azure Data Lake Store. Vous bénéficierez ainsi d’un mode de stockage économique et vos données resteront en ligne et donc facilement accessibles.  
  
-   **Intégration à des outils d’aide à la décision (BI).** Vous pouvez utiliser PolyBase avec la pile d’analyse et d’aide à la décision de Microsoft ou n’importe quel outil tiers compatible avec SQL Server.  
  
## <a name="performance"></a>Performance  
  
-   **Délégation des calculs à Hadoop.**L’optimiseur de requête prend une décision basée sur les coûts de déléguer les calculs à Hadoop si doit permettre d’améliorer les performances des requêtes.  Il s’appuie sur les statistiques des tables externes pour prendre la décision basée sur les coûts.   La délégation des calculs a pour effet de créer des tâches MapReduce et de tirer parti des ressources de calcul distribuées de Hadoop.  
  
-   **Mise à l’échelle des ressources de calcul.** Pour améliorer les performances des requêtes, vous pouvez utiliser des [groupes de scale-out PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md)SQL Server. Cela autorise un transfert de données en parallèle entre les instances SQL Server et les nœuds Hadoop, et cela ajoute des ressources de calcul qui permettent d’exploiter les données externes.  
  
## <a name="polybase-guide-topics"></a>Rubriques du guide de PolyBase  
 Ce guide vous propose des rubriques destinées à vous aider à utiliser PolyBase avec efficacité.  
  
|||  
|-|-|  
|**Rubrique**|**Description**|  
|[Prise en main de PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)|Étapes de base pour installer et configurer PolyBase. Cette rubrique vous montre comment créer des objets externes qui pointent vers des données stockées dans Hadoop ou Stockage Blob Azure, et propose des exemples de requêtes.|  
|[Récapitulatif des fonctionnalités avec version de PolyBase](../../relational-databases/polybase/polybase-versioned-feature-summary.md)|Décrit les fonctionnalités de PolyBase qui sont prises en charge par SQL Server, Base de données SQL et SQL Data Warehouse.|  
|[groupes de scale-out PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md)|Faites monter en puissance le parallélisme entre SQL Server et Hadoop au moyen de groupes de scale-out SQL Server.|  
|[Installation de PolyBase](../../relational-databases/polybase/polybase-installation.md)|Informations de référence et étapes à suivre pour installer PolyBase avec l’Assistant Installation ou un outil en ligne de commande.|  
|[Configuration de PolyBase](../../relational-databases/polybase/polybase-configuration.md)|Configurez les paramètres SQL Server pour PolyBase.  Par exemple, configurez la délégation des calculs et la sécurité kerberos.|  
|[Objets T-SQL PolyBase](../../relational-databases/polybase/polybase-t-sql-objects.md)|Créez les objets T-SQL dont se servira PolyBase pour définir et accéder aux données externes.|  
|[Requêtes PolyBase](../../relational-databases/polybase/polybase-queries.md)|Utilisez des instructions T-SQL pour interroger, importer ou exporter des données externes.|  
|[Résolution des problèmes de Polybase](../../relational-databases/polybase/polybase-troubleshooting.md)|Techniques de gestion des requêtes PolyBase. Utilisez des vues de gestion dynamique (DMV) pour surveiller les requêtes PolyBase, et apprenez à lire un plan de requête PolyBase pour identifier les goulots d’étranglement.|  
  
  

