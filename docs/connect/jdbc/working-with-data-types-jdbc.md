---
title: Utilisation des types de données (JDBC) | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 19d75051b03a3d6d966961e681e9ce9d70396e86
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "76934445"
---
# <a name="working-with-data-types-jdbc"></a>Utilisation des types de données (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

La fonction principale du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] est de permettre aux développeurs Java d’accéder aux données contenues dans les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour ce faire, le pilote JDBC sert d’interface pour la conversion entre les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les types et objets en langage Java.  
  
> [!NOTE]  
> Pour obtenir une présentation détaillée des types de données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et du pilote JDBC, notamment leurs différences et leur conversion en types de données en langage Java, consultez [Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
Afin de travailler avec les types de données SQL Server, le pilote JDBC fournit les méthodes get\<Type> et set\<Type> pour les classes [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) et [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Il fournit également les méthodes get\<Type> et update\<Type> pour la classe [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md). La méthode que vous utilisez dépend du type de données avec lequel vous travaillez et si vous utilisez des jeux de résultats ou des requêtes.  
  
Les rubriques de cette section décrivent comment utiliser les types de données du pilote JDBC pour accéder aux données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans vos applications Java.  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Exemple de types de données de base](../../connect/jdbc/basic-data-types-sample.md)|Décrit l’utilisation des méthodes getter du jeu de résultats pour récupérer les valeurs des types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de base, ainsi que l’utilisation des méthodes update du jeu de résultats pour mettre à jour ces valeurs.|  
|[Exemple de type de données SQLXML](../../connect/jdbc/sqlxml-data-type-sample.md)|Explique comment stocker des données XML dans une base de données relationnelle, comment récupérer des données XML à partir d’une base de données et comment analyser des données XML à l’aide du type de données Java **SQLXML**.|  
|[Exemple de types de données spatiales](../../connect/jdbc/spatial-data-types-sample.md)|Explique comment stocker et récupérer des données avec des types de données spatiaux 'Geometry' et 'Geography' d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec les types Java **Geometry** et **Geography** définis par Microsoft JDBC Driver.|

## <a name="see-also"></a>Voir aussi

[Exemples d'applications du pilote JDBC](../../connect/jdbc/sample-jdbc-driver-applications.md)  
