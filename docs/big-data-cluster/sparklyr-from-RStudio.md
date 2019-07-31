---
title: Utiliser sparklyr à partir de RStudio
titleSuffix: SQL Server big data clusters
description: Connectez-vous au cluster Big Data à l’aide de sparklyr à partir de RStudio.
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f346fed17e4c79214a7eba43f70767fc80b98a07
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "67728378"
---
# <a name="use-sparklyr-in-sql-server-big-data-cluster"></a>Utiliser sparklyr dans SQL Server Cluster Big Data

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sparklyr fournit une interface R pour Apache Spark. Sparklyr est un moyen populaire pour les développeurs de R d’utiliser Spark. Cet article explique comment utiliser sparklyr dans un cluster SQL Server 2019 Big Data (version préliminaire) à l’aide de RStudio.

## <a name="prerequisites"></a>Prérequis

- [Déployez un cluster SQL Server 2019 Big Data](quickstart-big-data-cluster-deploy.md).

### <a name="install-rstudio-desktop"></a>Installer RStudio Desktop

Installez et configurez **RStudio Desktop** en procédant comme suit:

1. Si vous exécutez sur un client Windows, [Téléchargez et installez R 3.4.4](https://cran.rstudio.com/bin/windows/base/old/3.4.4).

1. [Téléchargez et installez RStudio Desktop](https://www.rstudio.com/products/rstudio/download/).

1. Une fois l’installation terminée, exécutez les commandes suivantes à l’intérieur de RStudio Desktop pour installer les packages requis:

   ```RStudioDesktop
   install.packages("DBI", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   install.packages("dplyr", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   install.packages("sparklyr", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   ```

## <a name="connect-to-spark-in-a-big-data-cluster"></a>Se connecter à Spark dans un cluster Big Data

Vous pouvez utiliser sparklyr pour vous connecter à partir d’un client au cluster Big Data à l’aide de livy et de la passerelle HDFS/Spark. 

Dans RStudio, créez un script R et connectez-vous à Spark comme dans l’exemple suivant:

> [!TIP]
> Pour les `<USERNAME>` valeurs `<PASSWORD>` et, utilisez le nom d’utilisateur (par exemple, racine) et le mot de passe que vous définissez lors du déploiement du cluster Big Data. Pour obtenir `<IP>` les `<PORT>` valeurs et, consultez la documentation sur la [connexion à un cluster Big Data](connect-to-big-data-cluster.md).

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

Après vous être connecté à Spark, vous pouvez exécuter sparklyr. L’exemple suivant exécute une requête sur un jeu de données IRIS à l’aide de sparklyr:

```r
iris_tbl <- copy_to(sc, iris)

iris_count <- dbGetQuery(sc, "SELECT COUNT(*) FROM iris")

iris_count
```

## <a name="distributed-r-computations"></a>Calculs R distribués

L’une des fonctionnalités de sparklyr est la possibilité de [distribuer des calculs R](https://spark.rstudio.com/guides/distributed-r/) avec [spark_apply](https://spark.rstudio.com/reference/spark_apply/).

Étant donné que les clusters Big Data utilisent des connexions livy `packages = FALSE` , vous devez définir dans l’appel à **spark_apply**. Pour plus d’informations, consultez la [section livy](https://spark.rstudio.com/guides/distributed-r/#livy) de la documentation sparklyr sur les calculs R distribués. Avec ce paramètre, vous ne pouvez utiliser que les packages R déjà installés sur votre cluster Spark dans le code R transmis à **spark_apply**. L’exemple suivant illustre cette fonctionnalité:

```r
iris_tbl %>% spark_apply(function(e) nrow(e), names = "nrow", group_by = "Species", packages = FALSE)
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [que sont les clusters SQL Server 2019 Big Data](big-data-cluster-overview.md).
