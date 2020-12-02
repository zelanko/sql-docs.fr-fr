---
description: Interroger des colonnes en utilisant Always Encrypted avec enclaves sécurisées
title: Interroger des colonnes en utilisant Always Encrypted avec enclaves sécurisées | Microsoft Docs
ms.custom: ''
ms.date: 10/31/2019
ms.reviewer: vanto
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 8daabf320e0f736bcfabc5addb8508320b10bb8f
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "88482222"
---
# <a name="query-columns-using-always-encrypted-with-secure-enclaves"></a>Interroger des colonnes en utilisant Always Encrypted avec enclaves sécurisées
[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

Cet article contient des considérations générales relatives à l’exécution de requêtes sur des colonnes chiffrées en utilisant une enclave sécurisée côté serveur pour [Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves.md). 

Les types de requêtes suivants impliquent l’utilisation d’une enclave sécurisée :
- Les requêtes qui déclenchent des opérations de chiffrement sur place en utilisant des clés activées pour les enclaves. Consultez [Configurer le chiffrement de colonne sur place avec Transact-SQL](always-encrypted-enclaves-configure-encryption-tsql.md).
- Les *requêtes avancées* : des comparaisons de plages ou des opérations de correspondance de modèle sur des colonnes chiffrées, avec un chiffrement aléatoire et des clés activées pour les enclaves.
- Les requêtes qui créent ou mettent à jour des index sur des colonnes chiffrées avec un chiffrement aléatoire et des clés activées pour les enclaves. Pour plus d’informations, consultez [Créer et utiliser des index sur des colonnes à l’aide d’Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-create-use-indexes.md).

> [!NOTE]
> Les requêtes et les index avancés sont pris en charge seulement sur les colonnes activées pour les enclaves (colonnes chiffrées avec des clés de chiffrement de colonne activées pour les enclaves) qui utilisent un chiffrement aléatoire. Le chiffrement déterministe ne prend pas en charge les requêtes ou les index avancés.

> [!NOTE]
> Les requêtes avancées sur les colonnes de chaînes de caractères chiffrées nécessitent des colonnes utilisant des classements avec un ordre de tri binary2 (classements BIN2). 


## <a name="next-steps"></a>Étapes suivantes
- [Interroger des colonnes en utilisant Always Encrypted avec enclaves sécurisées avec SSMS](always-encrypted-enclaves-query-columns-ssms.md)

## <a name="see-also"></a>Voir aussi
- [Tutoriel : Bien démarrer avec Always Encrypted avec enclaves sécurisées en utilisant SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)

