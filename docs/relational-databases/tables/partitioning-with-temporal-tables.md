---
title: "Partitionnement des tables temporelles | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 04/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 313714b8-4ad1-4c14-93a3-7f628a334a51
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0134010294aec01d47271a7e00e6a13e4a3ad208
ms.lasthandoff: 04/11/2017

---
# <a name="partitioning-with-temporal-tables"></a>Partitionnement des tables temporelles
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Vous pouvez utiliser le partitionnement, de manière indépendante, sur la table actuelle et la table de l’historique. Toutefois, le partitionnement ne peut pas être utilisé pour modifier le contenu des données sans contrôle de version du système.  
  
> [!NOTE]  
>  Le partitionnement est une fonctionnalité Enterprise Edition.  
  
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
 [Prise en main des tables temporelles de contrôle de version du système](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [Vérifications de cohérence système des tables temporelles](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Considérations et limitations liées aux tables temporelles](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [Sécurité de la table temporelle](../../relational-databases/tables/temporal-table-security.md)   
 [Gérer la rétention des données d’historique dans les tables temporelles avec version gérée par le système](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Tables temporelles à système par version avec tables optimisées en mémoire](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Vues et fonctions de métadonnées de table temporelle](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  

