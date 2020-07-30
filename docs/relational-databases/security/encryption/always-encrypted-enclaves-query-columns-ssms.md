---
title: Interroger des colonnes en utilisant Always Encrypted avec enclaves sécurisées avec SSMS | Microsoft Docs
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
ms.openlocfilehash: 50f44a01383a307ac462c0f4fcb3e9e3f67d66fa
ms.sourcegitcommit: 620a868e623134ad6ced6728ce9d03d7d0038fe0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87411505"
---
# <a name="query-columns-using-always-encrypted-with-secure-enclaves-with-ssms"></a>Interroger des colonnes en utilisant Always Encrypted avec enclaves sécurisées avec SSMS
[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

Cet article explique comment utiliser SQL Server Management Studio pour émettre des requêtes qui utilisent une enclave sécurisée côté serveur pour [Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves.md), notamment :
- Les requêtes qui déclenchent des opérations de chiffrement sur place.
- Les requêtes déclenchant des calculs complexes, notamment des comparaisons de plages ou des opérations de correspondance de modèle sur les colonnes chiffrées avec des clés activées pour les enclaves.
- Les requêtes qui créent ou mettent à jour des index sur des colonnes chiffrées avec un chiffrement aléatoire et des clés activées pour les enclaves.  

Pour utiliser SSMS afin d’exécuter des requêtes sur des colonnes chiffrées avec une enclave sécurisée, suivez les instructions de [Interroger des colonnes en utilisant Always Encrypted avec SQL Server Management Studio](always-encrypted-query-columns-ssms.md). Voici quelques éléments spécifiques aux enclaves que vous devez prendre en compte :

- Vous avez besoin de SSMS version 18.3 ou ultérieure.
- Veillez à exécuter les requêtes dans une fenêtre de requête utilisant une enclave sécurisée à partir d’une connexion pour laquelle Always Encrypted et les calculs d’enclave sont activés. Pour obtenir des instructions détaillées, consultez [Tutoriel : Bien démarrer avec Always Encrypted avec enclaves sécurisées en utilisant SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md) et [Activation et désactivation d’Always Encrypted pour une connexion de base de données ](always-encrypted-query-columns-ssms.md#en-dis).

## <a name="next-steps"></a>Étapes suivantes
- [Développer des applications en utilisant Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-client-development.md)

## <a name="see-also"></a>Voir aussi  
- [Tutoriel : Bien démarrer avec Always Encrypted avec enclaves sécurisées en utilisant SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)
- [Configurer le chiffrement de colonne sur place avec Transact-SQL](always-encrypted-enclaves-configure-encryption-tsql.md)
- [Créer et utiliser des index sur des colonnes à l’aide d’Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-create-use-indexes.md)

