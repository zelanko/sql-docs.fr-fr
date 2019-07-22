---
title: Prise en main des tables temporelles avec contrôle de version par le système | Microsoft Docs
ms.custom: ''
ms.date: 03/28/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: d431f216-82cf-4d97-825e-bb35d3d53a45
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0bf81a84acbec65334ec02d7bd358215f6a0b0ea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68016353"
---
# <a name="getting-started-with-system-versioned-temporal-tables"></a>Prise en main des tables temporelles de contrôle de version du système
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  En fonction de votre scénario, vous pouvez créer des tables temporelles de contrôle de version du système ou modifier des tables existantes en ajoutant des attributs temporels au schéma de table existant.   
Lorsque les données d’une table temporelle sont modifiées, le système crée un historique de version en toute transparence pour les applications et les utilisateurs finaux. Par conséquent, l’utilisation de tables temporelles de contrôle de version du système ne nécessite pas de changer la manière dont la table est modifiée ou dont le dernier état (réel) des données est interrogé.   
Outre des DML et des interrogations à un rythme régulier, la fonctionnalité temporelle offre un moyen simple et pratique d’obtenir des informations relatives à l’historique des données par le biais de la syntaxe étendue Transact-SQL.   
Une table d’historique est affectée à chaque table avec contrôle de version du système, mais elle est complètement transparente pour les utilisateurs, sauf s’ils souhaitent optimiser les performances de la charge de travail ou l’encombrement de stockage en créant des index supplémentaires ou en choisissant d’autres options de stockage.    
Le schéma suivant illustre le flux de travail type relatif aux tables temporelles avec version gérée par le système :   
![Bien démarrer avec la table temporelle](../../relational-databases/tables/media/getting-started-with-temporal.png "Bien démarrer avec la table temporelle")  
  
 Cette rubrique est constituée des 5 sous-rubriques suivantes :  
  
-   [Création d’une table temporelle avec contrôle de version du système](../../relational-databases/tables/creating-a-system-versioned-temporal-table.md)  
  
-   [Modification des données dans une table temporelle avec système par version](../../relational-databases/tables/modifying-data-in-a-system-versioned-temporal-table.md)  
  
-   [Interrogation des données dans une table temporelle avec système par version](../../relational-databases/tables/querying-data-in-a-system-versioned-temporal-table.md)  
  
-   [Modification du schéma d’une table temporelle à version contrôlée par le système](../../relational-databases/tables/changing-the-schema-of-a-system-versioned-temporal-table.md)  
  
-   [Arrêt du contrôle de version du système sur une table temporelle avec contrôle de version par le système](../../relational-databases/tables/stopping-system-versioning-on-a-system-versioned-temporal-table.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tables temporelles](../../relational-databases/tables/temporal-tables.md)   
 [Vérifications de cohérence système des tables temporelles](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Partitionnement des tables temporelles](../../relational-databases/tables/partitioning-with-temporal-tables.md)   
 [Considérations et limitations liées aux tables temporelles](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [Sécurité de la table temporelle](../../relational-databases/tables/temporal-table-security.md)   
 [Gérer la rétention des données d’historique dans les tables temporelles avec version gérée par le système](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Tables temporelles avec version gérée par le système avec tables à mémoire optimisée](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Vues et fonctions de métadonnées de table temporelle](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  
