---
title: Utilisation de données volumineuses
description: Découvrez comment utiliser des types de données volumineuses dans JDBC Driver pour SQL Server dans ces exemples d’applications.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5b93569f-eceb-4f05-b49c-067564cd3c85
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 09099ca9b8d007b52d47122d7be55d6fbef81301
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86923281"
---
# <a name="working-with-large-data"></a>Utilisation de données volumineuses

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le pilote JDBC prend en charge la mise en mémoire tampon adaptative, ce qui vous permet de récupérer tout type de données de grande valeur sans la charge liée au temps de traitement des curseurs côté serveur. Avec la mise en mémoire tampon adaptative, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] récupère les résultats de l’exécution des instructions à partir du serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chaque fois que l’application en a besoin, et non en une seule fois. Le pilote ignore également les résultats dès que l'application ne peut plus y accéder.

Dans [!INCLUDE[msCoName](../../includes/msconame_md.md)] JDBC Driver version 1.2 pour [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], le mode de mise en mémoire tampon était « **full** » par défaut. Si votre application n’a pas affecté la valeur « **adaptive** » à la propriété de connexion « responseBuffering », soit dans les propriétés de connexion, soit à l’aide de la méthode [setResponseBuffering](reference/setresponsebuffering-method-sqlserverstatement.md) de l’objet [SQLServerStatement](reference/sqlserverstatement-class.md), cela signifie que le pilote prenait en charge la lecture en une seule fois de l’ensemble des résultats à partir du serveur. Pour pouvoir obtenir le comportement de mise en mémoire tampon adaptative, votre application devait affecter explicitement « **adaptive** » à la propriété de connexion « responseBuffering ».

La valeur **adaptive** représente le mode de mise en mémoire tampon par défaut ; par ailleurs, le pilote JDBC met en mémoire tampon la plus petite quantité de données possible en cas de nécessité. Pour plus d’informations sur la mise en mémoire tampon adaptative, consultez [Utiliser la mise en mémoire tampon adaptative](using-adaptive-buffering.md).

 Les rubriques de cette section décrivent différentes façons de récupérer des données de valeur élevée à partir d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="in-this-section"></a>Dans cette section

| Rubrique                                                                                                   | Description                                                              |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| [Exemple de lecture de données volumineuses](reading-large-data-sample.md)                                               | Explique comment utiliser une instruction SQL pour récupérer des données de grande valeur.       |
| [Exemple de lecture de données volumineuses avec des procédures stockées](reading-large-data-with-stored-procedures-sample.md) | Explique comment récupérer une valeur de paramètre OUT CallableStatement de grande taille. |
| [Exemple de mise à jour de données volumineuses](updating-large-data-sample.md)                                             | Explique comment mettre à jour des données de grande valeur dans une base de données.                |

## <a name="see-also"></a>Voir aussi

[Exemples d'applications du pilote JDBC](sample-jdbc-driver-applications.md)
