---
title: Configurer le chiffrement de colonne sur place en utilisant Always Encrypted avec enclaves sécurisées | Microsoft Docs
ms.custom: ''
ms.date: 10/10/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: d887e428773e6901544422edcb6960e6e9ae0580
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "73595514"
---
# <a name="configure-column-encryption-in-place-using-always-encrypted-with-secure-enclaves"></a>Configurer le chiffrement de colonne sur place en utilisant Always Encrypted avec enclaves sécurisées 
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

[Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves.md) prend en charge les opérations de chiffrement sur les colonnes de base de données sur place, à l’intérieur d’une enclave sécurisée dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le chiffrement sur place élimine la nécessité de déplacer les données pour ces opérations en dehors de la base de données, ce qui rend les opérations de chiffrement plus rapides et plus fiables. 

> [!NOTE]
> En dépit des avantages en matière de performances du chiffrement sur place, les opérations de chiffrement sur des grandes tables peuvent prendre beaucoup de temps et consommer des ressources importantes, ce qui peut affecter et dégrader les performances et la disponibilité de vos applications.

Le chiffrement sur place permet aussi de déclencher des opérations de chiffrement avec l’instruction [ALTER TABLE ALTER COLUMN (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md), ce qui n’est pas possible sans une enclave.

## <a name="prerequisites"></a>Conditions préalables requises
Les opérations de chiffrement prises en charge et les exigences pour la ou les clés de chiffrement de colonne utilisées pour les opérations sont les suivantes :
- Chiffrement d’une colonne de texte en clair. La clé de chiffrement de colonne utilisée pour chiffrer la colonne doit être activée pour les enclaves.
- Rechiffrement d’une colonne chiffrée avec un nouveau type de chiffrement et/ou une nouvelle clé de chiffrement de colonne. La clé de chiffrement de colonne actuelle et la nouvelle clé de chiffrement de colonne (si elle est différente de la clé actuelle) doivent être activées pour les enclaves.
- Déchiffrement d’une colonne chiffrée : la clé de chiffrement de colonne protégeant la colonne doit être activée pour les enclaves.

Pour plus d’informations sur la façon de garantir que vos clés de chiffrement de colonne sont activées pour les enclaves, consultez [Gérer les clés pour Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-manage-keys.md).

Le chiffrement sur place nécessite également une instance SQL Server qui a une enclave sécurisée correctement initialisée. Consultez [Configurer le type d’enclave pour l’option de configuration de serveur Always Encrypted](../../../database-engine/configure-windows/configure-column-encryption-enclave-type.md).

Un utilisateur ou une application déclenchant des opérations de chiffrement doit avoir les autorisations nécessaires pour apporter des modifications de schéma à la table contenant les colonnes impactées et pour accéder aux clés principales de colonne impliquées dans les opérations, de même que les métadonnées de clé pertinentes dans la base de données.

Vous pouvez déclencher le chiffrement sur place seulement avec [ALTER TABLE ALTER COLUMN (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) depuis SQL Server Management Studio ou depuis votre application personnalisée. Consultez [Configurer le chiffrement de colonne sur place avec Transact-SQL](always-encrypted-enclaves-configure-encryption-tsql.md).

> [!NOTE]
> Actuellement, l’[Assistant Always Encrypted](always-encrypted-wizard.md) et l’applet de commande [Set-SqlColumnEncryption](https://docs.microsoft.com/powershell/module/sqlserver/set-sqlcolumnencryption) ne prennent pas en charge le chiffrement sur place et téléchargent toujours les données pour les opérations de chiffrement, même si votre configuration répond aux exigences ci-dessus. 

## <a name="next-steps"></a>Étapes suivantes
- [Configurer le chiffrement de colonne sur place avec Transact-SQL](always-encrypted-enclaves-configure-encryption-tsql.md)
- [Créer et utiliser des index sur des colonnes en utilisant Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-create-use-indexes.md)
- [Développer des applications en utilisant Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-client-development.md)
