---
title: Connexion à Azure SQL DB (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9e77e4b0-40c0-455c-8431-ca5d43849aa7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 10be1dc3652c944b9de08a01b0f4cdff5ae5849a
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176238"
---
# <a name="connecting-to-azure-sql-db-sybasetosql"></a>Connexion à Azure SQL DB (SybaseToSQL)
Pour migrer des bases de données Sybase vers Azure SQL DB, vous devez vous connecter à l’instance cible d’Azure SQL DB. Lorsque vous vous connectez, SSMA obtient les métadonnées relatives à toutes les bases de données de l’instance d’Azure SQL DB et affiche les métadonnées de la base de données dans l’Explorateur de métadonnées Azure SQL DB. SSMA stocke les informations de l’instance de la base de données SQL Azure à laquelle vous êtes connecté, mais ne stocke pas les mots de passe.  
  
Votre connexion à Azure SQL DB reste active jusqu’à ce que vous fermiez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter à Azure SQL DB si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu’à ce que vous chargeant des objets de base de données dans Azure SQL DB et migriez les données.  
  
Les métadonnées relatives à l’instance d’Azure SQL DB ne sont pas synchronisées automatiquement. Au lieu de cela, pour mettre à jour les métadonnées dans l’Explorateur de métadonnées Azure SQL DB, vous devez mettre à jour manuellement les métadonnées Azure SQL DB. Pour plus d’informations, consultez la section «synchronisation des métadonnées Azure SQL DB» plus loin dans cette rubrique.  
  
## <a name="required-azure-sql-db-permissions"></a>Autorisations Azure SQL DB requises  
Le compte utilisé pour se connecter à Azure SQL DB nécessite des autorisations différentes en fonction des actions effectuées par le compte:  
  
1.  Pour convertir des objets Sybase [!INCLUDE[tsql](../../includes/tsql-md.md)] en syntaxe, pour mettre à jour des métadonnées à partir d’Azure SQL dB ou pour enregistrer une syntaxe convertie dans des scripts, le compte doit avoir l’autorisation de se connecter à l’instance d’Azure SQL db.  
  
2.  Pour charger des objets de base de données dans Azure SQL DB, l’exigence d’autorisation minimale est l’appartenance au rôle de base de données **db_owner** dans la base de données cible.  
  
## <a name="establishing-an-azure-sql-db-connection"></a>Établissement d’une connexion Azure SQL DB  
Avant de convertir des objets de base de données Sybase en syntaxe Azure SQL DB, vous devez établir une connexion à l’instance de base de données SQL Azure dans laquelle vous souhaitez migrer la ou les bases de données Sybase.  
  
Lorsque vous définissez les propriétés de connexion, vous spécifiez également la base de données dans laquelle les objets et les données seront migrés. Vous pouvez personnaliser ce mappage au niveau du schéma Sybase après vous être connecté à Azure SQL DB. Pour plus d’informations, consultez [mappage de schémas Sybase ASE à des schémas &#40;de&#41; SQL Server SybaseToSQL](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)  
  
> [!WARNING]  
> Avant d’essayer de vous connecter à Azure SQL DB, assurez-vous que l’instance d’Azure SQL DB est en cours d’exécution et peut accepter des connexions.  
  
**Pour se connecter à Azure SQL DB**  
  
1.  Dans le menu **fichier** , sélectionnez **se connecter à Azure SQL DB**(cette option est activée après la création d’un projet).  
  
    Si vous vous êtes déjà connecté à Azure SQL DB, le nom de la commande sera **reconnecté à Azure SQL DB**  
  
2.  Dans la boîte de dialogue connexion, entrez ou sélectionnez le nom du serveur Azure SQL DB.  
  
3.  Entrez, sélectionnez ou **recherchez** le nom de la base de données.  
  
4.  Entrez ou sélectionnez **nom d’utilisateur**.  
  
5.  Entrez le **mot de passe**.  
  
6.  SSMA recommande la connexion chiffrée à Azure SQL DB.  
  
7.  Cliquer sur **Se connecter**.  
  
> [!IMPORTANT]  
> SSMA pour Sybase ne prend pas en charge la connexion à la base de données **Master** dans Azure SQL db.  
  
## <a name="synchronizing-azure-sql-db-metadata"></a>Synchronisation des métadonnées Azure SQL DB  
Les métadonnées relatives aux bases de données Azure SQL DB ne sont pas automatiquement mises à jour. Les métadonnées dans l’Explorateur de métadonnées Azure SQL DB sont une capture instantanée des métadonnées lors de la première connexion à Azure SQL DB, ou la dernière fois que vous avez mis à jour manuellement les métadonnées. Vous pouvez mettre à jour manuellement les métadonnées de toutes les bases de données ou d’une base de données ou d’un objet de base de données unique.  
  
**Pour synchroniser les métadonnées**  
  
1.  Assurez-vous que vous êtes connecté à Azure SQL DB.  
  
2.  Dans l’Explorateur de métadonnées de base de données SQL Azure, activez la case à cocher en regard de la base de données ou du schéma de base de données que vous souhaitez mettre à jour.  
  
    Par exemple, pour mettre à jour les métadonnées de toutes les bases de données, activez la case à cocher en regard de bases de données.  
  
3.  Cliquez avec le bouton droit sur bases de données, ou sur la base de données individuelle ou le schéma de base de données, puis sélectionnez **synchroniser avec la base de**données.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante de la migration dépend des besoins de votre projet:  
  
-   Pour personnaliser le mappage entre les schémas Sybase et les bases de données et schémas Azure SQL DB, consultez [mappage de schémas Sybase ASE à des schémas &#40;de&#41; SQL Server SybaseToSQL](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)  
  
-   Pour personnaliser les options de configuration des projets, consultez [définition des &#40;options&#41; de projet SybaseToSQL](../../ssma/sybase/setting-project-options-sybasetosql.md)  
  
-   Pour personnaliser le mappage des types de données sources et cibles, consultez [mappage de Sybase ASE et des &#40;types&#41; de données de SQL Server SybaseToSQL](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md)  
  
-   Si vous n’avez pas besoin d’effectuer ces tâches, vous pouvez convertir les définitions d’objet de base de données Sybase en définitions d’objet de base de données SQL Azure. Pour plus d’informations, consultez [conversion d' &#40;objets de base&#41; de données Sybase ASE SybaseToSQL](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Migration de bases de données Sybase ASE vers SQL Server-Azure &#40;SQL DB SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
