---
title: Autorisations
description: Cet article décrit la configuration requise et les options de gestion des autorisations de base de données pour les Data Warehouse parallèles.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 499ac56d8a462f62dac92b97654a9ace12bd356e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "79289687"
---
# <a name="managing-permissions-in-parallel-data-warehouse"></a>Gestion des autorisations dans les Data Warehouse parallèles
Cet article décrit la configuration requise et les options de gestion des autorisations de base de données pour SQL Server PDW.

## <a name="database-engine-permission-basics"></a><a name="BackupRestoreBasics"></a>Notions de base des autorisations Moteur de base de données
Les autorisations Moteur de base de données sur les SQL Server PDW sont gérées au niveau du serveur par le biais de connexions et au niveau de la base de données via les utilisateurs de base de données et les rôles de base de données définis par l’utilisateur.

**Connexions** Les connexions sont des comptes d’utilisateur individuels pour la connexion au SQL Server PDW. SQL Server PDW prend en charge les connexions à l’aide de l’authentification Windows et de l’authentification SQL Server.  Les connexions d’authentification Windows peuvent être des utilisateurs Windows ou des groupes Windows à partir de n’importe quel domaine approuvé par SQL Server PDW. SQL Server les connexions d’authentification sont définies et authentifiées par SQL Server PDW et doivent être créées en spécifiant un mot de passe.

Les membres du rôle serveur fixe **sysadmin** (par exemple, la connexion **sa** ) peuvent se connecter à une base de données sans avoir été mappés à un utilisateur de base de données. Ils sont mappés à l’utilisateur **dbo** . Le propriétaire de la base de données est également mappé en tant qu’utilisateur **dbo** .

**Rôles de serveur** Il existe quatre rôles de serveur spéciaux avec un ensemble de rôles préconfigurés qui fournissent un groupe pratique d’autorisations au niveau du serveur. Les rôles de serveur **sysadmin**, **MediumRC**, **LargeRC**et **XLargeRCfixed** sont les seuls rôles de serveur actuellement implémentés dans SQL Server PDW. La connexion **sa** est le seul membre du rôle serveur fixe **sysadmin** , et les connexions supplémentaires ne peuvent pas être ajoutées au rôle **sysadmin** . Les connexions peuvent être accordées à l’autorisation **Control Server** , qui est similaire, bien que non identique, au rôle serveur fixe **sysadmin** . Utilisez [ALTER Server Role](../t-sql/statements/alter-server-role-transact-sql.md) pour ajouter des membres aux autres rôles de serveur. SQL Server PDW ne prend pas en charge les rôles de serveur définis par l’utilisateur.

**Utilisateurs de base de données** Les connexions sont autorisées à accéder à une base de données en créant un utilisateur de base de données dans une base de données et en mappant cet utilisateur de base de données à une connexion. En général, le nom d’utilisateur de base de données est le même que le nom de connexion, mais ce n’est pas obligatoire. Chaque utilisateur de base de données est mappé à une seule connexion. Une connexion ne peut être mappée qu’à un seul utilisateur dans une base de données, mais peut être mappée comme utilisateur de base de données dans plusieurs bases de données.

**Rôles de base de données fixes** Les rôles de base de données fixes sont un ensemble de rôles préconfigurés qui fournissent un groupe pratique d’autorisations au niveau de la base de données. Les utilisateurs de base de données et les rôles de base de données définis par l’utilisateur peuvent être ajoutés aux rôles de base de données fixes à l’aide de la procédure [sp_addrolemember](../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) . Pour plus d’informations sur les rôles de base de données fixes, consultez [rôles de base de données fixes](#fixed-database-roles).

**Rôles de base de données définis par l’utilisateur** Les utilisateurs disposant de l’autorisation **CREATE ROLE** peuvent créer des rôles de base de données définis par l’utilisateur pour représenter des groupes d’utilisateurs disposant d’autorisations communes. En général, les autorisations sont accordées ou refusées à l’ensemble du rôle, ce qui simplifie la gestion et la surveillance des autorisations.

Les autorisations sont accordées aux principaux de sécurité (connexions, utilisateurs et rôles) à l’aide de l’instruction **Grant** . Les autorisations sont refusées explicitement à l’aide de la commande **Deny** . Une autorisation précédemment accordée ou refusée est supprimée à l’aide de l’instruction **Revoke** . Les autorisations sont cumulatives : l’utilisateur bénéficie de toutes les autorisations accordées à lui-même, à la connexion et à toute appartenance à un groupe. Toutefois, tout refus d’autorisation remplace toutes les attributions. <!-- MISSING LINKS (For information, syntax, and available permissions with these commands, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md)).  -->

