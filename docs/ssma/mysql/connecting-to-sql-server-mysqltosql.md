---
title: Connexion à SQL Server (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- connecting to SQL Server 2008, SQL Server permission
- connecting to SQL Server 2008, synchronization
ms.assetid: 08233267-693e-46e6-9ca3-3a3dfd3d2be7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 0ec33e462f1b68d70a86a0fbf4f7cf0214d25770
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68103127"
---
# <a name="connecting-to-sql-server-mysqltosql"></a>Connexion à SQL Server (MySQLToSQL)
Pour migrer des bases de données MySQL vers SQL Server, vous devez vous connecter à l’instance cible de SQL Server. Quand vous vous connectez, SSMA obtient les métadonnées relatives à toutes les bases de données dans l’instance de SQL Server et affiche les métadonnées de la base de données dans l’Explorateur de métadonnées SQL Server. SSMA stocke les informations de l’instance de SQL Server à laquelle vous êtes connecté, mais ne stocke pas les mots de passe.  
  
Votre connexion à SQL Server reste active jusqu’à ce que vous fermiez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter à SQL Server si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu’à ce que vous chargeant des objets de base de données dans SQL Server et migriez les données.  
  
Les métadonnées relatives à l’instance de SQL Server ne sont pas synchronisées automatiquement. Au lieu de cela, pour mettre à jour les métadonnées dans SQL Server Explorateur de métadonnées, vous devez mettre à jour manuellement les métadonnées de SQL Server. Pour plus d’informations, consultez la section « synchronisation des métadonnées de SQL Server » plus loin dans cette rubrique.  
  
## <a name="required-sql-server-permissions"></a>Autorisations de SQL Server requises  
Le compte utilisé pour se connecter à SQL Server nécessite des autorisations différentes en fonction des actions effectuées par le compte :  
  
-   Pour convertir des objets MySQL [!INCLUDE[tsql](../../includes/tsql-md.md)] en syntaxe, pour mettre à jour des métadonnées à partir de SQL Server, ou pour enregistrer la syntaxe convertie dans des scripts, le compte doit avoir l’autorisation de se connecter à l’instance de SQL Server.  
  
-   Pour charger des objets de base de données dans SQL Server, l’exigence d’autorisation minimale est l’appartenance au rôle de base de données **db_owner** dans la base de données cible.  
  
## <a name="establishing-a-sql-server-connection"></a>Établissement d’une connexion SQL Server  
Avant de convertir des objets de base de données MySQL en SQL Server syntaxe, vous devez établir une connexion à l’instance de SQL Server dans laquelle vous souhaitez migrer la ou les bases de données MySQL.  
  
Lorsque vous définissez les propriétés de connexion, vous spécifiez également la base de données dans laquelle les objets et les données seront migrés. Vous pouvez personnaliser ce mappage au niveau du schéma MySQL après vous être connecté à SQL Server. Pour plus d’informations, consultez [mappage de bases de données MySQL à des schémas de SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
> [!IMPORTANT]  
> Avant d’essayer de vous connecter à SQL Server, assurez-vous que l’instance de SQL Server est en cours d’exécution et peut accepter des connexions.  
  
**Pour se connecter à SQL Server**  
  
1.  Dans le menu **fichier** , sélectionnez **se connecter à SQL Server** (cette option est activée après la création d’un projet).  
  
    Si vous vous êtes déjà connecté à SQL Server, le nom de la commande sera **reconnecté à SQL Server**.  
  
2.  Dans la boîte de dialogue connexion, entrez ou sélectionnez le nom de l’instance de SQL Server.  
  
    -   Si vous vous connectez à l’instance par défaut sur l’ordinateur local, vous pouvez entrer **localhost** ou un point (**.**).  
  
    -   Si vous vous connectez à l’instance par défaut sur un autre ordinateur, entrez le nom de l’ordinateur.  
  
    -   Si vous vous connectez à une instance nommée sur un autre ordinateur, entrez le nom de l’ordinateur suivi d’une barre oblique inverse, puis du nom de l’instance, par exemple MyServer\MyInstance.  
  
3.  Si votre instance de SQL Server est configurée pour accepter les connexions sur un port autre que celui par défaut, entrez le numéro de port utilisé pour les connexions SQL Server dans la zone **port du serveur** . Pour l’instance par défaut de SQL Server, le numéro de port par défaut est 1433. Pour les instances nommées, SSMA essaiera d’obtenir le numéro de port à partir du service SQL Server Browser.  
  
4.  Dans la zone **authentification** , sélectionnez le type d’authentification à utiliser pour la connexion. Pour utiliser le compte Windows actuel, sélectionnez **authentification Windows**. Pour utiliser une connexion SQL Server, sélectionnez SQL Server l’authentification, puis entrez le nom de connexion et le mot de passe.  
  
5.  Pour une connexion sécurisée, deux contrôles sont ajoutés, les cases à cocher **chiffrer la connexion** et **TrustServerCertificate** . La case à cocher **TrustServerCertificate** est visible uniquement lorsque l’option **chiffrer la connexion** est activée. Lorsque l’option **chiffrer la connexion** est activée (true) et la valeur **TrustServerCertificate** est désactivée (false), elle valide le certificat SQL Server SSL. La validation du certificat de serveur est une partie de la négociation SSL qui garantit qu'il s'agit du serveur correct avec lequel établir une connexion. Pour ce faire, un certificat doit être installé côté client et du côté serveur.  
  
6.  Cliquez sur Se connecter.  
  
**Compatibilité de version supérieure**  
  
Il est autorisé à se connecter/se reconnecter à des versions ultérieures de SQL Server.  
  
1.  Vous serez en mesure de vous connecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à 2008 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou 2012 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou 2014 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou 2016 quand le projet créé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est 2005.  
  
2.  Vous serez en mesure de vous connecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à 2012 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou 2014 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou 2016 lorsque le projet créé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est 2008, mais qu’il n’est pas autorisé à se connecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aux versions inférieures, c.-à-d., 2005.  
  
3.  Vous serez en mesure de vous connecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à 2012 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou 2014 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou 2016 lorsque le projet créé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est 2012.  
  
4.  Vous ne pouvez vous connecter qu' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à 2014 ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 lorsque le projet créé est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014.  
  
5.  La compatibilité de version supérieure n’est pas valide pour « SQL Azure ».  
  
||||||||  
|-|-|-|-|-|-|-|  
|**TYPE de projet et VERSION du serveur cible**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005<br /> (Version : 9. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008<br /> (Version : 10. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012<br />(Version : 11. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014<br />(Version : 12. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016<br />(Version : 13. x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|Oui|Oui|Oui|Oui|Oui||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||Oui|Oui|Oui|Oui||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||Oui|Oui|Oui||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014||||Oui|Oui||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2016|||||Oui||  
|SQL Azure||||||Oui|  
  
> [!IMPORTANT]  
> La conversion des objets de base de données est effectuée en fonction du type de projet, mais pas de celui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la version de connectée à. Dans le cas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’un projet 2005, la conversion est effectuée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en fonction du nombre de 2005, même si vous êtes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connecté à une version plus récente de (SQL Server 2008/SQL Server 2012/SQL Server 2014/SQL Server 2016).  
  
## <a name="synchronizing-sql-server-metadata"></a>Synchronisation des métadonnées de SQL Server  
Les métadonnées relatives aux bases de données SQL Server ne sont pas automatiquement mises à jour. Les métadonnées dans SQL Server Explorateur de métadonnées sont un instantané des métadonnées lorsque vous vous êtes connecté pour la première fois à SQL Server, ou la dernière fois que vous avez mis à jour manuellement les métadonnées. Vous pouvez mettre à jour manuellement les métadonnées de toutes les bases de données ou d’une base de données ou d’un objet de base de données unique.  
  
**Pour synchroniser les métadonnées**  
  
1.  Assurez-vous que vous êtes connecté à SQL Server.  
  
2.  Dans SQL Server Explorateur de métadonnées, activez la case à cocher en regard de la base de données ou du schéma de base de données que vous souhaitez mettre à jour.  
  
    Par exemple, pour mettre à jour les métadonnées de toutes les bases de données, activez la case à cocher en regard de bases de données.  
  
3.  Cliquez avec le bouton droit sur bases de données, ou sur la base de données individuelle ou le schéma de base de données, puis sélectionnez **synchroniser avec la base de**données.  
  
## <a name="next-step"></a>étape suivante  
L’étape suivante de la migration dépend des besoins de votre projet :  
  
-   Pour personnaliser le mappage entre les schémas MySQL et les bases de données SQL Server et les schémas, consultez [mappage de bases de données MySQL à des schémas de SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
-   Pour personnaliser les options de configuration des projets, consultez [définition des options de projet &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)  
  
-   Pour personnaliser le mappage des types de données sources et cibles, consultez [mappage des types de données MySQL et SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   Si vous n’avez pas besoin d’effectuer ces tâches, vous pouvez convertir les définitions d’objet de base de données MySQL en SQL Server définitions d’objets. Pour plus d’informations, consultez [conversion de bases de données MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Migration de bases de données MySQL vers SQL Server-Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
