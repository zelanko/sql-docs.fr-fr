---
title: "Configurer une base de données miroir chiffrée | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cryptography [SQL Server], database mirroring
- encryption [SQL Server], database mirroring
- database master key [SQL Server], database mirroring
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 7329a575-be29-46e0-abc6-1344db37920c
caps.latest.revision: 24
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 7e54d3e8e72533be42bbfa3490c86293d7f0d0c6
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="set-up-an-encrypted-mirror-database"></a>Configurer une base de données miroir chiffrée
  Pour activer le déchiffrement automatique de la clé principale d'une base de données miroir, vous devez fournir le mot de passe utilisé pour chiffrer la clé principale à l'instance de serveur miroir. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les versions ultérieures incluent des mécanismes de transfert du mot de passe. Utilisez **sp_control_dbmasterkey_password** pour créer des informations d’identification destinées à la clé principale de la base de données avant de démarrer la mise en miroir de celle-ci. Vous devez répéter cette procédure pour chaque base de données qui sera mise en miroir. Pour plus d’informations, consultez [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md).  
  
> [!CAUTION]  
>  N’activez pas le déchiffrement avec basculement d’une base de données qui doit rester inaccessible à l’administrateur système ( **sa** ) et à d’autres principaux de serveur hautement privilégiés. Vous pouvez configurer une base de données de sorte que la hiérarchie de ses clés ne puisse pas être déchiffrée par la clé principale du service. Cette option est prise en charge comme défense renforcée des bases de données contenant des informations qui ne doivent pas être accessibles à l’administrateur système ( **sa** ) ou à d’autres principaux de serveur hautement privilégiés. L’activation du déchiffrement avec basculement de cette base de données supprime cette défense renforcée, en permettant à l’administrateur système ( **sa** ) et à d’autres principaux de serveur hautement privilégiés de déchiffrer la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md)   
 [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Configuration de la mise en miroir d’une base de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md)  
  
  
