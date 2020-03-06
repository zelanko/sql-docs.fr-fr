---
title: Accorder des autorisations T-SQL
description: Accordez des autorisations T-SQL pour les opérations de base de données en parallèle Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6bbe78979c393490a52e1051fe158ae138f93dcc
ms.sourcegitcommit: ff1bd69a8335ad656b220e78acb37dbef86bc78a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78339568"
---
# <a name="grant-t-sql-permissions-for-parallel-data-warehouse"></a>Accorder des autorisations T-SQL pour des Data Warehouse parallèles
Accordez des autorisations T-SQL pour les opérations de base de données en parallèle Data Warehouse.

## <a name="grant-permissions-to-submit-database-queries"></a>Accorder des autorisations pour envoyer des requêtes de base de données
Cette section décrit comment accorder des autorisations aux utilisateurs et aux rôles de base de données pour interroger des données sur l’appareil SQL Server PDW.  
  
Les instructions utilisées pour accorder des autorisations aux données de requête dépendent de l’étendue de l’accès souhaité. Les instructions SQL suivantes créent une connexion nommée KimAbercrombie qui peut accéder à l’appliance, créer un utilisateur de base de données nommé KimAbercrombie dans la base de données **AdventureWorksPDW2012** , créer un rôle de base de données nommé PDWQueryData, ajouter le KimAbercrombie à l’PDWQueryData, puis afficher les options d’octroi d’accès à la requête, selon que l’accès est accordé au niveau de l’objet ou de la base de données.  
  
```sql  
USE master;  
GO  
  
CREATE LOGIN KimAbercrombie WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
USE AdventureWorksPDW2012;  
GO  
  
CREATE USER KimAbercrombie;  
GO  
  
CREATE ROLE PDWQueryData;  
GO  
  
EXEC sp_addrolemember 'PDWQueryData', 'KimAbercrombie'  
GO  
  
-- If the permission is granted against a table or view only, use this syntax:  
GRANT SELECT ON OBJECT::AdventureWorksPDW2012..DimEmployee TO PDWQueryData;  
GO  
  
-- If the permission is granted for the database, use this syntax:  
GRANT SELECT ON DATABASE::AdventureWorksPDW2012 TO PDWQueryData;  
GO  
  
-- If KimAbercrombie is the only user that needs to access a table, use this syntax:  
GRANT SELECT ON OBJECT::AdventureWorksPDW2012..DimEmployee TO KimAbercrombie;  
GO  
```  
  
## <a name="grant-permissions-to-use-the-admin-console"></a>Accorder des autorisations pour utiliser la console d’administration
Cette section décrit comment accorder des autorisations à des connexions pour utiliser la console d’administration.  
  
**Utiliser la console d’administration**  
  
Pour utiliser la console d’administration, un compte de connexion nécessite l’autorisation **View Server State** au niveau du serveur. L’instruction SQL suivante accorde l’autorisation **View Server State** à la connexion `KimAbercrombie` afin que Kim puisse utiliser la console d’administration pour surveiller l’appareil SQL Server PDW.  
  
```sql  
USE master;  
GO  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
GO  
```  
  
**Terminer les sessions**  
  
Pour accorder à un compte de connexion l’autorisation d’arrêter des sessions, accordez l’autorisation **ALTER ANY Connection** comme suit :  
  
```sql  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
## <a name="grant-permissions-to-load-data"></a>Accorder des autorisations pour charger des données
Cette section décrit comment accorder des autorisations aux rôles de base de données et aux utilisateurs de base de données pour charger des données sur le SQL Server PDWappliance.  
  
Le script suivant montre les autorisations requises pour chaque option de chargement. Vous pouvez modifier cela pour répondre à vos besoins spécifiques.  
  
```sql  
-- Create server login for the examples that follow.  
USE master;  
CREATE LOGIN BI_ETLUser WITH PASSWORD = '******';  
  
--Grant BULK Load permissions   
GRANT ADMINISTER BULK OPERATIONS TO BI_ETLUser;  
  
--Grant Staging database permissions  
USE stagedb;  
CREATE USER BI_ETLUser for login BI_ETLUser;  
EXEC sp_addrolemember 'db_datareader','BI_ETLUser';  
EXEC sp_addrolemember 'db_datawriter','BI_ETLUser';  
EXEC sp_addrolemember 'db_ddladmin','BI_ETLUser';  
  
-- The CREATE TABLE permission is required for the database hosting the temporary table.  
-- This may be the staging database (if specified) or destination database.   
-- The CREATE permission is not required if loading in fastappend mode.  
GRANT CREATE TABLE ON database::stagedb TO BI_ETLUser;  
  
