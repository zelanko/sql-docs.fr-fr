---
title: Utilisation des types de données (JDBC)
description: Découvrez comment utiliser des types de données dans JDBC Driver pour SQL Server à travers ces exemples d’applications.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6994e7ce587cf72d7879c79604cbe3c68873ddf0
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86923280"
---
# <a name="working-with-data-types-jdbc"></a>Utilisation des types de données (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

La fonction principale du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] est de permettre aux développeurs Java d’accéder aux données contenues dans les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour ce faire, le pilote JDBC sert d’interface pour la conversion entre les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les types et objets en langage Java.

> [!NOTE]
> Pour obtenir une présentation détaillée des types de données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et du pilote JDBC, notamment leurs différences et leur conversion en types de données en langage Java, consultez [Présentation des types de données du pilote JDBC](understanding-the-jdbc-driver-data-types.md).

Afin d’utiliser des types de données SQL Server, le pilote JDBC fournit les méthodes get\<Type> et set\<Type> pour les classes [SQLServerPreparedStatement](reference/sqlserverpreparedstatement-class.md) et [SQLServerCallableStatement](reference/sqlservercallablestatement-class.md). Il fournit également les méthodes get\<Type> et update\<Type> pour la classe [SQLServerResultSet](reference/sqlserverresultset-class.md). La méthode que vous utilisez dépend du type de données avec lequel vous travaillez et si vous utilisez des jeux de résultats ou des requêtes.

Les rubriques de cette section décrivent comment utiliser les types de données du pilote JDBC pour accéder aux données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans vos applications Java.

## <a name="in-this-section"></a>Contenu de cette section

|Rubrique|Description|
|-----------|-----------------|
|[Exemple de types de données de base](basic-data-types-sample.md)|Décrit l’utilisation des méthodes getter du jeu de résultats pour récupérer les valeurs des types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de base, ainsi que l’utilisation des méthodes update du jeu de résultats pour mettre à jour ces valeurs.|
|[Exemple de type de données SQLXML](sqlxml-data-type-sample.md)|Explique comment stocker des données XML dans une base de données relationnelle, comment récupérer des données XML à partir d’une base de données et comment analyser des données XML à l’aide du type de données Java **SQLXML**.|
|[Exemple de types de données spatiales](spatial-data-types-sample.md)|Explique comment stocker et récupérer des données avec des types de données spatiaux 'Geometry' et 'Geography' d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec les types Java **Geometry** et **Geography** définis par Microsoft JDBC Driver.|

## <a name="see-also"></a>Voir aussi

[Exemples d'applications du pilote JDBC](sample-jdbc-driver-applications.md)
