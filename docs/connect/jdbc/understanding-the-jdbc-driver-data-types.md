---
title: "Présentation des Types de données du pilote JDBC | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7802328d-4d23-4775-9573-4169b127d258
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1cd9f516a8d72aabf8b10d25b9553cf35a3be3bd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="understanding-the-jdbc-driver-data-types"></a>Présentation des types de données de pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]prend en charge l’utilisation des types de données de base et avancés JDBC dans une application Java qui utilise [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] comme base de données.  
  
 Le système de type JDBC modère la conversion entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] des types de données et les types de langage Java et les objets. Les types JDBC sont modelés sur les types SQL-92 et SQL-99. Le pilote JDBC adhère à la spécification JDBC et est conçu pour fournir un bon compromis entre la prévisibilité et la flexibilité.  
  
 Les rubriques de cette section décrivent comment utiliser les types de données de base et avancés et comment les types de données peuvent être convertis en d'autres types de données.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[À l’aide des Types de base de données](../../connect/jdbc/using-basic-data-types.md)|Décrit les types de données de base JDBC. Inclut des exemples illustrant comment travailler avec les types de données en utilisant des jeux de résultats, des requêtes paramétrables et des procédures stockées.|  
|[Configurer la façon dont les valeurs java.sql.Time sont envoyées au serveur](../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)|Décrit la manière dont le pilote JDBC génère les dates.|  
|[À l’aide des Types de données avancés](../../connect/jdbc/using-advanced-data-types.md)|Décrit les types de données avancés JDBC.|  
|[Comprendre les différences entre les types de données](../../connect/jdbc/understanding-data-type-differences.md)|Décrit les différences entre les différents types de données de pilote JDBC.|  
|[Présentation des Conversions de Type de données](../../connect/jdbc/understanding-data-type-conversions.md)|Explique comment est gérée la conversion de type de données lors de l'utilisation de méthodes getter et setter.|  
|[Prise en charge du jeu de caractères nationaux](../../connect/jdbc/national-character-set-support.md)|Décrit la prise en charge des types du jeu de caractères nationaux.|  
|[Prise en charge des données XML](../../connect/jdbc/supporting-xml-data.md)|Décrit l'interface SQLXML. Décrit également comment lire et écrire des données XML depuis et vers la base de données relationnelle avec le **SQLXML** type de données Java.|  
|[Wrappers et Interfaces](../../connect/jdbc/wrappers-and-interfaces.md)|Présente les interfaces qui ont le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] des méthodes spécifiques et des constantes qui permettent à un serveur d’application créer un proxy de la classe, traite également prend en charge pour le l’interface java.sql.Wrapper.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