-- If loading in append or fastappend mode, the INSERT permission is required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
  
-- If loading in reload mode, the INSERT and DELETE permissions are required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
GRANT DELETE ON database::stagedb TO BI_ETLUser;  
  
-- If loading in upsert mode, the INSERT and UPDATE permissions are required on the destination table.  
GRANT INSERT ON database::stagedb TO BI_ETLUser;  
GRANT UPDATE ON database::stagedb TO BI_ETLUser;  
  
-- Destination DB  
USE tpch_1gb;  
CREATE USER BI_ETLUser FOR LOGIN BI_ETLUser;  
EXEC sp_addrolemember 'db_datareader','BI_ETLUser';  
EXEC sp_addrolemember 'db_datawriter','BI_ETLUser';  
```  
  
## <a name="grant-permissions-to-copy-data-off-the-appliance"></a>Accorder des autorisations à Copier des données hors de l’appliance
Cette section explique comment accorder des autorisations à un utilisateur ou à un rôle de base de données pour copier des données de l’appareil SQL Server PDW.  
  
Pour déplacer des données vers un autre emplacement, vous devez disposer de l’autorisation **Select** sur la table contenant les données à déplacer.  
  
Si la destination des données est une autre SQL Server PDW, l’utilisateur doit disposer de l’autorisation **Create table** au niveau de la destination et de l’autorisation **ALTER Schema** sur le schéma qui contiendra la table.  
  
## <a name="grant-permissions-to-manage-databases"></a>Accorder des autorisations pour gérer les bases de données
Cette section décrit comment accorder des autorisations à un utilisateur de base de données pour gérer une base de données sur l’appareil SQL Server PDW.  
  
Dans certains cas, une entreprise affecte un responsable pour une base de données. Le gestionnaire contrôle l’accès des autres connexions à la base de données, ainsi que les données et les objets de la base de données. Pour gérer tous les objets, rôles et utilisateurs dans une base de données, accordez à l’utilisateur l’autorisation **Control** sur la base de données. L’instruction suivante accorde à l’utilisateur `KimAbercrombie`l’autorisation **Control** sur la base de données **AdventureWorksPDW2012** .  
  
```sql
USE AdventureWorksPDW2012;  
GO  
GRANT CONTROL ON DATABASE:: AdventureWorksPDW2012 TO KimAbercrombie;  
```  
  
Pour accorder à un utilisateur l’autorisation de contrôler toutes les bases de données de l’appliance, accordez l’autorisation **ALTER ANY DATABASE** dans la base de données Master.  
  
## <a name="grant-permissions-to-manage-logins-users-and-database-roles"></a>Accorder des autorisations pour gérer les connexions, les utilisateurs et les rôles de base de données
Cette section décrit comment accorder des autorisations pour gérer les connexions, les utilisateurs de base de données et les rôles de base de données.  
  
### <a name="PermsAdminConsole"></a>Accorder des autorisations pour gérer les connexions  
**Ajouter ou gérer des connexions**  
  
Les instructions SQL suivantes créent une connexion nommée KimAbercrombie qui peut créer de nouvelles connexions à l’aide de l’instruction [Create login](../t-sql/statements/create-login-transact-sql.md) et modifier les connexions existantes à l’aide de l’instruction [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md) .  
  
L’autorisation **ALTER ANY login** donne la possibilité de créer de nouvelles connexions et de supprimer des existantes. Une fois qu’il existe une connexion, la connexion peut être gérée par les connexions avec l’autorisation **ALTER ANY login** ou l’autorisation **ALTER** sur cette connexion. Une connexion peut modifier le mot de passe et la base de données par défaut pour sa propre connexion.  
  
```sql 
CREATE LOGIN KimAbercrombie   
WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
GO  
  
GRANT ALTER ANY LOGIN TO KimAbercrombie;  
```  
  
### <a name="grant-permissions-to-manage-login-sessions"></a>Accorder des autorisations pour gérer les sessions de connexion  
Pour pouvoir afficher toutes les sessions sur le serveur, vous devez disposer de l’autorisation **View Server State** . La possibilité de mettre fin aux sessions d’autres connexions requiert l’autorisation **ALTER ANY Connection** . L’exemple suivant utilise la `KimAbercrombie` connexion créée précédemment.  
  
```sql  
-- Grant permissions to view sessions and queries  
GRANT VIEW SERVER STATE TO KimAbercrombie;  
  
