---
title: Utilisation de la résolution transparente des adresses IP réseau | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d255208f-d486-4ad3-8080-61c6e0261825
author: MightyPen
ms.author: genemi
ms.openlocfilehash: df5b0233168c52b4f79cdc6d2d03cd7b72e16046
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008480"
---
# <a name="using-transparent-network-ip-resolution"></a>Utilisation de la résolution d’adresses IP réseau transparente
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

TransparentNetworkIPResolution est une révision de la fonctionnalité MultiSubnetFailover existante, disponible dans le pilote Microsoft ODBC 13,1 pour SQL Server, qui affecte la séquence de connexion du pilote dans le cas où la première adresse IP résolue du nom d’hôte n’est pas répondez et plusieurs adresses IP sont associées au nom d’hôte. Il interagit avec MultiSubnetFailover pour fournir les trois séquences de connexion suivantes:

* 0: une adresse IP est tentée, suivie de toutes les adresses IP en parallèle
* 1: toutes les adresses IP sont tentées en parallèle
* 2: toutes les adresses IP sont tentées l’une après l’autre

|TransparentNetworkIPResolution|MultiSubnetFailover|Attitude|
|:-:|:-:|:-:|
|(par défaut)|(par défaut)|0|
|(par défaut)|Activé|1|
|(par défaut)|Désactivé|0|
|Activé|(par défaut)|0|
|Activé|Activé|1|
|Activé|Désactivé|0|
|Désactivé|(par défaut)|2|
|Désactivé|Activé|1|
|Désactivé|Désactivé|2|

La `TransparentNetworkIPResolution` chaîne de connexion et le mot clé DSN contrôlent ce paramètre au niveau de la chaîne de connexion. La valeur par défaut est activé.

Mot clé|Valeurs|Valeur par défaut
-|-|-
`TransparentNetworkIPResolution`|`Yes`, `No`|`Yes`

L' `SQL_COPT_SS_TNIR` attribut de pré-connexion permet à une application de contrôler ce paramètre par programme:

Attribut de connexion|   Taille/Type|  Valeur par défaut| Valeur| Description
-|-|-|-|-
`SQL_COPT_SS_TNIR` (1249)| `SQL_IS_INTEGER` ou `SQL_IS_UINTEGER`| `SQL_IS_ON`(1), `SQL_IS_OFF`(0)|`SQL_IS_ON`|Active ou désactive TNIR.

<a name="for-more-information-about-multisubnetfailover-see-odbc-driver-on-linux-and-macos---high-availability-and-disaster-recoveryconnectodbclinux-macodbc-driver-on-linux-support-for-high-availability-disaster-recoverymd"></a>Pour plus d’informations sur MultiSubnetFailover, consultez [pilote ODBC sur Linux et MacOS-haute disponibilité et récupération d’urgence](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)
--------------------------------------------------
## <a name="see-also"></a>Voir aussi  
* [Microsoft ODBC Driver for SQL Server sur Windows](../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
* [Clustering de sous-réseaux multiples SQL Server (SQL Server)](https://msdn.microsoft.com/library/ff878716.aspx#RelatedContent)
