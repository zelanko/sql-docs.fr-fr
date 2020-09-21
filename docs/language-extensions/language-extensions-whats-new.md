---
title: Nouveautés des extensions de langage SQL Server
titleSuffix: ''
description: Découvrez les nouveautés des extensions de langage SQL Server qui développent, étendent et améliorent l’intégration entre les langages externes et la plateforme de données.
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4a38bba48d9accd16a3e8ca68bd3136c3419e5ad
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88173512"
---
# <a name="whats-new-in-sql-server-language-extensions"></a>Nouveautés des extensions de langage SQL Server
[!INCLUDE [SQL Server 2019 and later](../includes/applies-to-version/sqlserver2019.md)]

Des fonctionnalités propres aux [extensions de langage](language-extensions-overview.md) sont ajoutées à chaque version de SQL Server, car nous continuons à développer, étendre et approfondir l’intégration entre les langages externes et la plateforme de données. 

## <a name="new-in-sql-server-2019"></a>Nouveautés de SQL Server 2019 

Cette version ajoute la prise en charge des extensions de langage dans SQL Server. Pour plus d’informations sur toutes les fonctionnalités de cette version, consultez [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md) et [Notes de publication pour SQL Server 2019](../sql-server/sql-server-ver15-release-notes.md).

- Le runtime Java par défaut sur Windows et Linux est Open Zulu JRE. Il est fourni lors de l’installation des extensions de langage SQL Server [sur Windows](install/install-sql-server-language-extensions-on-windows.md) et [sur Linux](../linux/sql-server-linux-setup-language-extensions.md).
- [Types de données Java](how-to/java-to-sql-data-types.md) pris en charge.
- [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md) pour l’inscription d’un langage externe (par exemple, Java) auprès de SQL Server.
- [Kit SDK d’extensibilité Microsoft pour Java](how-to/extensibility-sdk-java-sql-server.md).
- Sur Windows et Linux, le code Java est accessible dans une bibliothèque externe à l’aide de l’instruction [CREATE EXTERNAL LIBRARY (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md). En savoir plus : [Guide pratique pour appeler du code Java dans SQL Server](how-to/call-java-from-sql.md)
- [Extension de langage Java](language-extensions-overview.md) sur Windows et Linux. Vous pouvez rendre le code Java compilé accessible à SQL Server en affectant des autorisations et en définissant le chemin. Les applications clientes ayant accès à SQL Server peuvent utiliser des données et exécuter votre code en appelant [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), la même procédure que celle utilisée pour l’intégration de R et de Python sur SQL Server Machine Learning Services.

## <a name="next-steps"></a>Étapes suivantes

+ Installer les [extensions de langage SQL Server sur Windows](install/install-sql-server-language-extensions-on-windows.md) ou [sur Linux](../linux/sql-server-linux-setup-language-extensions.md)
