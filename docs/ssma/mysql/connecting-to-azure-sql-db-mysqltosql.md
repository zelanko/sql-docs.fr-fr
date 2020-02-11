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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103195"
---
# <a name="connecting-to-azure-sql-db-mysqltosql"></a>Connexion à Azure SQL DB (MySQLToSQL)
Pour migrer des bases de données MySQL vers SQL Azure, vous devez vous connecter à l’instance cible de SQL Azure. Quand vous vous connectez, SSMA obtient les métadonnées relatives à toutes les bases de données dans l’instance de SQL Azure et affiche les métadonnées de la base de données dans l’Explorateur de métadonnées SQL Azure. SSMA stocke les informations de l’instance de SQL Azure à laquelle vous êtes connecté, mais ne stocke pas les mots de passe.  
  
Votre connexion à SQL Azure reste active jusqu’à ce que vous fermiez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter à SQL Azure si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu’à ce que vous chargeant des objets de base de données dans SQL Azure et migriez les données.  
  
Les métadonnées relatives à l’instance de SQL Azure ne sont pas synchronisées automatiquement. Au lieu de cela, pour mettre à jour les métadonnées dans SQL Azure Explorateur de métadonnées, vous devez mettre à jour manuellement les métadonnées de SQL Azure. Pour plus d’informations, consultez la section « synchronisation des métadonnées de SQL Azure » plus loin dans cette rubrique.  
  
## <a name="required-sql-azure-permissions"></a>Autorisations de SQL Azure requises  
Le compte utilisé pour se connecter à SQL Azure nécessite des autorisations différentes en fonction des actions effectuées par le compte :  
  
-   Pour convertir des objets MySQL [!INCLUDE[tsql](../../includes/tsql-md.md)] en syntaxe, pour mettre à jour des métadonnées à partir de SQL Azure, ou pour enregistrer la syntaxe convertie dans des scripts, le compte doit avoir l’autorisation de se connecter à l’instance de SQL Azure.  
  
-   Pour charger des objets de base de données dans SQL Azure, l’exigence d’autorisation minimale est l’appartenance au rôle de base de données **db_owner** dans la base de données cible.  
  
## <a name="establishing-a-sql-azure-connection"></a>Établissement d’une connexion SQL Azure  
Avant de convertir des objets de base de données MySQL en SQL Azure syntaxe, vous devez établir une connexion à l’instance de SQL Azure dans laquelle vous souhaitez migrer la ou les bases de données MySQL.  
  
Lorsque vous définissez les propriétés de connexion, vous spécifiez également la base de données dans laquelle les objets et les données seront migrés. Vous pouvez personnaliser ce mappage au niveau du schéma MySQL après vous être connecté à SQL Azure. Pour plus d’informations, consultez [mappage de bases de données MySQL à des schémas de SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
> [!IMPORTANT]  
> Avant d’essayer de vous connecter à SQL Azure, assurez-vous que l’instance de SQL Azure est en cours d’exécution et peut accepter des connexions.  
  
**Pour se connecter à SQL Azure**  
  
1.  Dans le menu **fichier** , sélectionnez **se connecter à SQL Azure** (cette option est activée après la création d’un projet).  
  
    Si vous vous êtes déjà connecté à SQL Azure, le nom de la commande sera **reconnecté à SQL Azure**.  
  
2.  Dans la boîte de dialogue connexion, entrez ou sélectionnez le nom du serveur de SQL Azure.  
  
3.  Entrez, sélectionnez ou **recherchez** le nom de la base de données.  
  
4.  Entrez ou sélectionnez **nom d’utilisateur**.  
  
5.  Entrez le **mot de passe**.  
  
6.  SSMA recommande la connexion chiffrée à SQL Azure.  
  
7.  Cliquez sur **Connecter**.  
  
> [!IMPORTANT]  
> SSMA pour MySQL ne prend pas en charge la connexion à la base de données **Master** dans SQL Azure.  
  
## <a name="synchronizing-sql-azure-metadata"></a>Synchronisation des métadonnées de SQL Azure  
Les métadonnées relatives aux bases de données SQL Azure ne sont pas automatiquement mises à jour. Les métadonnées dans SQL Azure Explorateur de métadonnées sont un instantané des métadonnées lorsque vous vous êtes connecté pour la première fois à SQL Azure, ou la dernière fois que vous avez mis à jour manuellement les métadonnées. Vous pouvez mettre à jour manuellement les métadonnées de toutes les bases de données ou d’une base de données ou d’un objet de base de données unique.  
  
**Pour synchroniser les métadonnées**  
  
1.  Assurez-vous que vous êtes connecté à SQL Azure.  
  
2.  Dans SQL Azure Explorateur de métadonnées, activez la case à cocher en regard de la base de données ou du schéma de base de données que vous souhaitez mettre à jour.  
  
    Par exemple, pour mettre à jour les métadonnées de toutes les bases de données, activez la case à cocher en regard de bases de données.  
  
3.  Cliquez avec le bouton droit sur bases de données, ou sur la base de données individuelle ou le schéma de base de données, puis sélectionnez **synchroniser avec la base de**données.  
  
## <a name="next-step"></a>étape suivante  
L’étape suivante de la migration dépend des besoins de votre projet :  
  
-   Pour personnaliser le mappage entre les schémas MySQL et les bases de données SQL Azure et les schémas, consultez [mappage de bases de données MySQL à des schémas de SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
-   Pour personnaliser les options de configuration des projets, consultez [définition des options de projet &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)  
  
-   Pour personnaliser le mappage des types de données sources et cibles, consultez [mappage des types de données MySQL et SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   Si vous n’avez pas besoin d’effectuer ces tâches, vous pouvez convertir les définitions d’objet de base de données MySQL en SQL Azure définitions d’objets. Pour plus d’informations, consultez [conversion de bases de données MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Migration de bases de données MySQL vers SQL Server-Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
