---
title: Utilisez sparklyr à partir de RStudio
titleSuffix: SQL Server 2019 big data clusters
description: Connectez-vous au cluster Big data à l’aide de sparklyr à partir de RStudio.
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 83980f9d08a3894b0fbf7871cf899483e06702c4
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018355"
---
# <a name="use-sparklyr-in-sql-server-2019-big-data-cluster"></a>Utiliser Sparklyr dans un cluster de données SQL Server 2019 Big

Sparklyr fournit une interface R pour Apache Spark. Sparklyr est la façon préférée pour les développeurs R d’utiliser Spark. Cet article décrit comment utiliser sparklyr dans un cluster de données volumineuses de SQL Server 2019 (version préliminaire) à l’aide de RStudio.

## <a name="prerequisites"></a>Prérequis

- [Déployer un cluster de données volumineuses de SQL Server 2019](quickstart-big-data-cluster-deploy.md).
- [Installer RStudio](https://www.rstudio.com/)

## <a name="connect-to-spark-in-ss19-big-data-cluster"></a>Se connecter à spark dans le cluster de SS19 Big Data

Dans RStudio, créer un RScript et se connecter à la Spark comme suit. Cluster de données volumineuses Spark se connecte via Livy, ce qui peut être atteinte avec la [passerelle HDFS/Spark](connect-to-big-data-cluster.md#hdfs). Pour l’authentification, utilisez le nom d’utilisateur et le mot de passe définis lors du déploiement.

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