L’exemple suivant illustre une méthode courante et recommandée pour configurer des autorisations.

1.  Si vous utilisez l’authentification Windows, créez une connexion pour chaque utilisateur Windows ou groupe Windows qui se connectera à SQL Server PDW. Si vous utilisez l’authentification SQL Server, créez une connexion pour chaque personne qui se connectera à SQL Server PDW.

2.  Créez un utilisateur de base de données pour chaque connexion dans toutes les bases de données nécessaires.

3.  Créez un ou plusieurs rôles de base de données définis par l’utilisateur, chacun représentant une fonction similaire. Par exemple, analyste financier et analyste des ventes.

4.  Ajoutez des utilisateurs de base de données à un ou plusieurs rôles de base de données définis par l’utilisateur.

5.  Accordez des autorisations aux rôles de base de données définis par l’utilisateur.

Les connexions sont des objets de niveau serveur et peuvent être répertoriées en affichant [sys. server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md). Seules les autorisations au niveau du serveur peuvent être accordées aux principaux de serveur.

Les utilisateurs et les rôles de base de données sont des objets de niveau base de données et peuvent être répertoriés en affichant [sys. database_principals](../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md). Seules les autorisations au niveau de la base de données peuvent être accordées aux principaux de base de données.

## <a name="default-permissions"></a><a name="BackupTypes"></a>Autorisations par défaut
La liste suivante décrit les autorisations par défaut :

-   Lorsqu’une connexion est créée à l’aide de l’instruction **Create login** , la connexion reçoit l’autorisation **Connect SQL** , ce qui permet à la connexion de se connecter au SQL Server PDW.

-   Lorsqu’un utilisateur de base de données est créé à l’aide de l’instruction **Create User** , il reçoit l’autorisation **Connect on database ::** _<database_name>_ , ce qui permet à la connexion de se connecter à cette base de données en tant qu’utilisateur.

-   Tous les principaux, y compris le rôle PUBLIC, n’ont pas d’autorisations explicites ou implicites par défaut, car les autorisations implicites sont héritées des autorisations explicites. Par conséquent, si aucune autorisation explicite n’est présente, il ne peut pas non plus y avoir d’autorisations implicites.

-   Lorsqu’une connexion devient le propriétaire d’un objet ou d’une base de données, la connexion a toujours toutes les autorisations sur l’objet ou la base de données. Les autorisations de propriété ne sont pas visibles en tant qu’autorisations explicites. Les instructions **Grant**, **Revoke**et **Deny** n’ont aucun effet sur les autorisations de propriété. La propriété peut être modifiée à l’aide de l’instruction [ALTER AUTHORIZATION](../t-sql/statements/alter-authorization-transact-sql.md) .

-   La connexion AS a toutes les autorisations sur l’appliance. De même que les autorisations de propriété, les autorisations AS ne peuvent pas être changées et ne sont pas visibles comme des autorisations explicites. Les instructions **Grant**, **Revoke**et **Deny** n’ont aucun effet sur les autorisations d’administrateur système.

-   Le rôle de serveur PUBLIC ne reçoit pas d’autorisations par défaut et n’hérite pas des autorisations d’autres rôles de serveur. Le rôle serveur PUBLIC peut recevoir des autorisations explicites avec les instructions **Grant**, **Revoke**et **Deny** .

-   Les transactions ne nécessitent pas d’autorisations. Tous les principaux peuvent exécuter les commandes **Begin transaction**, **Commit**et **Rollback** transaction. Toutefois, un principal doit disposer des autorisations appropriées pour exécuter chaque instruction au sein de la transaction.

-   L’instruction **USE** n’a pas besoin d’autorisation. Tous les principaux peuvent exécuter l’instruction **use** sur n’importe quelle base de données. Toutefois, pour accéder à une base de données, ils doivent avoir un principal d’utilisateur dans la base de données ou l’utilisateur invité doit être activé.

### <a name="the-public-role"></a>Rôle PUBLIC
Toutes les nouvelles connexions d’appliance appartiennent automatiquement au rôle PUBLIC. Le rôle serveur PUBLIC possède les caractéristiques suivantes :

-   Le rôle serveur PUBLIC n’a pas d’autorisations par défaut.

-   Tous les principaux sont membres du rôle serveur PUBLIC et le rôle serveur PUBLIC n’est pas membre d’un autre rôle serveur.

-   Le rôle serveur PUBLIC ne peut pas hériter des autorisations implicites. Toutes les autorisations accordées au rôle PUBLIC doivent être accordées explicitement.

