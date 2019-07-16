---
title: Configuration du pare-feu - SQL Server Machine Learning Services
description: Comment configurer le pare-feu pour les connexions sortantes à partir de SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: f62b42754b56ac07714eeade0d86e6c8ac582698
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962342"
---
# <a name="firewall-configuration-for-sql-server-machine-learning-services"></a>Configuration du pare-feu pour SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article répertorie les considérations sur les configurations de pare-feu qui l’administrateur ou un architecte devez garder à l’esprit lors de l’utilisation des services machine learning.

## <a name="default-firewall-rules"></a>Règles de pare-feu par défaut

Par défaut, le programme d’installation de SQL Server désactive les connexions sortantes en créant des règles de pare-feu.

Dans SQL Server 2016 et 2017, ces règles sont basées sur les comptes d’utilisateurs locaux, où le programme d’installation créé une règle sortante pour **SQLRUserGroup** qui refuse l’accès de réseau à ses membres (chaque compte de travail a été répertoriée comme un principe local soumis aux la règle. Pour plus d’informations sur SQLRUserGroup, consultez [vue d’ensemble de la sécurité pour l’infrastructure d’extensibilité dans SQL Server Machine Learning Services](../../advanced-analytics/concepts/security.md#sqlrusergroup).

Dans SQL Server 2019, dans le cadre du passage à AppContainers, voici les nouvelles règles de pare-feu en fonction des AppContainer SIDs : un pour chacune des 20 AppContainers créé par le programme d’installation de SQL Server. Conventions d’affectation de noms pour le nom de règle de pare-feu sont **bloquer l’accès réseau pour AppContainer-00 dans l’instance SQL Server MSSQLSERVER**où 00 est le nombre de l’AppContainer (00-20 par défaut) et MSSQLSERVER est le nom de l’instruction SQL Instance de serveur.

> [!Note]
> Si les appels réseau sont nécessaires, vous pouvez désactiver les règles de trafic sortant dans le pare-feu Windows.

## <a name="restrict-network-access"></a>Restreindre l’accès réseau

Dans une installation par défaut, une règle de pare-feu Windows est utilisée pour bloquer tout accès réseau sortant à partir de processus du runtime externe. Règles de pare-feu doivent être créées pour empêcher les processus externes runtime de télécharger des packages ou à partir d’autres appels de réseau qui pourraient être malveillant.

Si vous utilisez un autre programme de pare-feu, vous pouvez également créer des règles pour bloquer les connexions réseau sortantes pour les runtimes externes, en définissant des règles pour les comptes d’utilisateur local ou du groupe représenté par le pool de comptes d’utilisateur.

Nous recommandons vivement que vous activez le pare-feu de Windows (ou un autre pare-feu de votre choix) pour empêcher un accès illimité au réseau par les runtimes R ou Python.

## <a name="next-steps"></a>Étapes suivantes

[Configurer le pare-feu Windows pour les connexions entrantes](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)