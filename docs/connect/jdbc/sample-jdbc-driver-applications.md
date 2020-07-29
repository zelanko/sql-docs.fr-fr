---
title: Exemples d'applications du pilote JDBC
description: Les exemples d'application du pilote JDBC pour SQL Server illustrent différentes fonctionnalités et pratiques de programmation appropriées que vous pouvez suivre lors de l’utilisation du pilote JDBC.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e136b87c-a138-45d6-8c3e-bcef94b7e483
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 17479d32cd752650b4bfb1d03f5bc36ab52d8ca4
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86915915"
---
# <a name="sample-jdbc-driver-applications"></a>Exemples d'applications du pilote JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Les exemples d’applications de [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] illustrent diverses fonctionnalités du pilote JDBC. En outre, ils présentent les bonnes pratiques de programmation que vous pouvez suivre lors de l’utilisation du pilote JDBC avec une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Tous les exemples d'applications sont contenus dans les fichiers de code *.java qui peuvent être compilés et exécutés sur votre ordinateur local ; ils se trouvent dans plusieurs sous-dossiers à l'emplacement suivant :

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples
```

Les rubriques de cette section décrivent la configuration et l'exécution des exemples d'applications et incluent une présentation de ce que montrent les exemples d'applications.

## <a name="in-this-section"></a>Contenu de cette section

| Rubrique                                                                            | Description                                                                                                                                                                                                                                                             |
| -------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Connexion et récupération de données](connecting-and-retrieving-data.md)              | Ces exemples d’applications présentent la connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ils présentent également différentes façons de récupérer des données à partir d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. |
| [Utiliser des types de données &#40;JDBC&#41;](working-with-data-types-jdbc.md)        | Ces exemples d’applications présentent l’utilisation des méthodes des types de données du pilote JDBC pour travailler avec des données dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].                                                                                           |
| [Utilisation de jeux de résultats](working-with-result-sets.md)                          | Ces exemples d’applications présentent l’utilisation de jeux de résultats pour traiter des données contenues dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].                                                                                                         |
| [Utilisation de données volumineuses](working-with-large-data.md)                            | Ces exemples d’applications montrent comment utiliser la mise en mémoire tampon adaptative pour récupérer des données de valeur élevée d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sans la charge mémoire associée aux curseurs côté serveur.                                                      |
| [Découverte et classification des données SQL](data-discovery-classification-sample.md) | Cet exemple d’application montre comment récupérer les informations de recherche et de classification de données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d’un objet ResultSet avec le pilote JDBC.                                         |

## <a name="see-also"></a>Voir aussi

[Présentation du pilote JDBC](overview-of-the-jdbc-driver.md)
