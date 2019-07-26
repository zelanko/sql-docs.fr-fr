---
title: Configuration du pare-feu
description: Comment configurer le pare-feu pour les connexions sortantes à partir de SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 754e243f45965801b9295d2b40a920d52bd2c95c
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469853"
---
# <a name="firewall-configuration-for-sql-server-machine-learning-services"></a>Configuration du pare-feu pour SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article répertorie les considérations relatives à la configuration du pare-feu que l’administrateur ou l’architecte doit garder à l’esprit lors de l’utilisation des services Machine Learning.

## <a name="default-firewall-rules"></a>Règles de pare-feu par défaut

Par défaut, le programme d’installation de SQL Server désactive les connexions sortantes en créant des règles de pare-feu.

Dans SQL Server 2016 et 2017, ces règles sont basées sur les comptes d’utilisateurs locaux, où le programme d’installation a créé une règle de trafic sortant pour **SQLRUserGroup** qui a refusé l’accès réseau à ses membres (chaque compte de travail était répertorié comme un principe local soumis à la règle. Pour plus d’informations sur SQLRUserGroup, consultez [vue d’ensemble de la sécurité pour l’infrastructure d’extensibilité dans SQL Server machine learning services](../../advanced-analytics/concepts/security.md#sqlrusergroup).

Dans SQL Server 2019, dans le cadre de la migration vers AppContainers, il existe de nouvelles règles de pare-feu basées sur les SID AppContainer: une pour chacune des 20 AppContainers créés par le programme d’installation de SQL Server. Les conventions d’affectation de noms pour le nom de règle de pare-feu sont **accès réseau de blocage pour AppContainer-00 dans SQL Server instance MSSQLSERVER**, où 00 est le numéro de l’appcontainer (00-20 par défaut) et MSSQLSERVER est le nom de l’instance de SQL Server.

> [!Note]
> Si des appels réseau sont requis, vous pouvez désactiver les règles de trafic sortant dans le pare-feu Windows.

## <a name="restrict-network-access"></a>Restreindre l’accès réseau

Dans une installation par défaut, une règle de pare-feu Windows est utilisée pour bloquer tout accès réseau sortant des processus d’exécution externes. Des règles de pare-feu doivent être créées pour empêcher les processus d’exécution externes de télécharger des packages ou d’effectuer d’autres appels réseau potentiellement malveillants.

Si vous utilisez un autre programme de pare-feu, vous pouvez également créer des règles pour bloquer les connexions réseau sortantes pour les runtimes externes, en définissant des règles pour les comptes d’utilisateurs locaux ou pour le groupe représenté par le pool de comptes d’utilisateurs.

Nous vous recommandons vivement d’activer le pare-feu Windows (ou un autre pare-feu de votre choix) pour empêcher l’accès réseau non restreint par les runtimes R ou python.

## <a name="next-steps"></a>Étapes suivantes

[Configurer le pare-feu Windows pour les connexions entrantes](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)