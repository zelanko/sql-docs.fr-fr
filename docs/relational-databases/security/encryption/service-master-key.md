---
title: "Clé principale du service | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service master key [SQL Server]
- service master key [SQL Server], about service master key
ms.assetid: 85f2095d-2590-4f59-8a29-7e100edd02bb
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fd1adfac8a64c19577374d309390bead0cb12de9
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="service-master-key"></a>Clé principale du service
  La clé principale du service représente la racine de la hiérarchie de chiffrement de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Elle est générée automatiquement la première fois qu'il est nécessaire de chiffrer une autre clé. Par défaut, la clé principale du service est chiffrée à l'aide de l'API de protection des données (DPAPI) Windows et de la clé de la machine locale. La clé principale du service ne peut être ouverte que par le compte de service Windows sous lequel elle a été créée ou par un principal ayant accès au nom du compte de service et à son mot de passe.  
  
 La régénération ou la restauration de la clé principale du service implique le déchiffrement puis le chiffrement de la hiérarchie complète de chiffrement. À moins que l'intégrité de la clé n'ait été compromise, cette opération nécessitant de nombreuses ressources doit être planifiée pendant une période où la demande est faible.  
  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] utilise l’algorithme de chiffrement AES pour protéger la clé principale du service (SMK) et la clé principale de base de données (DMK). AES est un algorithme de chiffrement plus récent que 3DES, qui était utilisé dans les versions antérieures. Au terme de la mise à niveau d'une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)] vers [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les clés SMK et DMK doivent être régénérées pour mettre à niveau les clés principales vers AES. Pour plus d’informations sur la régénération de la clé SMK, consultez [ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-service-master-key-transact-sql.md) et [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-master-key-transact-sql.md).  
  
## <a name="best-practice"></a>Meilleure pratique  
 Sauvegardez la clé principale du service et stockez la copie sauvegardée en un lieu sûr, hors site.  
  
## <a name="related-tasks"></a>Tâches associées  
 [BACKUP SERVICE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/backup-service-master-key-transact-sql.md)  
  
 [RESTORE SERVICE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/restore-service-master-key-transact-sql.md)  
  
 [ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-service-master-key-transact-sql.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchie de chiffrement](../../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

