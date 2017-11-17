---
title: "Partitionnement des tables temporelles | Microsoft Docs"
ms.custom: 
ms.date: 04/26/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 313714b8-4ad1-4c14-93a3-7f628a334a51
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: e76675099ab290d29231d434eb74e92b613185b7
ms.openlocfilehash: cb93e468300aea6a666ad04e9ce6ad20e1b85fc2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/29/2017

---
# <a name="partitioning-with-temporal-tables"></a>Partitionnement des tables temporelles
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Vous pouvez utiliser le partitionnement, de manière indépendante, sur la table actuelle et la table de l’historique. Toutefois, le partitionnement ne peut pas être utilisé pour modifier le contenu des données sans contrôle de version du système.  
  
> [!NOTE]  
>  Le partitionnement est une fonctionnalité de l’édition Enterprise dans SQL Server 2016 avant le Service Pack 1 et les versions antérieures. Le partitionnement est pris en charge dans toutes les éditions de SQL Server 2016 Service Pack 1 et des versions ultérieures.
  
-   **Table actuelle :**  
  
    -   **SWITCH IN** sur la table actuelle peut être utilisé pour faciliter le chargement et l’interrogation des données quand **SYSTEM_VERSIONING** a la valeur **ON**  
  
    -   **SWITCH OUT** n’est pas autorisé quand **SYSTEM_VERSIONING** a la valeur **ON**  
  
-   **Table de l’historique :**  
  
    -   **SWITCH OUT** à partir de la table d’historique peut être utilisé quand **SYSTEM_VERSIONING** a la valeur **ON** pour vider les parties de données d’historique qui ne sont plus pertinentes.  
  
    -   **SWITCH IN** n’est pas autorisé quand **SYSTEM_VERSIONING** a la valeur **ON** , car il peut invalider la cohérence des données temporelles.  
  
## <a name="did-this-article-help-you-were-listening"></a>Cet article vous a-t-il été utile ? Nous sommes à votre écoute  
 Quels renseignements souhaitez-vous obtenir ? Avez-vous trouvé ce que vous cherchiez ? Nous tenons compte de vos commentaires pour améliorer le contenu de nos articles. Veuillez envoyer vos commentaires à l’adresse suivante : [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Partitioning%20with%20Temporal%20Tables%20page)  
  
## <a name="see-also"></a>Voir aussi  
 [Tables temporelles](../../relational-databases/tables/temporal-tables.md)   
 [Prise en main des tables temporelles avec versions gérées par le système](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [Vérifications de cohérence système des tables temporelles](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Considérations et limitations liées aux tables temporelles](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [Sécurité de la table temporelle](../../relational-databases/tables/temporal-table-security.md)   
 [Gérer la rétention des données d’historique dans les tables temporelles avec version gérée par le système](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Tables temporelles avec version gérée par le système avec tables à mémoire optimisée](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Vues et fonctions de métadonnées de table temporelle](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  

