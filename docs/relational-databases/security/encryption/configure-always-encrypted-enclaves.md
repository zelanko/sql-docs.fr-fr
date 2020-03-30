---
title: Configurer et utiliser Always Encrypted avec enclaves sécurisées | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 568944db62ca94048c45450500d3060daa957680
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "74317941"
---
# <a name="configure-and-use-always-encrypted-with-secure-enclaves"></a>Configurer et utiliser Always Encrypted avec enclaves sécurisées 

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[Always Encrypted avec enclaves sécurisés](always-encrypted-enclaves.md) étend la fonctionnalité [Always Encrypted](always-encrypted-database-engine.md) existante pour activer des fonctionnalités plus complexes sur les données sensibles tout en préservant la confidentialité des données. Cet article liste les tâches courantes de configuration et d’utilisation de la fonctionnalité.

Pour obtenir un tutoriel montrant comment rapidement prendre en main Always Encrypted avec enclaves sécurisées, consultez [Tutoriel : bien démarrer avec Always Encrypted avec enclaves sécurisées en utilisant SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md).

## <a name="set-up-your-environment-to-support-enclaves-and-attestation"></a>Configurer votre environnement pour prendre en charge les enclaves et l’attestation
Pour plus de détails, consultez les articles suivants :
- [Planifier l’attestation avec le Service Guardian hôte](./always-encrypted-enclaves-host-guardian-service-plan.md)
- [Déployer le Service Guardian hôte pour [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)]](./always-encrypted-enclaves-host-guardian-service-deploy.md)
- [Inscrire votre ordinateur auprès du Service Guardian hôte](./always-encrypted-enclaves-host-guardian-service-register.md)

## <a name="manage-keys-for-always-encrypted-with-secure-enclaves"></a>Gérer les clés pour Always Encrypted avec enclaves sécurisées
Consultez les articles suivants pour plus de détails :
- [Gérer des clés pour Always Encrypted avec enclaves sécurisées - vue d’ensemble](always-encrypted-enclaves-manage-keys.md)
- [Provisionner des clés activées pour les enclaves](always-encrypted-enclaves-provision-keys.md)
- [Permuter des clés activées pour les enclaves](always-encrypted-enclaves-rotate-keys.md)

## <a name="configure-columns-with-always-encrypted-with-secure-enclaves"></a>Configurer des colonnes à l’aide d’Always Encrypted avec enclaves sécurisées
Consultez les articles suivants pour plus de détails :
- [Configurer le chiffrement de colonne sur place à l’aide d’Always Encrypted avec enclaves sécurisées - vue d’ensemble](always-encrypted-enclaves-configure-encryption.md)
- [Configurer le chiffrement de colonne sur place avec Transact-SQL](always-encrypted-enclaves-configure-encryption-tsql.md)
- [Activer Always Encrypted avec enclaves sécurisées pour les colonnes chiffrées existantes](always-encrypted-enclaves-enable-for-encrypted-columns.md)

> [!NOTE]
> Pour obtenir un tutoriel pas à pas sur la manière de tester votre environnement de test et d’essayer la fonctionnalité Always Encrypted avec enclaves sécurisées dans SSMS, consultez [Tutoriel : bien démarrer avec Always Encrypted avec enclaves sécurisées en utilisant SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md).

## <a name="query-columns-using-always-encrypted-with-secure-enclaves"></a>Interroger des colonnes en utilisant Always Encrypted avec enclaves sécurisées
Consultez les articles suivants pour plus de détails :
- [Interroger des colonnes à l’aide d’Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-query-columns.md)
- [Interroger des colonnes en utilisant Always Encrypted avec enclaves sécurisées avec SSMS](always-encrypted-enclaves-query-columns-ssms.md)

## <a name="create-and-use-indexes-on-enclave-enabled-columns"></a>Créer et utiliser des index sur des colonnes avec enclave
Consultez les articles suivants pour plus de détails :
- [Créer et utiliser des index sur des colonnes à l’aide d’Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-create-use-indexes.md)

## <a name="develop-applications-using-always-encrypted-with-secure-enclaves"></a>Développer des applications avec Always Encrypted avec enclaves sécurisées
Consultez les articles suivants pour plus de détails :
- [Développer des applications en utilisant Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-client-development.md)
