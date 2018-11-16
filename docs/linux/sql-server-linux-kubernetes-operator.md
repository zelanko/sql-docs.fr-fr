---
title: SQL Server Always On groupe Kubernetes opérateur globales exigences de disponibilité
description: Cet article présente les différents paramètres pour les SQL Server Kubernetes Always On groupe opérateur globales exigences de disponibilité
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: cd3cf1cd36866010843347d5c7a05a8cd39c20ef
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51660598"
---
# <a name="sql-server-always-on-availability-group-kubernetes-operator-parameters"></a>SQL Server Always On paramètres d’opérateur disponibilité groupe Kubernetes

Un groupe de disponibilité Always On sur Kubernetes nécessite un opérateur. Un manifeste décrit l’opérateur. Le manifeste est un `.yaml` fichier. Voir un exemple de la spécification dans [groupes de disponibilité Always On pour les conteneurs de SQL Server](sql-server-ag-kubernetes.md).

Cet article explique les variables d’environnement globales de l’opérateur.

## <a name="example"></a>Exemple

L’exemple suivant décrit un déploiement pour le `mssql-operator`.

## <a name="global-environment-variables"></a>Variables d’environnement globales

* `MSSQL_K8S_POD_NAMESPACE` 
  * Requis
  * **Description**: espace de noms Kubernetes le de l’opérateur.

* `MSSQL_K8S_SQL_WRITE_LEASE_PERIOD_SECONDS`
  * Ce paramètre est facultatif
  * **Description**: la durée de l’écriture-bail de sql server. Permet de conserver le serveur sql server accessible en écriture et empêcher les scénarios de « split brain ». Réplicas secondaires attendez que ce nombre de secondes après avoir sélectionné un nouveau responsable.

* `MSSQL_K8S_MONITOR_PERIOD_SECONDS`
  * Ce paramètre est facultatif
  * **Description**: la période pour surveiller l’état du groupe de disponibilité. Détermine la vitesse à laquelle les réplicas sont ajoutés et supprimés. Doit être inférieur à `MSSQL_K8S_SQL_WRITE_LEASE_PERIOD_SECONDS`.
  * **Par défaut**: 1

* `MSSQL_K8S_LEASE_DURATION_SECONDS`
  * Ce paramètre est facultatif
  * **Description**: durée de bail de responsable de groupe de disponibilité. Détermine la durée pendant laquelle les réplicas secondaires attendre avant de l’élection de nouveau si le réplica principal est arrêté anormalement. Cela est différent de bail d’écriture de SQL Server. 
  * **Par défaut**: 10
  
  >[!NOTE]
  >Autres paramètres calculée automatiquement en fonction de `MSSQL_K8S_LEASE_DURATION_SECONDS`.

* `MSSQL_K8S_RENEW_DEADLINE_SECONDS`
  * Ce paramètre est facultatif
  * **Description**: durée pendant laquelle le réplica principal agissant retente l’actualisation leadership avant d’abandonner. Doit être inférieur à `MSSQL_K8S_LEASE_DURATION_SECONDS`.
  * **Par défaut**:  `MSSQL_K8S_LEASE_DURATION_SECONDS` /2

* `MSSQL_K8S_RETRY_PERIOD_SECONDS`
  * Ce paramètre est facultatif
  * **Description**: durée le convertisseur [master](https://kubernetes.io/docs/concepts/architecture/master-node-communication/) attendra avant de le renouveler le bail responsable. Doit être inférieur à `MSSQL_K8S_LEASE_DURATION_SECONDS`.
  * **Par défaut**:  `MSSQL_K8S_RENEW_DEADLINE_SECONDS` /2

* `MSSQL_K8S_ACQUIRE_PERIOD_SECONDS` 
  * Ce paramètre est facultatif
  * **Description**: période de réplicas secondaires interrogent si le bail responsable a expiré. 
  * **Par défaut**: 1


  ## <a name="next-steps"></a>Étapes suivantes

[Groupe de disponibilité de SQL Server sur un cluster Kubernetes](sql-server-ag-kubernetes.md)
