---
title: Se connecter et récupérer des données | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bd4751fe3d1acb7119c87e39ecd8694a0fa83c19
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "69028224"
---
# <a name="connecting-and-retrieving-data"></a>Connexion et récupération de données

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Lorsque vous travaillez avec le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], il existe deux méthodes principales pour établir une connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La première méthode consiste à définir les propriétés de connexion de l'URL de connexion, puis à appeler la méthode getConnection de la classe DriverManager pour retourner un objet [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
> [!NOTE]  
> Pour obtenir la liste des propriétés de connexion prises en charge par le pilote JDBC, consultez [Définir les propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).  
  
La seconde méthode implique de définir les propriétés de connexion grâce aux méthodes setter de la classe [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md), puis d'appeler la méthode [getConnection](../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md) pour retourner un objet SQLServerConnection.  
  
Les rubriques de cette section décrivent les différentes façons de se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; elles présentent également différentes techniques d'extraction de données.  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
| Rubrique                                                                | Description                                                                                                                                                   |
| -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Exemple d’URL de connexion](../../connect/jdbc/connection-url-sample.md) | Décrit l'utilisation d'une URL de connexion pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et l'utilisation d'une instruction SQL pour extraire des données. |
| [Exemple de source de données](../../connect/jdbc/data-source-sample.md)       | Décrit l'utilisation d'une source de données pour se connecter à SQL Server et l'utilisation d'une procédure stockée pour extraire des données.                                                 |
  
## <a name="see-also"></a>Voir aussi

[Exemples d'applications du pilote JDBC](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
