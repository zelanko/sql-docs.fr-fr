---
title: Exemples d’Applications de pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e136b87c-a138-45d6-8c3e-bcef94b7e483
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bea9da66105735a69b8d4d0eb53abeeacd233584
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39454503"
---
# <a name="sample-jdbc-driver-applications"></a>Exemples d'applications du pilote JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Les exemples d’applications de [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] illustrent diverses fonctionnalités du pilote JDBC. En outre, ils présentent les bonnes pratiques de programmation que vous pouvez suivre lors de l’utilisation du pilote JDBC avec une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Tous les exemples d'applications sont contenus dans les fichiers de code *.java qui peuvent être compilés et exécutés sur votre ordinateur local ; ils se trouvent dans plusieurs sous-dossiers à l'emplacement suivant :  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples  
```

Les rubriques de cette section décrivent la configuration et l'exécution des exemples d'applications et incluent une présentation de ce que montrent les exemples d'applications.  
  
## <a name="in-this-section"></a>Dans cette section  
  
| Rubrique                                                                                                        | Description                                                                                                                                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Connexion et récupération de données](../../connect/jdbc/connecting-and-retrieving-data.md)                       | Ces exemples d’applications présentent la connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Ils présentent également différentes façons de récupérer des données à partir d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. |
| [Utiliser des types de données &#40;JDBC&#41;](../../connect/jdbc/working-with-data-types-jdbc.md)                 | Ces exemples d’applications présentent l’utilisation des méthodes des types de données du pilote JDBC pour travailler avec des données dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].                                                                                           |
| [Utilisation de jeux de résultats](../../connect/jdbc/working-with-result-sets.md)                                   | Ces exemples d’applications présentent l’utilisation de jeux de résultats pour traiter des données contenues dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].                                                                                                         |
| [Utilisation de données volumineuses](../../connect/jdbc/working-with-large-data.md)                                     | Ces exemples d’applications montrent comment utiliser la mise en mémoire tampon adaptative pour récupérer des données de valeur élevée d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sans la charge mémoire associée aux curseurs côté serveur.                                                      |
| [Découverte et classification des données SQL](../../connect/jdbc/data-discovery-classification-sample.md) | Cet exemple d’application montre comment récupérer les informations de Classification et de découverte de données contenues dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données à partir d’un objet de jeu de résultats à l’aide du pilote JDBC.                                      |
  
## <a name="see-also"></a> Voir aussi

[Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  