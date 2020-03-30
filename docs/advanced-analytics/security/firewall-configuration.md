---
title: Configuration du pare-feu
description: Guide pratique pour configurer le pare-feu pour les connexions sortantes de SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c55f68a1134fee6477c52182ad66b8705e363296
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "68715597"
---
# <a name="firewall-configuration-for-sql-server-machine-learning-services"></a>Configuration du pare-feu pour SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article dresse la liste des éléments que l’administrateur ou l’architecte doit prendre en considération au moment de configurer le pare-feu quand les services Machine Learning sont utilisés.

## <a name="default-firewall-rules"></a>Règles de pare-feu par défaut

Par défaut, le programme d’installation SQL Server désactive les connexions sortantes en créant des règles de pare-feu.

Dans SQL Server 2016 et 2017, ces règles étaient basées sur les comptes d’utilisateurs locaux : le programme d’installation créait une règle de trafic sortant pour **SQLRUserGroup** qui refusait l’accès réseau à ses membres (chaque compte de travail est listé comme un principe local soumis à la règle). Pour plus d’informations sur SQLRUserGroup, consultez [Vue d’ensemble de la sécurité de l’infrastructure d’extensibilité dans SQL Server Machine Learning Services](../../advanced-analytics/concepts/security.md#sqlrusergroup).

Dans SQL Server 2019, dans le cadre de la migration vers les éléments AppContainers, il existe de nouvelles règles de pare-feu basées sur les SID AppContainer : une pour chacun des 20 éléments AppContainers créés par le programme d’installation SQL Server. Les conventions d’affectation de noms pour le nom de la règle de pare-feu sont **Bloquer l’accès réseau pour AppContainer-00 dans l’instance SQL Server MSSQLSERVER**, où 00 est le numéro de l’élément AppContainer (00-20 par défaut) et MSSQLSERVER est le nom de l’instance SQL Server.

> [!Note]
> Si des appels réseau sont nécessaires, vous pouvez désactiver les règles de trafic sortant dans le pare-feu Windows.

## <a name="restrict-network-access"></a>Restreindre l’accès réseau

Dans une installation par défaut, une règle de pare-feu Windows est utilisée pour bloquer tout accès réseau sortant des processus d’exécution externes. Des règles de pare-feu doivent être créées pour éviter que les processus d’exécution externe téléchargent des packages ou passent d’autres appels réseau potentiellement malveillants.

Si vous utilisez un autre programme de pare-feu, vous pouvez aussi créer des règles pour bloquer les connexions réseau sortantes pour les runtimes externes en définissant des règles pour les comptes d’utilisateurs locaux ou pour le groupe représenté par le pool de comptes d’utilisateurs.

Nous vous recommandons vivement d’activer le pare-feu Windows (ou le pare-feu de votre choix) pour empêcher tout accès réseau non restreint par les runtimes R ou Python.

## <a name="next-steps"></a>Étapes suivantes

[Configurer le pare-feu Windows pour les connexions entrantes](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)