---
description: Définir des options de chiffrement sur des serveurs cibles
title: Définir des options de chiffrement sur des serveurs cibles
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 164b825f2d896085d217e0bd7e87ac405511477c
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038222"
---
# <a name="set-encryption-options-on-target-servers"></a>Définir des options de chiffrement sur des serveurs cibles
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance), la plupart, mais pas toutes les fonctionnalités SQL Server Agent sont actuellement prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Managed Instance et SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Si vous ne pouvez pas utiliser de certificat pour les communications chiffrées TLS (Transport Layer Security), anciennement SSL (Secure Sockets Layer) entre des serveurs maîtres et l’ensemble ou une partie de vos serveurs cibles, mais que vous souhaitez chiffrer le canal entre ces serveurs, configurez le serveur cible de façon à utiliser le niveau de sécurité requis.  
  
Pour configurer le niveau de sécurité approprié requis pour un canal de communication spécifique serveur maître/serveur cible, affectez à la sous-clé de registre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\** \<*instance_name*> **\SQLServerAgent\MsxEncryptChannelOptions(REG_DWORD)** sur le serveur cible l’une des valeurs suivantes. La valeur de \<*instance_name*> est **MSSQL.** _n_. Par exemple, **MSSQL.1** ou **MSSQL.3**.  
  
|Valeur|Description|  
|---------|---------------|  
|**0**|Désactive le chiffrement entre ce serveur cible et le serveur maître. Ne choisissez cette option que lorsque le canal entre le serveur cible et le serveur maître est sécurisé par d'autres moyens.|  
|**1**|Active le chiffrement uniquement entre ce serveur cible et le serveur maître, mais aucune validation de certificat n'est requise.|  
|**2**|Active le chiffrement TLS et la validation de certificat complets entre ce serveur cible et le serveur maître. Il s’agit du paramètre par défaut. Sauf si vous avez une raison particulière de choisir une valeur différente, nous vous recommandons de ne pas le modifier.|  
  
Si **1** ou **2** est spécifié, le protocole TLS doit être activé sur les serveurs maîtres et cibles. Si **2** est spécifié, un certificat signé correctement doit également être présent sur le serveur maître.  
  
> [!CAUTION]  
> [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a> Voir aussi  
[Procédure : activer des connexions chiffrées dans le moteur de base de données (Gestionnaire de configuration SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