## <a name="determining-permissions"></a><a name="BackupProc"></a>Détermination des autorisations
Le fait qu’une connexion ait ou non l’autorisation d’effectuer une action spécifique dépend des autorisations accordées ou refusées à la connexion, à l’utilisateur et aux rôles dont l’utilisateur est membre. Les autorisations au niveau du serveur (telles que **Create login** et **View Server State**) sont disponibles pour les principaux de niveau serveur (connexions). Les autorisations au niveau de la base de données (telles que **Select** dans une table ou **Execute** sur une procédure) sont disponibles pour les principaux au niveau de la base de données (utilisateurs et rôles de base de données).

### <a name="implicit-and-explicit-permissions"></a>Autorisations implicites et explicites
Une *autorisation explicite* est une autorisation **GRANT** ou **DENY** donnée à un principal par une instruction **GRANT** ou **DENY**. Les autorisations au niveau de la base de données sont répertoriées dans la vue [sys. database_permissions](../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md) . Les autorisations au niveau du serveur sont répertoriées dans la vue [sys. server_permissions](../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) .

Une *autorisation implicite* est une autorisation **Grant** ou **Deny** qu’un principal (connexion ou rôle de serveur) a hérité. Une autorisation peut être héritée des manières suivantes.

-   Un principal peut hériter d’une autorisation d’un rôle si le principal est membre du rôle même si le principal ne dispose pas d’une autorisation **Grant** ou **Deny** explicite.

-   Un principal peut hériter d’une autorisation sur un objet subordonné (par exemple, une table) si le principal a une autorisation sur l’une des étendues parentes des objets (par exemple, le schéma de la table ou l’autorisation sur l’ensemble de la base de données).

-   Un principal peut hériter d’une autorisation en ayant une autorisation qui comprend une autorisation subordonnée. Par exemple, l’autorisation **ALTER ANY User** comprend les autorisations **Create User** et **ALTER on User ::** _<name>_ Permissions.

### <a name="determining-permissions-when-performing-actions"></a>Détermination des autorisations lors de l’exécution d’actions
Le processus de détermination de l’autorisation à assigner à un principal est complexe. La complexité se produit lors de la détermination des autorisations implicites, car les principaux peuvent être membres de plusieurs rôles et les autorisations peuvent être transmises via plusieurs niveaux dans la hiérarchie des rôles.

La liste suivante décrit les règles générales permettant de déterminer les autorisations :

-   La propriété implique l’autorisation.

    Un propriétaire d’objet dispose de toutes les autorisations sur l’objet. De même, le propriétaire d’une base de données dispose de toutes les autorisations sur la base de données et de toutes les autorisations sur les objets de la base de données. Ces autorisations ne peuvent pas être modifiées.

-   Les autorisations peuvent être héritées sur plusieurs niveaux dans la hiérarchie des appartenances aux rôles de serveur.

    Supposons, par exemple, que vous ayez la situation suivante :

    -   La connexion David est membre du rôle de base de données PerfAnalysts.

    -   PerfAnalysts est membre de la production du rôle de base de données.

    -   David et PerfAnalysts ne disposent pas de l’autorisation **Select** sur la table Customer. L’autorisation a été révoquée ou n’a jamais été explicitement accordée.

    -   La production dispose d’une autorisation **Select** sur la table Customer.

    Dans ce cas, PerfAnalysts hérite de l’autorisation **Grant** sur la table Customer de production, et David hérite de l’autorisation **Grant** sur la table Customer de production.

-   **Deny** remplace les autorisations **lorsque des** autorisations sont en conflit.

    Par exemple, supposons que la connexion David n’ait pas d’autorisations sur la table Customer et qu’elle est membre de deux rôles de base de données : dbgroup1, qui a l’autorisation **Deny** sur la table Customer et dbgroup2, qui dispose de l’autorisation **Grant** sur la table Customer. Dans ce cas, David héritera de l’autorisation **Deny** sur la table Customer. C’est le cas si les rôles ont obtenu leurs autorisations de manière explicite ou implicite.

### <a name="auditing-permissions"></a>Audit des autorisations
Pour rechercher les autorisations d’un utilisateur, vérifiez les éléments suivants.

-   Exécutez la requête suivante pour déterminer les connexions qui sont des administrateurs système.

    ```sql
    SELECT SPLogins.name, 'is a member of ', SPRoles.name 
    FROM sys.server_role_members AS SRM 
    JOIN sys.server_principals AS SPRoles 
        ON SRM.role_principal_id = SPRoles.principal_id 
    JOIN sys.server_principals AS SPLogins 
        ON SRM.member_principal_id = SPLogins.principal_id;
    ```

