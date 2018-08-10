---
title: Utilisation de données volumineuses | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5b93569f-eceb-4f05-b49c-067564cd3c85
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a60bc049b02ca998119fd4741fa51589a029aeca
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39452293"
---
# <a name="working-with-large-data"></a>Utilisation de données volumineuses

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le pilote JDBC prend en charge la mise en mémoire tampon adaptative, ce qui vous permet de récupérer tout type de données de grande valeur sans la charge liée au temps de traitement des curseurs côté serveur. Avec la mise en mémoire tampon adaptative, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] récupère les résultats de l’exécution des instructions à partir du serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] chaque fois que l’application en a besoin, et non en une seule fois. Le pilote ignore également les résultats dès que l'application ne peut plus y accéder.

Dans [!INCLUDE[msCoName](../../includes/msconame_md.md)] JDBC Driver version 1.2 pour [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)], le mode de mise en mémoire tampon était « **full** » par défaut. Si votre application n’a pas affecté la valeur « **adaptive** » à la propriété de connexion « responseBuffering », soit dans les propriétés de connexion, soit à l’aide de la méthode [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) de l’objet [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), cela signifie que le pilote prenait en charge la lecture en une seule fois de l’ensemble des résultats à partir du serveur. Pour pouvoir obtenir le comportement de mise en mémoire tampon adaptative, votre application devait affecter explicitement « **adaptive** » à la propriété de connexion « responseBuffering ».  
  
La valeur **adaptive** représente le mode de mise en mémoire tampon par défaut ; par ailleurs, le pilote JDBC met en mémoire tampon la plus petite quantité de données possible en cas de nécessité. Pour plus d’informations sur l’utilisation de la mise en mémoire tampon adaptative, consultez [à l’aide de mise en mémoire tampon adaptative](../../connect/jdbc/using-adaptive-buffering.md).  
  
 Les rubriques de cette section décrivent différentes façons de récupérer des données de valeur élevée à partir d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
| Rubrique                                                                                                                      | Description                                                              |
| -------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| [Exemple de lecture de données volumineuses](../../connect/jdbc/reading-large-data-sample.md)                                               | Explique comment utiliser une instruction SQL pour récupérer des données de grande valeur.       |
| [Exemple de lecture de données volumineuses avec des procédures stockées](../../connect/jdbc/reading-large-data-with-stored-procedures-sample.md) | Explique comment récupérer une valeur de paramètre OUT CallableStatement de grande taille. |
| [Exemple de mise à jour de données volumineuses](../../connect/jdbc/updating-large-data-sample.md)                                             | Explique comment mettre à jour des données de grande valeur dans une base de données.                |
  
## <a name="see-also"></a> Voir aussi

[Exemples d’applications JDBC Driver](../../connect/jdbc/sample-jdbc-driver-applications.md)  
