---
title: Connexion à Azure SQL Database (AccessToSQL) | Microsoft Docs
description: Découvrez comment vous connecter à une instance cible de Azure SQL Database pour migrer des bases de données Access. SSMA obtient des métadonnées sur les bases de données dans Azure SQL Database.
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- instance of SQL Azure
- metadata, refreshing
- refreshing metadata
- SQL Azure
- SQL Azure, connecting
- SQL Azure, connecting to
- SQL Azure, reconnecting
- SQL Azure, synchronizing metadata
ms.assetid: 1ba0d113-dc05-4431-8689-e14a8821bafd
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 3bb372b329ce516cae2ab26ece02721d7934b228
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87938909"
---
# <a name="connecting-to-azure-sql-database-accesstosql"></a>Connexion à Azure SQL Database (AccessToSQL)
Pour migrer des bases de données Access vers SQL Azure, vous devez vous connecter à l’instance cible de SQL Azure. Quand vous vous connectez, SSMA obtient les métadonnées relatives à toutes les bases de données dans l’instance de SQL Azure et affiche les métadonnées de la base de données dans l’Explorateur de métadonnées SQL Azure. SSMA stocke des informations sur l’instance de SQL Azure à laquelle vous êtes connecté, mais ne stocke pas les mots de passe.  
  
Votre connexion à SQL Azure reste active jusqu’à ce que vous fermiez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter à SQL Azure si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu’à ce que vous chargeant des objets de base de données dans SQL Azure et migriez les données.  
  
Les métadonnées relatives à l’instance de SQL Azure ne sont pas synchronisées automatiquement. Au lieu de cela, pour mettre à jour les métadonnées dans SQL Azure Explorateur de métadonnées, vous devez mettre à jour manuellement les métadonnées de SQL Azure. Pour plus d’informations, consultez la section « synchronisation des métadonnées de SQL Azure » plus loin dans cette rubrique.  
  
## <a name="required-sql-azure-permissions"></a>Autorisations de SQL Azure requises  
Le compte utilisé pour se connecter à SQL Azure nécessite des autorisations différentes en fonction des actions effectuées par le compte :  
  
-   Pour convertir des objets Access en [!INCLUDE[tsql](../../includes/tsql-md.md)] syntaxe, pour mettre à jour des métadonnées à partir de SQL Azure, ou pour enregistrer la syntaxe convertie dans des scripts, le compte doit avoir l’autorisation de se connecter à l’instance de SQL Azure.  
  
-   Pour charger des objets de base de données dans SQL Azure, l’exigence d’autorisation minimale est l’appartenance au rôle de base de données **db_owner** dans la base de données cible.  
  
## <a name="establishing-a-sql-azure-connection"></a>Établissement d’une connexion SQL Azure  
Avant de convertir des objets de base de données Access en SQL Azure syntaxe, vous devez établir une connexion à l’instance de SQL Azure dans laquelle vous souhaitez migrer la ou les bases de données Access.  
  
Lorsque vous définissez les propriétés de connexion, vous spécifiez également la base de données dans laquelle les objets et les données seront migrés. Vous pouvez personnaliser ce mappage au niveau du schéma d’accès après vous être connecté à SQL Azure. Pour plus d’informations, consultez [mappage de bases de données Access à des schémas de SQL Server](mapping-source-and-target-databases-accesstosql.md)  
  
> [!IMPORTANT]  
> Avant d’essayer de vous connecter à SQL Azure, assurez-vous que l’instance de SQL Azure est en cours d’exécution et peut accepter des connexions.  
  
**Pour se connecter à SQL Azure**  
  
1.  Dans le menu **fichier** , sélectionnez **se connecter à SQL Azure** (cette option est activée après la création d’un projet).  
  
    Si vous vous êtes connecté précédemment à SQL Azure, le nom de la commande sera **reconnecté à SQL Azure**.  
  
