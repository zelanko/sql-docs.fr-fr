---
title: Utilisation de la résolution d’adresses IP réseau transparente
description: Découvrez la résolution d’adresses IP réseau transparente du pilote ODBC Driver for SQL Server et la façon dont elle affecte la fonctionnalité MultiSubnetFailover.
ms.custom: ''
ms.date: 05/06/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d255208f-d486-4ad3-8080-61c6e0261825
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1a003b4817868516c6acfac10df80cafdf044c01
ms.sourcegitcommit: 37a3e2c022c578fc3a54ebee66d9957ff7476922
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82922292"
---
# <a name="using-transparent-network-ip-resolution"></a>Utilisation de la résolution d’adresses IP réseau transparente
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

TransparentNetworkIPResolution est une révision de la fonctionnalité MultiSubnetFailover existante, disponible dans la version 13.1 de Microsoft ODBC Driver for SQL Server, qui concerne la séquence de connexion du pilote dans le cas où la première adresse IP résolue du nom d’hôte ne répond pas et plusieurs adresses IP sont associées au nom d’hôte. Elle interagit avec MultiSubnetFailover pour fournir trois séquences de connexion :

* 0 : Une adresse IP est tentée, suivie de toutes les adresses IP en parallèle.
* 1 : Toutes les adresses IP sont tentées en parallèle.
* 2 : Toutes les adresses IP sont tentées l’une après l’autre.

|TransparentNetworkIPResolution|MultiSubnetFailover|Comportement|
|:-:|:-:|:-:|
|(par défaut)|(par défaut)|0|
|(par défaut)|activé|1|
|(par défaut)|Désactivé|0|
|activé|(par défaut)|0|
|activé|activé|1|
|activé|Désactivé|0|
|Désactivé|(par défaut)|2|
|Désactivé|activé|1|
|Désactivé|Désactivé|2|

La chaîne de connexion `TransparentNetworkIPResolution` et le mot clé DSN contrôlent ce paramètre au niveau de la chaîne de connexion. Il est activé par défaut.

Mot clé|Valeurs|Default
-|-|-
`TransparentNetworkIPResolution`|`Yes`, `No`|`Yes`

L’attribut préconnexion `SQL_COPT_SS_TNIR` permet à une application de contrôler programmatiquement ce paramètre :

Attribut de connexion|   Taille/Type|  Default| Valeur| Description
-|-|-|-|-
`SQL_COPT_SS_TNIR` (1249)| `SQL_IS_INTEGER` ou `SQL_IS_UINTEGER`| `SQL_IS_ON`(1), `SQL_IS_OFF`(0)|`SQL_IS_ON`|Active ou désactive TNIR.

<a name="for-more-information-about-multisubnetfailover-see-odbc-driver-on-linux-and-macos---high-availability-and-disaster-recovery"></a>Pour plus d’informations sur MultiSubnetFailover, consultez [Pilote ODBC sur Linux et macOS – Haute disponibilité et récupération d’urgence](linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).
--------------------------------------------------
## <a name="see-also"></a>Voir aussi  
* [Microsoft ODBC Driver for SQL Server sur Windows](windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
* [Clustering de sous-réseaux multiples SQL Server (SQL Server)](../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md)
