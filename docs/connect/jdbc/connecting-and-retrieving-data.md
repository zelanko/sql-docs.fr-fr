---
title: Connexion et récupération de données
description: Découvrez comment vous connecter à une base de données SQL et récupérer des données à l’aide du pilote Microsoft JDBC pour SQL Server et de ces exemples de code.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 92565d42605b67f61d3ab5e3842e3fb9f110b626
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86922885"
---
# <a name="connecting-and-retrieving-data"></a>Connexion et récupération de données

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Lorsque vous travaillez avec le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], il existe deux méthodes principales pour établir une connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La première méthode consiste à définir les propriétés de connexion de l'URL de connexion, puis à appeler la méthode getConnection de la classe DriverManager pour retourner un objet [SQLServerConnection](reference/sqlserverconnection-class.md).

> [!NOTE]
> Pour obtenir la liste des propriétés de connexion prises en charge par le pilote JDBC, consultez [Définir les propriétés de connexion](setting-the-connection-properties.md).

La seconde méthode implique de définir les propriétés de connexion grâce aux méthodes setter de la classe [SQLServerDataSource](reference/sqlserverdatasource-class.md), puis d'appeler la méthode [getConnection](reference/getconnection-method-sqlserverdatasource.md) pour retourner un objet SQLServerConnection.

Les rubriques de cette section décrivent les différentes façons de se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; elles présentent également différentes techniques d'extraction de données.

## <a name="in-this-section"></a>Contenu de cette section

| Rubrique                                             | Description                                                                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Exemple d’URL de connexion](connection-url-sample.md) | Décrit l'utilisation d'une URL de connexion pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et l'utilisation d'une instruction SQL pour extraire des données. |
| [Exemple de source de données](data-source-sample.md)       | Décrit l'utilisation d'une source de données pour se connecter à SQL Server et l'utilisation d'une procédure stockée pour extraire des données.                                                 |

## <a name="see-also"></a>Voir aussi

[Exemples d'applications du pilote JDBC](sample-jdbc-driver-applications.md)
