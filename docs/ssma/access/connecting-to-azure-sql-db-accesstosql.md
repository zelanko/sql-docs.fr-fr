---
title: Connexion à Azure SQL DB (AccessToSQL) | Microsoft Docs
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
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8924ffbbbbbedccdc3bb99469c92667efb822a4c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63138920"
---
# <a name="connecting-to-azure-sql-db-accesstosql"></a>Connexion à Azure SQL DB (AccessToSQL)
Pour migrer des bases de données Access vers SQL Azure, vous devez vous connecter à l’instance cible de SQL Azure. Lorsque vous vous connectez, SSMA Obtient les métadonnées relatives à toutes les bases de données dans l’instance de SQL Azure et affiche les métadonnées de la base de données dans l’Explorateur de métadonnées SQL Azure. SSMA stocke les informations sur l’instance de SQL Azure vous êtes connecté à, mais ne stockez pas les mots de passe.  
  
Votre connexion à SQL Azure reste active jusqu'à ce que vous fermiez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter à SQL Azure si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu'à ce que vous chargez des objets de base de données dans SQL Azure et migrez des données.  
  
Métadonnées relatives à l’instance de SQL Azure ne sont pas synchronisée automatiquement. Au lieu de cela, pour mettre à jour les métadonnées dans l’Explorateur de métadonnées SQL Azure, vous devez manuellement mettre à jour les métadonnées de SQL Azure. Pour plus d’informations, consultez la section « Synchronisation des métadonnées de SQL Azure » plus loin dans cette rubrique.  
  
## <a name="required-sql-azure-permissions"></a>Requis de SQL Azure des autorisations  
Le compte qui est utilisé pour se connecter à SQL Azure nécessite des autorisations différentes selon les actions réalisées par le compte :  
  
-   Pour convertir des objets d’accès à [!INCLUDE[tsql](../../includes/tsql-md.md)] syntaxe, pour mettre à jour des métadonnées à partir de SQL Azure, ou pour enregistrer une syntaxe convertie pour les scripts, le compte doit avoir l’autorisation de se connecter à l’instance de SQL Azure.  
  
-   Pour charger des objets de base de données dans SQL Azure, l’exigence d’autorisation minimal est l’appartenance à la **db_owner** rôle de base de données dans la base de données cible.  
  
## <a name="establishing-a-sql-azure-connection"></a>L’établissement d’un SQL Azure connexion  
Avant de convertir des objets de base de données Access à la syntaxe de SQL Azure, vous devez établir une connexion à l’instance de SQL Azure dans lequel vous souhaitez migrer la base de données Access ou les bases de données.  
  
Lorsque vous définissez les propriétés de connexion, vous spécifiez également la base de données où les objets et les données seront migrées. Vous pouvez personnaliser ce mappage au niveau du schéma d’accès une fois que vous vous connectez à SQL Azure. Pour plus d’informations, consultez [mappage de bases de données Access à des schémas de SQL Server](mapping-source-and-target-databases-accesstosql.md)  
  
> [!IMPORTANT]  
> Avant d’essayer de se connecter à SQL Azure, assurez-vous que l’instance de SQL Azure est en cours d’exécution et peut accepter les connexions.  
  
**Pour vous connecter à SQL Azure**  
  
1.  Sur le **fichier** menu, sélectionnez **se connecter à SQL Azure** (cette option est activée après la création d’un projet).  
  
    Si vous déjà connecté à SQL Azure, le nom de la commande sera **reconnexion à SQL Azure**.  
  
2.  Dans la boîte de dialogue de connexion, entrez ou sélectionnez le nom du serveur de SQL Azure.  
  
3.  Entrez, sélectionnez ou **Parcourir** le nom de la base de données.  
  
4.  Entrez ou sélectionnez **nom d’utilisateur**.  
  
5.  Entrez le **mot de passe**.  
  
6.  SSMA recommande une connexion chiffrée pour SQL Azure.  
  
7.  Cliquer sur **Se connecter**.  
  
> [!IMPORTANT]  
> SSMA pour Access ne prend pas en charge la connexion à **master** base de données dans SQL Azure.  
  
S’il n’y a aucune base de données dans le compte SQL Azure, vous pouvez créer la première base de données à l’aide **créer la base de données Azure** option qui s’affiche dans le, cliquez sur de **Parcourir** bouton.  
  
## <a name="synchronizing-sql-azure-metadata"></a>Synchronisation de SQL Azure des métadonnées  
Les métadonnées sur les bases de données SQL Azure ne sont pas automatiquement mis à jour. Les métadonnées dans l’Explorateur de métadonnées SQL Azure sont un instantané des métadonnées lorsque vous tout d’abord connecté à SQL Azure, ou la dernière fois que vous avez manuellement mis à jour les métadonnées. Vous pouvez mettre à jour manuellement les métadonnées pour toutes les bases de données, ou pour n’importe quel base de données unique ou un objet de base de données.  
  
**Pour synchroniser les métadonnées**  
  
1.  Assurez-vous que vous êtes connecté à SQL Azure.  
  
2.  Dans l’Explorateur de métadonnées SQL Azure, sélectionnez la case à cocher en regard de la base de données ou le schéma de base de données que vous souhaitez mettre à jour.  
  
    Par exemple, pour mettre à jour les métadonnées pour toutes les bases de données, sélectionnez la case en regard de bases de données.  
  
3.  Avec le bouton droit de bases de données, ou la base de données individuelle ou le schéma de base de données, puis sélectionnez **synchroniser avec la base de données**.  
  
## <a name="refreshing-sql-azure-metadata"></a>L’actualisation de SQL Azure des métadonnées  
Si les schémas de SQL Azure modifient après que vous être connecté, vous pouvez actualiser les métadonnées à partir du serveur.  
  
**Pour actualiser les métadonnées de SQL Azure**  
  
-   Dans l’Explorateur de métadonnées SQL Azure, avec le bouton droit cliquez sur **bases de données**, puis sélectionnez **Actualiser à partir de la base de données**.  
  
## <a name="reconnecting-to-sql-azure"></a>Rétablir la connexion à SQL Azure  
Votre connexion à SQL Azure reste active jusqu'à ce que vous fermiez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter à SQL Azure si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu'à ce que vous chargez des objets de base de données dans SQL Azure et migrez des données.  
  
La procédure de reconnexion à SQL Azure est identique à la procédure pour établir une connexion.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante de la migration dépend des besoins de votre projet :  
  
-   Pour personnaliser le mappage entre les schémas d’accès et des bases de données SQL Azure et des schémas, consultez [mappage de bases de données Access schémas SQL Server](mapping-source-and-target-databases-accesstosql.md).  
  
-   Pour personnaliser les options de configuration pour les projets, consultez [définition des Options de projet](setting-conversion-and-migration-options-accesstosql.md).  
  
-   Pour personnaliser le mappage des types de données source et cible, consultez [Source de mappage et les Types de données cible](mapping-source-and-target-data-types-accesstosql.md).  
  
-   Si vous n’avez pas à effectuer ces tâches, vous pouvez convertir les définitions d’objets de base de données Access dans les définitions d’objets SQL Azure. Pour plus d’informations, consultez [bases de données Access conversion](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Migration bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
