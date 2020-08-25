---
title: Limitations de sécurité pour SQL Server sur Linux
description: En savoir plus sur les restrictions de SQL Server sur Linux, notamment la façon dont l’utilisation des clés stockées dans Azure Key Vault et la gestion de clés extensible ne sont pas prises en charge.
author: VanMSFT
ms.author: vanto
ms.date: 09/12/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.openlocfilehash: 611afe6c02e979c7c9672d7d94f84844b8932cf6
ms.sourcegitcommit: 3ea082c778f6771b17d90fb597680ed334d3e0ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88088795"
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