-- Grant permission to end sessions  
GRANT ALTER ANY CONNECTION TO KimAbercrombie;  
```  
  
### <a name="grant-permission-to-manage-database-users"></a>Accorder l’autorisation de gérer les utilisateurs de base de données  
La création et la suppression d’utilisateurs de base de données requièrent l’autorisation **ALTER ANY User** . La gestion des utilisateurs existants requiert l’autorisation **ALTER ANY User** ou l’autorisation **ALTER** sur cet utilisateur. L’exemple suivant utilise la `KimAbercrombie` connexion créée précédemment.  
  
```sql  
-- Create a user  
USE AdventureWorksPDW2012;  
GO  
CREATE USER KimAbercrombie;  
  
-- Grant permissions to create and drop users   
GRANT ALTER ANY USER TO KimAbercrombie;  
```  
  
### <a name="grant-permisson-to-manage-database-roles"></a>Accorder à autorisations la gestion des rôles de base de données  
Pour créer et supprimer des rôles de base de données définis par l’utilisateur, vous devez disposer de l’autorisation **ALTER ANY Role** . L’exemple suivant utilise la `KimAbercrombie` connexion et l’utilisation créées précédemment.  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
-- Grant permissions to create and drop roles  
GRANT ALTER ANY ROLE TO KimAbercrombie;  
```  
  
### <a name="login-user-and-role-permission-charts"></a>Graphiques d’autorisation de connexion, d’utilisateur et de rôle  
Les graphiques suivants peuvent prêter à confusion, mais ils montrent comment les autorisations de levier plus élevées (telles que le contrôle) incluent des autorisations plus granulaires qui peuvent être accordées séparément (par exemple, ALTER). Il est recommandé de toujours accorder le moins d’autorisations à un utilisateur pour effectuer les tâches nécessaires. Pour ce faire, accordez des autorisations plus spécifiques, au lieu des autorisations de niveau supérieur.  
  
**Autorisations de connexion :**  
  
![Autorisations de connexion de sécurité APS](./media/grant-permissions/APS_security_login_perms.png "APS_security_login_perms")  
  
**Autorisations utilisateur :**  
  
![Autorisations utilisateur de sécurité APS](./media/grant-permissions/APS_security_user_perms.png "APS_security_user_perms")  
  
**Autorisations de rôle :**  
  
![Autorisations de rôle de sécurité APS](./media/grant-permissions/APS_security_role_perms.png "APS_security_role_perms")  
  
<!-- MISSING LINKS
For a list of all permissions, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  
  
-->

## <a name="grant-permissions-to-monitor-the-appliance"></a>Accorder des autorisations pour surveiller l’appliance
L’appliance SQL Server PDW peut être surveillée à l’aide de la console d’administration ou des vues du système SQL Server PDW. Les connexions requièrent l’autorisation niveau serveur **afficher l’état du serveur** pour surveiller l’appliance. Les connexions requièrent l’autorisation **ALTER ANY Connection** pour mettre fin aux connexions à l’aide de la console d’administration ou de la commande **Kill** . Pour plus d’informations sur les autorisations requises pour utiliser la console d’administration, consultez [accorder des autorisations pour utiliser la console d’administration &#40;SQL Server PDW&#41;](#grant-permissions-to-use-the-admin-console).  
  
### <a name="PermsAdminConsole"></a>Accorder l’autorisation de surveiller l’appliance à l’aide des vues système  
Les instructions SQL suivantes créent une connexion nommée `monitor_login` et accordent l’autorisation **View Server State** à `monitor_login` la connexion.  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_login WITH PASSWORD='Password4321';  
GRANT VIEW SERVER STATE TO monitor_login;  
GO  
```  
  
### <a name="grant-permission-to-monitor-the-appliance-by-using-system-views-and-to-terminate-connections"></a>Accorder l’autorisation de surveiller l’appliance à l’aide des vues système et de mettre fin aux connexions  
Les instructions SQL suivantes créent une connexion nommée `monitor_and_terminate_login` et accordent les autorisations **View Server State** et **ALTER ANY Connection** à `monitor_and_terminate_login` la connexion.  
  
```sql  
USE master;  
GO  
CREATE LOGIN monitor_and_terminate_login WITH PASSWORD='Password1234';   
GRANT VIEW SERVER STATE TO monitor_and_terminate_login;   
GRANT ALTER ANY CONNECTION TO monitor_and_terminate_login;  
GO  
```  
  
Pour créer des connexions d’administrateur, consultez [rôles serveur fixes](pdw-permissions.md#fixed-server-roles).  
  
## <a name="see-also"></a>Voir aussi
[CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md)  
[CRÉER UN UTILISATEUR](../t-sql/statements/create-user-transact-sql.md)  
[CREATE ROLE](../t-sql/statements/create-role-transact-sql.md)  
[Load](load-overview.md)  
