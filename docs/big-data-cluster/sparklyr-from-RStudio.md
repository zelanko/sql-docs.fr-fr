---
title: Utilisez sparklyr à partir de RStudio
titleSuffix: SQL Server big data clusters
description: Connectez-vous au cluster big data à l’aide de sparklyr à partir de RStudio.
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 30b8ddccd01c0e8d9a4eac34f2f504b0d8971af6
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860190"
---
# <a name="use-sparklyr-in-sql-server-big-data-cluster"></a>Utiliser Sparklyr dans un cluster de données volumineux de SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sparklyr fournit une interface R pour Apache Spark. Sparklyr est la façon préférée pour les développeurs R d’utiliser Spark. Cet article décrit comment utiliser sparklyr dans un cluster de données volumineuses de SQL Server 2019 (version préliminaire) à l’aide de RStudio.

## <a name="prerequisites"></a>Prérequis

- [Déployer un cluster de données volumineuses de SQL Server 2019](quickstart-big-data-cluster-deploy.md).
- [Installer RStudio](https://www.rstudio.com/)

## <a name="connect-to-spark-in-ss19-big-data-cluster"></a>Se connecter à spark dans le cluster de SS19 Big Data

Dans RStudio, créer un RScript et se connecter à la Spark comme suit. Cluster de données volumineux Spark se connecte via Livy, ce qui peut être atteinte avec la [passerelle HDFS/Spark](connect-to-big-data-cluster.md#hdfs). Pour l’authentification, utilisez le nom d’utilisateur et le mot de passe définis lors du déploiement.

```r
library(sparklyr)
library(dplyr)
library(DBI)

#Specify the Knox username and password
config <- livy_config(user = "***root***", password = "****")

httr::set_config(httr::config(ssl_verifypeer = 0L))

sc <- spark_connect(master = "https://<IP>:<PORT>/gateway/default/livy/v1",
                    method = "livy",
                    config = config)
```

## <a name="run-sparklyr-queries"></a>Exécuter des requêtes sparklyr

Après la connexion à Spark, vous pouvez exécuter sparklyr. L’exemple suivant effectue une requête de dataset iris à l’aide de sparklyr :

``` r
copy_to(sc, iris)

iris_count <- dbGetQuery(sc, "SELECT COUNT(*) FROM iris")

iris_count
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses, consultez [que sont les clusters de données volumineuses de SQL Server 2019 ?](big-data-cluster-overview.md).