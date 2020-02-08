---
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
ms.openlocfilehash: d0a522d6deb01169189d6f5faaf7ba2f189d1522
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "73595504"
---
# <a name="query-columns-using-always-encrypted-with-secure-enclaves"></a>Interroger des colonnes en utilisant Always Encrypted avec enclaves sécurisées
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

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

