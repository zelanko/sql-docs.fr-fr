---
description: Connexion à Azure SQL Database (SybaseToSQL)
title: Connexion à Azure SQL Database (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9e77e4b0-40c0-455c-8431-ca5d43849aa7
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: eacdca6cf260557171f5adf63f8590842de77fcb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88372345"
---
# <a name="connecting-to-azure-sql-database-sybasetosql"></a>Connexion à Azure SQL Database (SybaseToSQL)
Pour migrer des bases de données Sybase vers Azure SQL Database, vous devez vous connecter à l’instance cible de Azure SQL Database. Quand vous vous connectez, SSMA obtient les métadonnées relatives à toutes les bases de données dans l’instance de Azure SQL Database et affiche les métadonnées de la base de données dans l’Explorateur de métadonnées Azure SQL Database. SSMA stocke les informations de l’instance de Azure SQL Database à laquelle vous êtes connecté, mais ne stocke pas les mots de passe.  
  
Votre connexion à Azure SQL Database reste active jusqu’à ce que vous fermiez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter à Azure SQL Database si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu’à ce que vous chargeant des objets de base de données dans Azure SQL Database et migriez les données.  
  
Les métadonnées relatives à l’instance de Azure SQL Database ne sont pas synchronisées automatiquement. Au lieu de cela, pour mettre à jour les métadonnées dans Azure SQL Database Explorateur de métadonnées, vous devez mettre à jour manuellement les métadonnées de Azure SQL Database. Pour plus d’informations, consultez la section « synchronisation des métadonnées de Azure SQL Database » plus loin dans cette rubrique.  
  
## <a name="required-azure-sql-database-permissions"></a>Autorisations de Azure SQL Database requises  
Le compte utilisé pour se connecter à Azure SQL Database nécessite des autorisations différentes en fonction des actions effectuées par le compte :  
  
1.  Pour convertir des objets Sybase en [!INCLUDE[tsql](../../includes/tsql-md.md)] syntaxe, pour mettre à jour des métadonnées à partir de Azure SQL Database, ou pour enregistrer la syntaxe convertie dans des scripts, le compte doit avoir l’autorisation de se connecter à l’instance de Azure SQL Database.  
  
2.  Pour charger des objets de base de données dans Azure SQL Database, l’exigence d’autorisation minimale est l’appartenance au rôle de base de données  **db_owner** dans la base de données cible.  
  
## <a name="establishing-an-azure-sql-database-connection"></a>Établissement d’une connexion Azure SQL Database  
Avant de convertir des objets de base de données Sybase en Azure SQL Database syntaxe, vous devez établir une connexion à l’instance de Azure SQL Database dans laquelle vous souhaitez migrer la ou les bases de données Sybase.  
  
Lorsque vous définissez les propriétés de connexion, vous spécifiez également la base de données dans laquelle les objets et les données seront migrés. Vous pouvez personnaliser ce mappage au niveau du schéma Sybase après vous être connecté à Azure SQL Database. Pour plus d’informations, consultez [mappage de schémas Sybase ASE à des schémas de SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)  
  
> [!WARNING]  
> Avant d’essayer de vous connecter à Azure SQL Database, assurez-vous que l’instance de Azure SQL Database est en cours d’exécution et peut accepter des connexions.  
  
**Pour se connecter à Azure SQL Database**  
  
1.  Dans le menu **fichier** , sélectionnez **se connecter à Azure SQL Database**(cette option est activée après la création d’un projet).  
  
    Si vous vous êtes déjà connecté à Azure SQL Database, le nom de la commande sera **reconnecté à Azure SQL Database**  
  
2.  Dans la boîte de dialogue connexion, entrez ou sélectionnez le nom du serveur de Azure SQL Database.  
  
3.  Entrez, sélectionnez ou **recherchez** le nom de la base de données.  
  
4.  Entrez ou sélectionnez **nom d’utilisateur**.  
  
5.  Entrez le **mot de passe**.  
  
6.  SSMA recommande la connexion chiffrée à Azure SQL Database.  
  
7.  Cliquez sur **Connecter**.  
  
> [!IMPORTANT]  
> SSMA pour Sybase ne prend pas en charge la connexion à la base de données **Master** dans Azure SQL Database.  
  
## <a name="synchronizing-azure-sql-database-metadata"></a>Synchronisation des métadonnées de Azure SQL Database  
Les métadonnées relatives aux bases de données Azure SQL Database ne sont pas automatiquement mises à jour. Les métadonnées dans Azure SQL Database Explorateur de métadonnées sont un instantané des métadonnées lorsque vous vous êtes connecté pour la première fois à Azure SQL Database, ou la dernière fois que vous avez mis à jour manuellement les métadonnées. Vous pouvez mettre à jour manuellement les métadonnées de toutes les bases de données ou d’une base de données ou d’un objet de base de données unique.  
  
**Pour synchroniser les métadonnées**  
  
1.  Assurez-vous que vous êtes connecté à Azure SQL Database.  
  
2.  Dans Azure SQL Database Explorateur de métadonnées, activez la case à cocher en regard de la base de données ou du schéma de base de données que vous souhaitez mettre à jour.  
  
    Par exemple, pour mettre à jour les métadonnées de toutes les bases de données, activez la case à cocher en regard de bases de données.  
  
3.  Cliquez avec le bouton droit sur bases de données, ou sur la base de données individuelle ou le schéma de base de données, puis sélectionnez **synchroniser avec la base de**données.  
  
## <a name="next-step"></a>étape suivante  
L’étape suivante de la migration dépend des besoins de votre projet :  
  
-   Pour personnaliser le mappage entre les schémas Sybase et Azure SQL Database les bases de données et les schémas, consultez [mappage de schémas Sybase ASE à des schémas de SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)  
  
-   Pour personnaliser les options de configuration des projets, consultez [définition des options de projet &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md)  
  
-   Pour personnaliser le mappage des types de données sources et cibles, consultez [mappage des types de données Sybase ASE et SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md)  
  
-   Si vous n’avez pas besoin d’effectuer ces tâches, vous pouvez convertir les définitions d’objet de base de données Sybase en Azure SQL Database définitions d’objets. Pour plus d’informations, consultez [conversion d’objets de base de données Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Migration de bases de données Sybase ASE vers SQL Server Azure SQL Database &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
