---
title: Limitations de sécurité pour SQL Server sur Linux
description: Cet article décrit les restrictions de SQL Server sur Linux.
author: VanMSFT
ms.author: vanto
ms.date: 09/12/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.openlocfilehash: f1820b54532a820a47babdaf79e28d1baa0f096b
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85895303"
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Limitations de sécurité pour SQL Server sur Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

SQL Server sur Linux présente actuellement les limitations suivantes :

* Une stratégie de mot de passe standard est fournie. MUST_CHANGE est la seule option que vous pouvez configurer. L’option CHECK_POLICY n’est pas prise en charge.
* La gestion de clés extensible n’est pas prise en charge. 
* L’utilisation de clés stockées dans Azure Key Vault n’est pas prise en charge.
* SQL Server génère son propre certificat auto-signé pour le chiffrement des connexions. SQL Server peut être configuré pour utiliser un certificat fourni par l’utilisateur pour TLS. 

Pour plus d’informations sur les fonctionnalités de sécurité disponibles dans SQL Server, consultez le [Security Center pour le moteur de base de données SQL Server et Azure SQL Database](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="next-steps"></a>Étapes suivantes

Pour les tâches de sécurité courantes, consultez [Prise en main des fonctionnalités de sécurité de SQL Server sur Linux](sql-server-linux-security-get-started.md). Pour obtenir un script permettant de modifier le numéro de port TCP, les répertoires SQL Server et de configurer les indicateurs de trace ou le classement, consultez [Configurer SQL Server sur Linux avec mssql-conf](sql-server-linux-configure-mssql-conf.md).
