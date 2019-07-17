---
title: Connexion à Azure SQL DB (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to SQL Azure, SQL Azure permissions
- Connecting to SQL Azure, synchronization
ms.assetid: d0b6f16a-1880-459d-a0c7-28b7ef15c56a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7fb6740681c08cb915755b3362352f139e078c4c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68103195"
---
# <a name="connecting-to-azure-sql-db-mysqltosql"></a>Connexion à Azure SQL DB (MySQLToSQL)
Pour migrer des bases de données MySQL vers SQL Azure, vous devez vous connecter à l’instance cible de SQL Azure. Lorsque vous vous connectez, SSMA Obtient les métadonnées relatives à toutes les bases de données dans l’instance de SQL Azure et affiche les métadonnées de la base de données dans l’Explorateur de métadonnées SQL Azure. SSMA stocke les informations de l’instance de SQL Azure que vous êtes connecté à, mais ne stockez pas les mots de passe.  
  
Votre connexion à SQL Azure reste active jusqu'à ce que vous fermiez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter à SQL Azure si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu'à ce que vous chargez des objets de base de données dans SQL Azure et migrez des données.  
  
Métadonnées relatives à l’instance de SQL Azure ne sont pas synchronisée automatiquement. Au lieu de cela, pour mettre à jour les métadonnées dans l’Explorateur de métadonnées SQL Azure, vous devez manuellement mettre à jour les métadonnées de SQL Azure. Pour plus d’informations, consultez la section « Synchronisation des métadonnées de SQL Azure » plus loin dans cette rubrique.  
  
## <a name="required-sql-azure-permissions"></a>Requis de SQL Azure des autorisations  
Le compte qui est utilisé pour se connecter à SQL Azure nécessite des autorisations différentes selon les actions réalisées par le compte :  
  
-   Pour convertir des objets MySQL pour [!INCLUDE[tsql](../../includes/tsql-md.md)] syntaxe, pour mettre à jour des métadonnées à partir de SQL Azure, ou pour enregistrer une syntaxe convertie pour les scripts, le compte doit avoir l’autorisation de se connecter à l’instance de SQL Azure.  
  
-   Pour charger des objets de base de données dans SQL Azure, l’exigence d’autorisation minimal est l’appartenance à la **db_owner** rôle de base de données dans la base de données cible.  
  
## <a name="establishing-a-sql-azure-connection"></a>L’établissement d’un SQL Azure connexion  
Avant de convertir des objets de base de données MySQL à la syntaxe de SQL Azure, vous devez établir une connexion à l’instance de SQL Azure dans lequel vous souhaitez migrer la base de données MySQL ou les bases de données.  
  
Lorsque vous définissez les propriétés de connexion, vous spécifiez également la base de données où les objets et les données seront migrées. Vous pouvez personnaliser ce mappage au niveau du schéma de MySQL après que vous être connecté à SQL Azure. Pour plus d’informations, consultez [mappage de bases de données MySQL à des schémas de SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
> [!IMPORTANT]  
> Avant d’essayer de se connecter à SQL Azure, assurez-vous que l’instance de SQL Azure est en cours d’exécution et peut accepter les connexions.  
  
**Pour vous connecter à SQL Azure**  
  
1.  Sur le **fichier** menu, sélectionnez **se connecter à SQL Azure** (cette option est activée après la création d’un projet).  
  
    Si vous avez précédemment connecté à SQL Azure, le nom de la commande sera **reconnexion à SQL Azure**.  
  
2.  Dans la boîte de dialogue de connexion, entrez ou sélectionnez le nom du serveur de SQL Azure.  
  
3.  Entrez, sélectionnez ou **Parcourir** le nom de la base de données.  
  
4.  Entrez ou sélectionnez **nom d’utilisateur**.  
  
5.  Entrez le **mot de passe**.  
  
6.  SSMA recommande une connexion chiffrée pour SQL Azure.  
  
7.  Cliquer sur **Se connecter**.  
  
> [!IMPORTANT]  
> SSMA pour MySQL ne prend pas en charge la connexion à **master** base de données dans SQL Azure.  
  
## <a name="synchronizing-sql-azure-metadata"></a>Synchronisation de SQL Azure des métadonnées  
Les métadonnées sur les bases de données SQL Azure ne sont pas automatiquement mis à jour. Les métadonnées dans l’Explorateur de métadonnées SQL Azure sont un instantané des métadonnées lorsque vous tout d’abord connecté à SQL Azure, ou la dernière fois que vous avez manuellement mis à jour les métadonnées. Vous pouvez mettre à jour manuellement les métadonnées pour toutes les bases de données, ou pour n’importe quel base de données unique ou un objet de base de données.  
  
**Pour synchroniser les métadonnées**  
  
1.  Assurez-vous que vous êtes connecté à SQL Azure.  
  
2.  Dans l’Explorateur de métadonnées SQL Azure, sélectionnez la case à cocher en regard de la base de données ou le schéma de base de données que vous souhaitez mettre à jour.  
  
    Par exemple, pour mettre à jour les métadonnées pour toutes les bases de données, sélectionnez la case en regard de bases de données.  
  
3.  Avec le bouton droit de bases de données, ou la base de données individuelle ou le schéma de base de données, puis sélectionnez **synchroniser avec la base de données**.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante de la migration dépend des besoins de votre projet :  
  
-   Pour personnaliser le mappage entre les schémas de MySQL et des bases de données SQL Azure et des schémas, consultez [mappage de bases de données MySQL à des schémas de SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
-   Pour personnaliser les options de configuration pour les projets, consultez [définition des Options de projet &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)  
  
-   Pour personnaliser le mappage des types de données source et cible, consultez [MySQL de mappage et les Types de données SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   Si vous n’avez pas à effectuer ces tâches, vous pouvez convertir les définitions d’objets de base de données MySQL dans les définitions d’objets SQL Azure. Pour plus d’informations, consultez [conversion de bases de données MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Bases de données de migration de MySQL vers SQL Server - Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