2.  Dans la boîte de dialogue connexion, entrez ou sélectionnez le nom du serveur de SQL Azure.  
  
3.  Entrez, sélectionnez ou **Parcourez** le nom de la base de données.  
  
4.  Entrez ou sélectionnez **nom d’utilisateur**.  
  
5.  Entrez le **mot de passe**.  
  
6.  SSMA recommande la connexion chiffrée à SQL Azure.  
  
7.  Cliquez sur **Connecter**.  
  
> [!IMPORTANT]  
> SSMA pour Access ne prend pas en charge la connexion à la base de données **Master** dans SQL Azure.  
  
S’il n’existe aucune base de données dans le compte SQL Azure, vous pouvez créer la première base de données à l’aide de l’option **créer une base de données Azure** qui apparaît sur le bouton **Parcourir** .  
  
## <a name="synchronizing-sql-azure-metadata"></a>Synchronisation des métadonnées de SQL Azure  
Les métadonnées relatives aux bases de données dans Azure SQL Database ne sont pas automatiquement mises à jour. Les métadonnées dans SQL Azure Explorateur de métadonnées sont un instantané des métadonnées lorsque vous vous êtes connecté pour la première fois à SQL Azure, ou la dernière fois que vous avez mis à jour manuellement les métadonnées. Vous pouvez mettre à jour manuellement les métadonnées de toutes les bases de données ou d’une base de données ou d’un objet de base de données unique.  
  
**Pour synchroniser les métadonnées**  
  
1.  Assurez-vous que vous êtes connecté à SQL Azure.  
  
2.  Dans SQL Azure Explorateur de métadonnées, activez la case à cocher en regard de la base de données ou du schéma de base de données que vous souhaitez mettre à jour.  
  
    Par exemple, pour mettre à jour les métadonnées de toutes les bases de données, activez la case à cocher en regard de bases de données.  
  
3.  Cliquez avec le bouton droit sur bases de données, ou sur la base de données individuelle ou le schéma de base de données, puis sélectionnez **synchroniser avec la base de**données.  
  
## <a name="refreshing-sql-azure-metadata"></a>Actualisation des métadonnées de SQL Azure  
Si SQL Azure schémas changent après la connexion, vous pouvez actualiser les métadonnées à partir du serveur.  
  
**Pour actualiser les métadonnées SQL Azure**  
  
-   Dans SQL Azure Explorateur de métadonnées, cliquez avec le bouton droit sur **bases de données**, puis sélectionnez **Actualiser à partir de la base de données**.  
  
## <a name="reconnecting-to-sql-azure"></a>Reconnexion à SQL Azure  
Votre connexion à SQL Azure reste active jusqu’à ce que vous fermiez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter à SQL Azure si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu’à ce que vous chargeant des objets de base de données dans SQL Azure et migriez les données.  
  
La procédure de reconnexion à SQL Azure est identique à celle de la procédure d’établissement d’une connexion.  
  
## <a name="next-steps"></a>Étapes suivantes  
L’étape suivante de la migration dépend des besoins de votre projet :  
  
-   Pour personnaliser le mappage entre les schémas d’accès et les Azure SQL Database, consultez [mappage de bases de données Access à des schémas de SQL Server](mapping-source-and-target-databases-accesstosql.md).  
  
-   Pour personnaliser les options de configuration des projets, consultez [définition des options du projet](setting-conversion-and-migration-options-accesstosql.md).  
  
-   Pour personnaliser le mappage des types de données sources et cibles, consultez [mappage des types de données source et cible](mapping-source-and-target-data-types-accesstosql.md).  
  
-   Si vous n’avez pas besoin d’effectuer ces tâches, vous pouvez convertir les définitions d’objet de base de données Access en SQL Azure définitions d’objets. Pour plus d’informations, consultez [conversion de bases de données Access](converting-access-database-objects-accesstosql.md) .  
  
## <a name="see-also"></a>Voir aussi  
[Migration de bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
