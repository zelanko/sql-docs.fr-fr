---
title: Connexion à SQL Server (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- authentication
- instance of SQL Server
- metadata, refreshing
- ports
- refreshing metadata
- spaces in database names
- special characters
- SQL Server
- SQL Server, connecting
- SQL Server, connecting to
- SQL Server, reconnecting
ms.assetid: f84cf007-ddf1-4396-a07c-3e0729abc769
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 4630ae8d92dbf0e9b1c5bf615dd82d436a5751f5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68006650"
---
# <a name="connecting-to-sql-server-accesstosql"></a>Connexion à SQL Server (AccessToSQL)
Pour migrer des bases de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]données Access vers, vous devez vous connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]l’instance cible de. Quand vous vous connectez, SSMA obtient les métadonnées relatives aux bases de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’instance de et affiche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les métadonnées de la base de données dans l’Explorateur de métadonnées. SSMA stocke des informations sur l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance de à laquelle vous êtes connecté, mais ne stocke pas les mots de passe.  
  
Votre connexion à SQL Server reste active jusqu’à ce que vous fermiez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter à SQL Server si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu’à ce que vous chargeant des objets de base de données dans SQL Server et migriez les données.  
  
Les métadonnées relatives à l’instance de SQL Server ne sont pas synchronisées automatiquement. Au lieu de cela, pour mettre à jour les métadonnées dans SQL Server Explorateur de métadonnées, vous devez mettre à jour manuellement les métadonnées de SQL Server. Pour plus d’informations, consultez la section « synchronisation des métadonnées de SQL Server » plus loin dans cette rubrique.  
  
## <a name="required-sql-server-permissions"></a>Autorisations de SQL Server requises  
Le compte utilisé pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requiert des autorisations différentes en fonction des actions effectuées par ce compte.  
  
-   Pour convertir des objets Access [!INCLUDE[tsql](../../includes/tsql-md.md)] en syntaxe, pour actualiser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]les métadonnées à partir de ou pour enregistrer la syntaxe convertie dans des scripts, le compte doit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]avoir l’autorisation de se connecter à l’instance de.  
  
-   Pour charger des objets de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données dans et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]migrer des données vers, l’exigence d’autorisation minimale est l’appartenance au rôle de base de données **db_owner** dans la base de données cible.  
  
## <a name="establishing-a-sql-server-connection"></a>Établissement d’une connexion SQL Server  
Avant de convertir des objets de base [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de données Access en syntaxe, vous devez établir une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’instance de dans laquelle vous souhaitez migrer les bases de données Access.  
  
Lorsque vous définissez les propriétés de connexion, vous spécifiez également la base de données dans laquelle les objets et les données seront migrés. Vous pouvez personnaliser ce mappage au niveau de la base de données Access après [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]vous être connecté à. Pour plus d’informations, consultez [mappage des bases de données source et cible](mapping-source-and-target-databases-accesstosql.md).  
  
> [!IMPORTANT]  
> Avant de vous connecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]à, assurez-vous que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’instance de est en cours d’exécution et peut accepter des connexions. Pour plus d’informations, consultez « connexion au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] moteur de base de données » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne de.  
  
**Pour se connecter à SQL Server**  
  
1.  Dans le menu **fichier** , sélectionnez **se connecter à SQL Server**.  
  
    Si vous vous êtes connecté [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]précédemment à, le nom de la commande sera **reconnecté à SQL Server**.  
  
2.  Dans la zone **nom du serveur** , entrez ou sélectionnez le nom de l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de.  
  
    -   Si vous vous connectez à l’instance par défaut sur l’ordinateur local, vous pouvez entrer **localhost** ou un point (**.**).  
  
    -   Si vous vous connectez à l’instance par défaut sur un autre ordinateur, entrez le nom de l’ordinateur.  
  
    -   Si vous vous connectez à une instance nommée, entrez le nom de l’ordinateur, une barre oblique inverse et le nom de l’instance. Par exemple : MyServer\MyInstance.  
  
    -   Pour vous connecter à une instance utilisateur active [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)]de, connectez-vous à l’aide du protocole de canaux nommés et en \\ \\spécifiant le nom du canal, par exemple .\pipe\sql\query. Pour plus d’informations, consultez la documentation de [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)].  
  
