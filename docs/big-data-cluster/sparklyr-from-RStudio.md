---
title: Utilisez sparklyr à partir de RStudio
titleSuffix: SQL Server big data clusters
description: Connectez-vous au cluster big data à l’aide de sparklyr à partir de RStudio.
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8004146499bd8b17c7705f7558de075dfece5813
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65994180"
---
# <a name="use-sparklyr-in-sql-server-big-data-cluster"></a>Utiliser sparklyr dans un cluster de données volumineux de SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sparklyr fournit une interface R pour Apache Spark. Sparklyr est un moyen populaire pour les développeurs R d’utiliser Spark. Cet article décrit comment utiliser sparklyr dans un cluster de données volumineuses de SQL Server 2019 (version préliminaire) à l’aide de RStudio.

## <a name="prerequisites"></a>Prérequis

- [Déployer un cluster de données volumineuses de SQL Server 2019](quickstart-big-data-cluster-deploy.md).

### <a name="install-rstudio-desktop"></a>Installer RStudio Desktop

Installer et configurer **RStudio Desktop** en procédant comme suit :

1. Si vous exécutez sur un client Windows, [télécharger et installer R 3.4.4](https://cran.rstudio.com/bin/windows/base/old/3.4.4).

1. [Téléchargez et installez RStudio Desktop](https://www.rstudio.com/products/rstudio/download/).

1. Une fois l’installation terminée, exécutez les commandes suivantes à l’intérieur de RStudio Desktop pour installer les packages requis :

   ```RStudioDesktop
   install.packages("DBI", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   install.packages("dplyr", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   install.packages("sparklyr", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   ```

## <a name="connect-to-spark-in-a-big-data-cluster"></a>Se connecter à Spark dans un cluster de données volumineux

Vous pouvez utiliser sparklyr pour se connecter à partir d’un client pour le cluster de données volumineux à l’aide de Livy et la passerelle HDFS/Spark. 

Dans RStudio, créez un script R et se connecter à Spark comme dans l’exemple suivant :

> [!TIP]
> Pour le `<USERNAME>` et `<PASSWORD>` valeurs, utilisez le nom d’utilisateur (par exemple, la racine) et le mot de passe définis lors du déploiement de cluster de données volumineuses. Pour le `<IP>` et `<PORT>` valeurs, consultez la documentation sur [connexion à un cluster de données volumineuses](connect-to-big-data-cluster.md).

```r
library(sparklyr)
library(dplyr)
library(DBI)

#Specify the Knox username and password
config <- livy_config(user = "<username>", password = "<password>")

httr::set_config(httr::config(ssl_verifypeer = 0L, ssl_verifyhost = 0L))

sc <- spark_connect(master = "https://<IP>:<PORT>/gateway/default/livy/v1",
                    method = "livy",
                    config = config)
```

## <a name="run-sparklyr-queries"></a>Exécuter des requêtes sparklyr

Après la connexion à Spark, vous pouvez exécuter sparklyr. L’exemple suivant effectue une requête de dataset iris à l’aide de sparklyr :

```r
iris_tbl <- copy_to(sc, iris)

iris_count <- dbGetQuery(sc, "SELECT COUNT(*) FROM iris")

iris_count
```

## <a name="distributed-r-computations"></a>Effectuer des calculs R distribués

Une fonctionnalité de sparklyr est la possibilité de [distribuent des calculs de R](https://spark.rstudio.com/guides/distributed-r/) avec [spark_apply](https://spark.rstudio.com/reference/spark_apply/).

Étant donné que les clusters de données volumineuses utilisent des connexions de Livy, vous devez définir `packages = FALSE` dans l’appel à **spark_apply**. Pour plus d’informations, consultez le [section de Livy](https://spark.rstudio.com/guides/distributed-r/#livy) de la documentation de sparklyr sur des calculs R distribués. Avec ce paramètre, vous pouvez uniquement utiliser les packages R qui sont déjà installés sur votre cluster Spark dans le code R passé à **spark_apply**. L’exemple suivant illustre cette fonctionnalité :

```r
iris_tbl %>% spark_apply(function(e) nrow(e), names = "nrow", group_by = "Species", packages = FALSE)
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses, consultez [que sont les clusters de données volumineuses de SQL Server 2019](big-data-cluster-overview.md).
