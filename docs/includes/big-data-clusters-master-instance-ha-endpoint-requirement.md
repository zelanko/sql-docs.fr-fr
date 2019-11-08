---
ms.openlocfilehash: 497a564a10a3d35b33f47222fce8f89fe36bd15e
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73530920"
---
Pour certaines opérations, comme notamment la configuration des paramètres de serveur (au niveau de l’instance) ou l’ajout manuel d’une base de données à un groupe de disponibilité, une connexion à l’instance SQL Server peut s’avérer nécessaire. Les opérations comme `sp_configure`, `RESTORE DATABASE` ou n’importe quelle commande DDL dans une base de données appartenant à un groupe de disponibilité nécessitent une connexion à l’instance SQL Server. Par défaut, un cluster Big Data ne comporte pas de point de terminaison permettant une connexion à l’instance. Vous devez exposer ce point de terminaison manuellement.

Pour obtenir des instructions, consultez [Se connecter aux bases de données sur le réplica principal](../big-data-cluster/deployment-high-availability.md#instance-connect).