3.  Si votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configurée pour accepter les connexions sur un port autre que celui par défaut, entrez le numéro de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] port utilisé pour les connexions dans la zone **port du serveur** . Pour l’instance par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de, le numéro de port par défaut est 1433. Pour les instances nommées, SSMA essaiera d’obtenir le numéro de port [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auprès du service Browser.  
  
4.  Dans la zone **base de données** , entrez le nom de la base de données cible pour la migration des données et des objets.  
  
    Cette option n’est pas disponible lors de la reconnexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    Le nom de la base de données cible ne peut pas contenir d’espaces ou de caractères spéciaux. Par exemple, vous pouvez migrer des bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Access vers une base de données nommée « ABC ». Toutefois, vous ne pouvez pas migrer des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données Access vers une base de données nommée « a b-c ».  
  
    Vous pouvez personnaliser ce mappage par base de données une fois que vous êtes connecté. Pour plus d’informations, consultez [mappage des bases de données source et cible](mapping-source-and-target-databases-accesstosql.md) .  
  
5.  Dans le menu déroulant **authentification** , sélectionnez le type d’authentification à utiliser pour la connexion. Pour utiliser le compte Windows actuel, sélectionnez **authentification Windows**. Pour utiliser une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion, sélectionnez **SQL Server l’authentification**, puis entrez un nom d’utilisateur et un mot de passe.  
  
6.  Pour une connexion sécurisée, la case à cocher **chiffrer la connexion** et la case à cocher **TrustServerCertificate** s’ajoutent. Cette **case à cocher est activée uniquement** lorsque la case **chiffrer la connexion** est cochée. Lorsque l’option **chiffrer la connexion** est activée (true) et la valeur **TrustServerCertificate** est désactivée (false), valide le certificat SSL SQL Server. La validation du certificat de serveur est une partie de la négociation SSL qui garantit qu'il s'agit du serveur correct avec lequel établir une connexion. Pour ce faire, un certificat doit être installé côté client et du côté serveur.  
  
7.  Cliquez sur **Connecter**.  
  
**Compatibilité de version supérieure**  
  
Il est autorisé à se connecter/se reconnecter à des versions ultérieures de SQL Server.  
  
1.  Vous serez en mesure de vous connecter à SQL Server 2008 ou à SQL Server 2012 lorsque le projet créé est SQL Server 2005.  
  
2.  Vous serez en mesure de vous connecter à SQL Server 2012 lorsque le projet créé est SQL Server 2008, mais qu’il n’est pas autorisé à se connecter à des versions inférieures, par exemple SQL Server 2005.  
  
3.  Vous ne pouvez vous connecter qu’à SQL Server 2012 lorsque le projet créé est SQL Server 2012.  
  
4.  La compatibilité de version supérieure n’est pas valide pour SQL Azure.  
  
||||||||
|-|-|-|-|-|-|-|
|**TYPE de projet et VERSION du serveur cible**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 (version : 9. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2008 (version : 10. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2012 (version : 11. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014 (version : 12. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2016 (version : 13. x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|Oui|Oui|Oui|Oui|Oui||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||Oui|Oui|Oui|Oui||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||Oui|Oui|Oui||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014||||Oui|Oui||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016|||||Oui||
|SQL Azure||||||Oui|
  
> [!IMPORTANT]  
> La conversion des objets de base de données est effectuée en fonction du type de projet, mais pas de la version de la SQL Server connectée. Dans le cas d’SQL Server projet 2005, la conversion est effectuée en fonction du SQL Server 2005, même si vous êtes connecté à une version plus récente de SQL Server (SQL Server 2008/SQL Server 2012/SQL Server 2014/SQL Server 2016).  
  
## <a name="synchronizing-sql-server-metadata"></a>Synchronisation des métadonnées de SQL Server  
Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les schémas changent après la connexion, vous pouvez synchroniser les métadonnées avec le serveur.  
  
**Pour synchroniser les métadonnées SQL Server**  
  
-   Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’Explorateur de métadonnées, cliquez avec le bouton droit sur **bases de données**, puis sélectionnez **synchroniser avec la base de données**.  
  
## <a name="reconnecting-to-sql-server"></a>Reconnexion à SQL Server  
Votre connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reste active jusqu’à ce que vous fermiez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu’à ce que vous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chargeant des objets de base de données dans et migriez les données.  
  
La procédure de reconnexion à est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identique à celle de la procédure d’établissement d’une connexion.  
  
## <a name="next-steps"></a>Étapes suivantes  
Si vous souhaitez personnaliser le mappage entre les bases de données source et cible, consultez [mappage des bases de données source et cible](mapping-source-and-target-databases-accesstosql.md) . dans le cas contraire, l’étape [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suivante consiste à convertir des objets de base de données en syntaxe à l’aide de [Convert Database Objects](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Migration de bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
