---
title: sp_set_database_firewall_rule
titleSuffix: Azure SQL Database
ms.date: 08/04/2017
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sp_set_database_firewall_rule
- sp_set_database_firewall_rule_TSQL
- sys.sp_set_database_firewall_rule
- sys.sp_set_database_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_database_firewall_rule
- firewall_rules, setting database rules
ms.assetid: 8f0506b6-a4ac-4e4d-91db-8077c40cb17a
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.custom: seo-dt-2019
ms.openlocfilehash: dfe41ee68412414df24bc7f0bd583bbb0109b3db
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74055090"
---
# <a name="sp_set_database_firewall_rule-azure-sql-database"></a>sp_set_database_firewall_rule (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Crée ou met à jour les règles de pare-feu au niveau de la base de données pour votre [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Les règles de pare-feu de base de données peuvent être configurées pour la base de données **Master** et les bases de données utilisateur sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Les règles de pare-feu de base de données sont particulièrement utiles lors de l’utilisation des utilisateurs de base de données Pour plus d’informations, consultez [Utilisateurs de base de données autonome - Rendre votre base de données portable](../../relational-databases/security/contained-database-users-making-your-database-portable.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_set_database_firewall_rule [@name = ] [N]'name'  
, [@start_ip_address =] 'start_ip_address'  
, [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @name = ] [N]'name'` le nom utilisé pour décrire et distinguer le paramètre de pare-feu au niveau de la base de données. *Name* est de type **nvarchar (128)** sans valeur par défaut. L’identificateur Unicode `N` est facultatif pour les [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]. 
  
`[ @start_ip_address = ] 'start_ip_address'` l’adresse IP la plus basse dans la plage du paramètre de pare-feu au niveau de la base de données. Les adresses IP supérieures ou égales à celle-ci peuvent essayer de se connecter à l'instance [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L"adresse IP la plus basse possible est `0.0.0.0`. *start_ip_address* est de type **varchar (50)** sans valeur par défaut.  
  
`[ @end_ip_address = ] 'end_ip_address'` l’adresse IP la plus élevée dans la plage du paramètre de pare-feu au niveau de la base de données. Les adresses IP inférieures ou égales à celle-ci peuvent essayer de se connecter à l'instance [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L"adresse IP la plus élevée possible est `255.255.255.255`. *end_ip_address* est de type **varchar (50)** sans valeur par défaut.  
  
 Le tableau suivant montre les arguments et options pris en charge dans [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
> [!NOTE]  
>  Les tentatives de connexion Azure sont autorisées lorsque ce champ et le champ *start_ip_address* est égal à `0.0.0.0`.  
  
## <a name="remarks"></a>Notes  
 Les noms des paramètres de pare-feu au niveau base de données doivent être uniques. Si le nom du paramètre de pare-feu au niveau base de données spécifié pour la procédure stockée existe déjà dans le tableau des paramètres de pare-feu au niveau base de données, les adresses IP de début et de fin sont mises à jour. Sinon, un nouveau paramètre de pare-feu au niveau base de données est créé.  
  
 Lorsque vous ajoutez un paramètre de pare-feu au niveau de la base de données alors que les adresses IP de début et de fin sont égales à `0.0.0.0`, vous activez l’accès à votre base de données sur le serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] à partir de n’importe quelle ressource Azure. Spécifiez une valeur pour le paramètre de *nom* qui vous aidera à vous souvenir de la fonction du paramètre de pare-feu.  
  
## <a name="permissions"></a>Autorisations  
 Exige l’autorisation **CONTROL** sur la base de données.  
  
## <a name="examples"></a>Exemples  
 Le code suivant crée un paramètre de pare-feu au niveau de la base de données appelé `Allow Azure` qui permet d’accéder à votre base de données à partir d’Azure.  
  
```  
-- Enable Azure connections.  
EXECUTE sp_set_database_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 Le code suivant crée un paramètre de pare-feu au niveau base de données appelé `Example DB Setting 1` uniquement pour l'adresse IP `0.0.0.4`. Ensuite, la procédure stockée `sp_set_database firewall_rule` est à nouveau appelée pour mettre à jour l’adresse IP de fin à `0.0.0.6`, dans ce paramètre de pare-feu. Cela crée une plage qui permet aux adresses IP `0.0.0.4`, `0.0.0.5`et `0.0.0.6` d’accéder à la base de données.
  
```  
-- Create database-level firewall setting for only IP 0.0.0.4  
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.4';  
  
-- Update database-level firewall setting to create a range of allowed IP addresses
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.6';  
  
```  
  
## <a name="see-also"></a>Voir aussi  
   du [pare-feu Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)  
 [Procédure : configurer les paramètres de pare-feu (Azure SQL Database)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;Azure SQL Database&#41; ](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_delete_database_firewall_rule &#40;Azure SQL Database&#41; ](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)   
 [sys. database_firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  
