---
title: Exemples d’applications de pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e136b87c-a138-45d6-8c3e-bcef94b7e483
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6ef5c2d71d398be52ebed2b69020e87d54818176
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028316"
---
# <a name="sample-jdbc-driver-applications"></a>Exemples d'applications du pilote JDBC

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Les exemples d’applications de [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] illustrent diverses fonctionnalités du pilote JDBC. En outre, ils présentent les bonnes pratiques de programmation que vous pouvez suivre lors de l’utilisation du pilote JDBC avec une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
Tous les exemples d'applications sont contenus dans les fichiers de code *.java qui peuvent être compilés et exécutés sur votre ordinateur local ; ils se trouvent dans plusieurs sous-dossiers à l'emplacement suivant :  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples  
```

 Les rubriques de cette section décrivent la configuration et l'exécution des exemples d'applications et incluent une présentation de ce que montrent les exemples d'applications.  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
| Rubrique                                                                                                                  | Description                                                                                                                                                                                                                                                                   |
| ---------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Connexion et récupération de données](../../../connect/jdbc/code-samples/connecting-and-retrieving-data.md)                              | Ces exemples d’applications présentent la connexion à une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Ils présentent également différentes façons de récupérer des données à partir d’une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. |
| [Utiliser des types de données &#40;JDBC&#41;](../../../connect/jdbc/code-samples/working-with-data-types-jdbc.md)                        | Ces exemples d’applications présentent l’utilisation des méthodes des types de données du pilote JDBC pour travailler avec des données dans une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].                                                                                              |
| [Utilisation de jeux de résultats](../../../connect/jdbc/code-samples/working-with-result-sets.md)                                          | Ces exemples d’applications présentent l’utilisation de jeux de résultats pour traiter des données contenues dans une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].                                                                                                            |
| [Utilisation de données volumineuses](../../../connect/jdbc/code-samples/working-with-large-data.md)                                            | Ces exemples d’applications montrent comment utiliser la mise en mémoire tampon adaptative pour récupérer des données de valeur élevée d’une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sans la charge mémoire associée aux curseurs côté serveur.                                                         |
| [Découverte et classification des données SQL](../../jdbc/code-samples/data-discovery-and-classification-sample.md) | Cet exemple d’application montre comment récupérer les informations de découverte et de classification des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] données contenues dans une base de données à partir d’un objet ResultSet à l’aide du pilote JDBC.                                            |
  
## <a name="see-also"></a>Voir aussi

[Présentation du pilote JDBC](../../../connect/jdbc/overview-of-the-jdbc-driver.md)
