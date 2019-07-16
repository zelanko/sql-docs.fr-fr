---
title: Utiliser T-SQL (CREATE EXTERNAL LIBRARY) pour installer des packages R - Services de SQL Server Machine Learning
description: Ajouter de nouveaux packages R pour SQL Server 2016 R Services ou SQL Server 2017 Machine Learning Services (en base de données).
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/12/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 7d858cbc34ef614c5b84ed7543ceaa837d136a4e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962618"
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server"></a>Utiliser T-SQL (CREATE EXTERNAL LIBRARY) pour installer des packages R sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article explique comment installer de nouveaux packages R sur une instance de SQL Server où l’apprentissage automatique est activé. Il existe plusieurs approches sélectionnables. À l’aide de T-SQL convient le mieux pour les administrateurs de serveur qui ne sont pas familiarisés avec R.

**S’applique à :**  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Le [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) instruction permet d’ajouter un package ou un ensemble de packages à une instance ou une base de données spécifique sans avoir à exécuter R ou Python code directement. Toutefois, cette méthode nécessite la préparation du package et les autorisations de base de données supplémentaires.

+ Tous les packages doivent être disponibles en tant qu’un fichier zip local, et non téléchargé à la demande à partir d’internet.

+ Toutes les dépendances doivent être identifiés par le nom et la version et inclus dans le fichier zip. L’instruction échoue si les packages nécessaires ne sont pas disponibles, y compris les dépendances de package en aval. 

+ Vous devez être **db_owner** ou posséder une autorisation de créer une bibliothèque externe sur un rôle de base de données. Pour plus d’informations, consultez [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="download-packages-in-archive-format"></a>Télécharger les packages au format d’archive

Si vous installez un package unique, téléchargez le package au format compressé.

Il est plus courant d’installer plusieurs packages en raison des dépendances de package. Lorsqu’un package requiert d’autres packages, vous devez vérifier que tous les sont accessibles à l’autre lors de l’installation. Nous vous recommandons de [création d’un référentiel local](create-a-local-package-repository-using-minicran.md) à l’aide de [miniCRAN](https://andrie.github.io/miniCRAN/) pour assembler une collection complète des packages, ainsi que [igraph](https://igraph.org/r/) pour l’analyse des dépendances de packages. L’installation d’une version incorrecte d’un package ou l’omission d’une dépendance de package peut entraîner une Échec de l’instruction CREATE EXTERNAL LIBRARY. 

## <a name="copy-the-file-to-a-local-folder"></a>Copiez le fichier dans un dossier local

Copiez le fichier compressé contenant tous les packages vers un dossier local sur le serveur. Si vous n’avez pas d’accès au système de fichiers sur le serveur, vous pouvez également passer un package complet en tant que variable, à l’aide d’un format binaire. Pour plus d’informations, consultez [CREATE EXTERNAL LIBRARY](../../t-sql/statements/create-external-library-transact-sql.md).

## <a name="run-the-statement-to-upload-packages"></a>Exécutez l’instruction pour charger des packages

Ouvrir un **requête** fenêtre, à l’aide d’un compte avec des privilèges d’administrateur.

Exécutez l’instruction T-SQL `CREATE EXTERNAL LIBRARY` pour charger la collection de package compressé dans la base de données.

Par exemple, l’instruction suivante nomme comme source du package miniCRAN référentiel contenant le **randomForest** package, ainsi que ses dépendances. 

```sql
CREATE EXTERNAL LIBRARY randomForest
FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
WITH (LANGUAGE = 'R');
```

Vous ne pouvez pas utiliser un nom arbitraire ; le nom de la bibliothèque externe doit avoir le même nom que vous utiliserez lors du chargement ou de l’appel.

## <a name="verify-package-installation"></a>Vérifier l’installation du package

Si la bibliothèque est créée avec succès, vous pouvez exécuter le package dans SQL Server, en l’appelant à l’intérieur d’une procédure stockée.
    
```sql
EXEC sp_execute_external_script
@language =N'R',
@script=N'library(randomForest)'
```

## <a name="see-also"></a>Voir aussi

+ [Obtenir les informations sur le package](../package-management/installed-package-information.md)
+ [Didacticiels R](../tutorials/sql-server-r-tutorials.md)
