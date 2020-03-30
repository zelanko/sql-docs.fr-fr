---
title: Utiliser la résolution d’adresses IP réseau transparente | Microsoft Docs
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
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "68008480"
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

<a name="for-more-information-about-multisubnetfailover-see-odbc-driver-on-linux-and-macos---high-availability-and-disaster-recovery"></a>Pour plus d’informations sur MultiSubnetFailover, consultez [Pilote ODBC sur Linux et macOS – Haute disponibilité et récupération d’urgence](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).
--------------------------------------------------
## <a name="see-also"></a>Voir aussi  
* [Microsoft ODBC Driver for SQL Server sur Windows](../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
* [Clustering de sous-réseaux multiples SQL Server (SQL Server)](https://msdn.microsoft.com/library/ff878716.aspx#RelatedContent)
