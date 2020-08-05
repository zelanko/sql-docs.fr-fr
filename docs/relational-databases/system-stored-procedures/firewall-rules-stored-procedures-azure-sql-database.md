---
title: Procédures stockées pour les règles de pare-feu
titleSuffix: Azure SQL Database
ms.date: 07/28/2016
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- firewall rules stored procedures
- firewall_rules, setting
- firewall_rules, Azure SQL Database
- firewall systems, Azure SQL Database
ms.assetid: 3d4c2585-00de-46b5-8eee-0efb71cb3aea
author: VanMSFT
ms.author: vanto
ms.custom: seo-dt-2019
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: bace837ef11fc106632b84fe01ed5c8bc1448ffa
ms.sourcegitcommit: bc10ec0be5ddfc5f0bc220a9ac36c77dd6b80f1d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87544346"
---
# <a name="firewall-rules-stored-procedures-azure-sql-database"></a>Procédures stockées de règles de pare-feu (Azure SQL Database)
[!INCLUDE [asdb-asa](../../includes/applies-to-version/asdb-asa.md)]

  Cette section contient les procédures stockées suivantes qui définissent ou suppriment les règles de pare-feu. [!INCLUDE[tsql_md](../../includes/tsql-md.md)]les règles de pare-feu peuvent être utilisées avec [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] et [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] . Pour plus d’informations, consultez [configurer des règles de pare-feu Azure SQL Database-Overview](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/).

:::row:::
    :::column:::
        [sp_set_firewall_rule &#40;Base de données Azure SQL&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)
    :::column-end:::
    :::column:::
        [sp_delete_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md)
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        [sp_set_database_firewall_rule &#40;Base de données Azure SQL&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)
    :::column-end:::
    :::column:::
        [sp_delete_database_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)
    :::column-end:::
:::row-end:::

&nbsp;
  
Pour [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] , utilisez les règles de pare-feu Windows. Pour plus d’informations, consultez [Configurer un pare-feu Windows pour accéder au moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md).   
  


