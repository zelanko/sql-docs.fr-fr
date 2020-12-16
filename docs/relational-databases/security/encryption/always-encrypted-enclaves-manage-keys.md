---
description: Gérer les clés pour Always Encrypted avec enclaves sécurisées
title: Gérer les clés pour Always Encrypted avec enclaves sécurisées | Microsoft Docs
ms.custom: ''
ms.date: 10/30/2019
ms.reviewer: vanto
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15'
ms.openlocfilehash: 0c1f00a5b1e69bdb8f51f848210e8e90b0ae6a4b
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97477630"
---
# <a name="manage-keys-for-always-encrypted-with-secure-enclaves"></a>Gérer les clés pour Always Encrypted avec enclaves sécurisées
[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

[Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves.md) étend la gestion des clés pour [Always Encrypted](always-encrypted-database-engine.md) en introduisant des clés activées pour les enclaves : 

- **Clé principale de colonne activée pour les enclaves** : une clé principale de colonne qui est créée avec la propriété `ENCLAVE_COMPUTATIONS` spécifiée dans l’objet de métadonnées de la clé principale de colonne à l’intérieur de la base de données. 
- **Clé de chiffrement de colonne prenant en charge l’enclave** : clé de chiffrement de colonne qui est chiffrée avec une clé principale de colonne prenant en charge l’enclave. Seules les clés de chiffrement de colonne activées pour les enclaves peuvent être utilisées pour les calculs à l’intérieur d’une enclave sécurisée côté serveur. 

Les instructions générales et les processus de [gestion des clés Always Encrypted](overview-of-key-management-for-always-encrypted.md) s’appliquent à la gestion des clés activées pour les enclaves. 

## <a name="managing-keys"></a>Gestion des clés

Les articles suivants traitent des aspects spécifiques à la gestion des clés activées pour les enclaves.

- [Provisionner des clés activées pour les enclaves](always-encrypted-enclaves-provision-keys.md)
- [Permuter des clés activées pour les enclaves](always-encrypted-enclaves-rotate-keys.md)

## <a name="next-steps"></a>Étapes suivantes
- [Provisionner des clés activées pour les enclaves](always-encrypted-enclaves-provision-keys.md)

## <a name="see-also"></a>Voir aussi  
- [Vue d’ensemble de la gestion des clés pour Always Encrypted](overview-of-key-management-for-always-encrypted.md)
- [CREATE COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-column-master-key-transact-sql.md)
