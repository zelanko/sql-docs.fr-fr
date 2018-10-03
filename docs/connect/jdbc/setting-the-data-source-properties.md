---
title: Propriétés de la définition des données Source | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f3363d05-07fc-4bf8-ae5e-2a7a968808ad
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ef3719e41680f396c7dcd6bc41d667fe82fe7f6c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47639017"
---
# <a name="setting-the-data-source-properties"></a>Définition des propriétés de la source de données

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Les sources de données représentent le mécanisme recommandé de création de connexions JDBC dans un environnement Java EE (Java Platform, Enterprise Edition). Elles offrent des connexions, des connexions regroupées et des connexions distribuées sans codage effectué de manière irréversible des propriétés de connexion en code Java. Toutes les sources de données du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] peuvent définir ou obtenir la valeur d’une propriété quelconque en utilisant respectivement les méthodes d’accesseur Get et Set appropriées.

Les produits Java EE, tels que les serveurs d'applications et les moteurs servlet/JSP, vous permettent généralement de configurer des sources de données pour l'accès à la base de données. Toute propriété répertoriée dans la rubrique [Définition des propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md) peut être spécifiée à n’importe quel endroit où la configuration vous permet d’entrer une propriété en tant que paire propriété=valeur.

Pour plus d’informations sur les sources de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez la classe [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md). Pour obtenir un exemple montrant comment utiliser la classe SQLServerDataSource pour établir une connexion à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de base de données, consultez [exemple de Source de données](../../connect/jdbc/data-source-sample.md).

## <a name="see-also"></a> Voir aussi

[Connexion à SQL Server avec le pilote JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
