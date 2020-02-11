---
title: Configurer une base de données miroir chiffrée | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- cryptography [SQL Server], database mirroring
- encryption [SQL Server], database mirroring
- database master key [SQL Server], database mirroring
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 7329a575-be29-46e0-abc6-1344db37920c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2a74adba783f1a52bdd404e11f0f747234c47f4b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62754382"
---
# <a name="set-up-an-encrypted-mirror-database"></a>Configurer une base de données miroir chiffrée

Pour activer le déchiffrement automatique de la clé principale d'une base de données miroir, vous devez fournir le mot de passe utilisé pour chiffrer la clé principale à l'instance de serveur miroir. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les versions ultérieures incluent des mécanismes de transfert du mot de passe. Utilisez **sp_control_dbmasterkey_password** pour créer des informations d’identification destinées à la clé principale de la base de données avant de démarrer la mise en miroir de celle-ci. Vous devez répéter cette procédure pour chaque base de données qui sera mise en miroir. Pour plus d’informations, consultez [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql).
  
> [!CAUTION]  
>  N’activez pas le déchiffrement avec basculement d’une base de données qui doit rester inaccessible à l’administrateur système ( **sa** ) et à d’autres principaux de serveur hautement privilégiés. Vous pouvez configurer une base de données de sorte que la hiérarchie de ses clés ne puisse pas être déchiffrée par la clé principale du service. Cette option est prise en charge comme défense renforcée des bases de données contenant des informations qui ne doivent pas être accessibles à l’administrateur système ( **sa** ) ou à d’autres principaux de serveur hautement privilégiés. L’activation du déchiffrement avec basculement de cette base de données supprime cette défense renforcée, en permettant à l’administrateur système ( **sa** ) et à d’autres principaux de serveur hautement privilégiés de déchiffrer la base de données.  


<!-- Note: We cannot append '?view=sql-server-2016' to these, even tho in theory we might want to. -->

## <a name="see-also"></a>Voir aussi

[sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql)

[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql)

[ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql)

[Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)

[Configuration de la mise en miroir d’une base de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)