-   Exécutez la requête suivante pour déterminer les connexions qui ont reçu des autorisations explicites.

    ```sql
    SELECT name, 'has the ', state_desc , permission_name, ' permission'
    FROM sys.server_permissions AS SP
    JOIN sys.server_principals AS SPRoles 
        ON SP.grantee_principal_id = SPRoles.principal_id;
    ```

-   Exécutez la requête suivante dans une base de données utilisateur pour déterminer les utilisateurs de base de données qui sont membres d’un rôle de base de données.

    ```sql
    SELECT DPUsers.name, 'is a member of ', DPRoles.name  
    FROM sys.database_role_members AS DRM
    JOIN sys.database_principals AS DPRoles 
        ON DRM.role_principal_id = DPRoles.principal_id
    JOIN sys.database_principals AS DPUsers
        ON DRM.member_principal_id = DPUsers.principal_id;
    ```

-   Exécutez la requête suivante dans une base de données utilisateur pour déterminer les utilisateurs et les rôles de base de données auxquels des autorisations spécifiques ont été accordées ou refusées. Vous devez interroger des vues supplémentaires telles que sys. Objects et sys. schemas pour identifier les éléments décrits avec l’major_id.

    ```sql
    SELECT DPUsers.name, 'has the ', permission_name, 
    'permission on the item described as class = ', class, 'id = ', major_id
    FROM sys.database_permissions AS DP
    JOIN sys.database_principals AS DPUsers
        ON DP.grantee_principal_id = DPUsers.principal_id;
    ```

## <a name="database-permissions-best-practices"></a><a name="RestoreProc"></a>Meilleures pratiques relatives aux autorisations de base de données

-   Accordez des autorisations au niveau le plus granulaire qui est pratique. L’octroi d’autorisations au niveau de la table ou de la vue peut devenir impossible à gérer. Toutefois, l’octroi d’autorisations au niveau de la base de données peut être trop permissif. Si la base de données est conçue avec des schémas pour définir des limites de travail, peut-être que l’autorisation accordée au schéma est un compromis approprié entre le niveau de la table et le niveau de la base de données.

-   Accordez des autorisations à des rôles, plutôt qu’à des utilisateurs ou à des connexions. La gestion des droits à l’aide de rôles au lieu des utilisateurs permet d’accorder ou de révoquer rapidement un ensemble d’autorisations pour un utilisateur ou une connexion en les déplaçant dans ou en dehors du rôle. Lorsqu’une fonction passe d’une personne à une autre, les autorisations peuvent rester intactes au niveau du rôle pendant que l’appartenance au rôle change.

-   Accordez des autorisations aux rôles en fonction de la fonction et sur des rôles de groupe de niveau supérieur qui combinent les rôles de fonction de travail en fonction du groupe d’entreprise effectuant les actions.

-   Chaque utilisateur final doit avoir une connexion unique. N’autorisez pas les utilisateurs à partager des connexions. Fournir une connexion pour chaque utilisateur garantit une piste d’audit et simplifie la gestion des autorisations.

## <a name="fixed-database-roles"></a>Rôles de base de données fixes
SQL Server fournit des rôles préconfigurés au niveau de la base de données pour vous aider à gérer les autorisations sur un serveur. Les rôles préconfigurés sont résolus, car vous ne pouvez pas modifier les autorisations qui leur sont attribuées. Des rôles de base de données définis par l’utilisateur peuvent également être créés. Vous pouvez modifier les autorisations affectées aux rôles de base de données définis par l’utilisateur.

Les rôles sont des principaux de sécurité qui regroupent d’autres principaux. Les rôles de base de données sont à l’échelle de la base de données dans leur étendue d’autorisations. Les utilisateurs de base de données et autres rôles de base de données peuvent être ajoutés en tant que membres des rôles de base de données. Les rôles de base de données fixes ne peuvent pas être ajoutés les uns aux autres. (Les*rôles* sont semblables aux *groupes* du système d’exploitation Microsoft Windows.)

Il existe 9 rôles de base de données fixes.

-   **db_owner**

-   **db_securityadmin**

-   **db_accessadmin**

-   **db_backupoperator**

-   **db_ddladmin**

-   **db_datawriter**

-   **db_datareader**

-   **db_denydatawriter**

-   **db_denydatareader**

### <a name="permissions-of-the-fixed-database-roles"></a>Autorisations des rôles de base de données fixes
Le système des rôles serveur fixes et des rôles de base de données fixes est un système hérité issu des versions 1980. Les rôles fixes sont toujours pris en charge et sont utiles dans les environnements où il y a peu d’utilisateurs et les besoins en matière de sécurité sont simples. À partir de SQL Server 2005, un système plus détaillé d’octroi d’autorisation a été créé. Ce nouveau système est plus granulaire et offre de nombreuses autres options pour accorder et refuser des autorisations. La complexité supplémentaire du système plus granulaire rend plus difficile l’apprentissage, mais la plupart des systèmes d’entreprise doivent accorder des autorisations au lieu d’utiliser les rôles fixes. <!-- MISSING LINKS The permissions are discussed and listed in the topic [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md). -->Le graphique suivant montre les autorisations associées à chaque rôle de base de données fixe. Toutes les autorisations de ce graphique SQL Server ne sont pas disponibles (ou nécessaires) dans APS.

![Rôles de base de données fixes de sécurité APS](./media/pdw-permissions/APS_security_fixed_db_roles.png "APS_security_fixed_db_roles")

### <a name="related-content"></a>Contenu associé

-   Pour créer des rôles définis par l’utilisateur, voir [CREATE ROLE](../t-sql/statements/create-role-transact-sql.md).


## <a name="fixed-server-roles"></a>Rôles serveur fixes
Les rôles serveur fixes sont créés automatiquement par SQL Server. SQL Server PDW a une implémentation limitée de SQL Server rôles serveur fixes. Seuls les utilisateurs **sysadmin** et **public** ont des connexions utilisateur en tant que membres. Les rôles **setupadmin** et **dbcreator** sont utilisés en interne par SQL Server PDW. Des membres supplémentaires ne peuvent pas être ajoutés ou supprimés d’un rôle.

### <a name="sysadmin-fixed-server-role"></a>Rôle serveur fixe sysadmin
Les membres du rôle serveur fixe **sysadmin** peuvent effectuer n’importe quelle activité sur le serveur. La connexion **sa** est le seul membre du rôle serveur fixe **sysadmin** . Impossible d’ajouter des connexions supplémentaires au rôle serveur fixe **sysadmin** . L’accord de l’autorisation**CONTROL SERVER** s’apparente à une appartenance au rôle serveur fixe **sysadmin**. L’exemple suivant accorde l’autorisation **Control Server** à une connexion nommée Fay.

```sql
USE master;
GO
GRANT CONTROL SERVER TO Fay;
```

> [!IMPORTANT]
> L’autorisation **Control Server** fournit un contrôle presque complet de SQL Server PDW. Dans la mesure du possible, fournissez des autorisations plus granulaires aux connexions à la place. Par exemple, envisagez d’accorder l' **État du serveur d’affichage**, de **modifier une connexion**, d' **afficher une base de données**ou de **créer des autorisations de base de données** .

### <a name="public-server-role"></a>Rôle de serveur public
Chaque connexion qui peut se connecter à SQL Server PDW est membre du rôle serveur **public** . Toutes les connexions héritent des autorisations accordées à **public** sur n’importe quel objet. Affectez uniquement des autorisations **publiques** à un objet lorsque vous souhaitez que l’objet soit disponible pour tous les utilisateurs. Vous ne pouvez pas modifier l’appartenance au rôle **public** .

> [!NOTE]
> **public** est implémenté différemment des autres rôles. Étant donné que tous les principaux de serveur sont membres de public, l’appartenance du rôle **public** n’est pas répertoriée dans la DMV **sys. server_role_members** .

### <a name="fixed-server-roles-vs-granting-permissions"></a>Rôles serveur fixes et octroi d’autorisations
Le système des rôles serveur fixes et des rôles de base de données fixes est un système hérité issu des versions 1980. Les rôles fixes sont toujours pris en charge et sont utiles dans les environnements où il y a peu d’utilisateurs et les besoins en matière de sécurité sont simples. À partir de SQL Server 2005, un système plus détaillé d’octroi d’autorisation a été créé. Ce nouveau système est plus granulaire et offre de nombreuses autres options pour accorder et refuser des autorisations. La complexité supplémentaire du système plus granulaire rend plus difficile l’apprentissage, mais la plupart des systèmes d’entreprise doivent accorder des autorisations au lieu d’utiliser les rôles fixes. <!-- MISSING LINKS The permissions are discussed and listed in the topic [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  -->

## <a name="related-topics"></a>Rubriques connexes

- [Accorder des autorisations](grant-permissions.md)

<!-- MISSING LINKS
## See Also
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)
-->

