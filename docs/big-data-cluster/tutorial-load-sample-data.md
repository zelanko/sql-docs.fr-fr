---
title: Charger des exemples de données
titleSuffix: SQL Server 2019 big data clusters
description: Ce didacticiel montre comment charger des exemples de données dans un cluster de données volumineux de SQL Server. Les exemples de données inclut des données relationnelles dans l’instance principale de SQL Server. Il inclut également des données HDFS dans le pool de stockage. Ces données prend en charge les autres didacticiels de cette section.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/13/2018
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: a89b1bec266f590d6e96365436fe5339b9152f92
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241473"
---
# <a name="tutorial-load-sample-data-into-a-sql-server-2019-big-data-cluster"></a>Didacticiel : Charger des exemples de données dans un cluster de données volumineux de SQL Server 2019

Ce didacticiel explique comment utiliser un script pour charger des exemples de données dans un cluster de données volumineuses de SQL Server 2019 (version préliminaire). La plupart des autres didacticiels dans la documentation utilisent ces exemples de données.

> [!TIP]
> Vous trouverez des exemples supplémentaires pour le cluster de données volumineux de SQL Server 2019 (version préliminaire) dans le [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster) référentiel GitHub. Ils se trouvent dans le **sql-server-samples/samples/features/sql-big-data-cluster/** chemin d’accès.

## <a name="prerequisites"></a>Prérequis

- [Un cluster déployé des données volumineuses](deployment-guidance.md)
- [Outils de données volumineuses](deploy-big-data-tools.md)
   - **mssqlctl**
   - **kubectl**
   - **sqlcmd**
   - **curl**

## <a id="sampledata"></a> Charger des exemples de données

Les étapes suivantes utilisent un script de démarrage pour télécharger une sauvegarde de base de données SQL Server et de charger les données dans votre cluster de données volumineux. Simplicité d’utilisation, ces étapes ont été décomposés en [Windows](#windows) et [Linux](#linux) sections.

## <a id="windows"></a> Windows

Les étapes suivantes décrivent comment utiliser un client Windows pour charger les exemples de données dans votre cluster de données volumineux.

1. Ouvrez une nouvelle invite de commandes Windows.

   > [!IMPORTANT]
   > N’utilisez pas Windows PowerShell pour ces étapes. Dans PowerShell, le script échouera, car il utilise la version de PowerShell de **curl**.

1. Utilisez **curl** pour télécharger le script de démarrage pour les exemples de données.

   ```cmd
   curl -o bootstrap-sample-db.cmd "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd"
   ```

1. Téléchargez le **bootstrap-exemples-db.sql** script Transact-SQL. Ce script est appelé par le script de démarrage.

   ```cmd
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Le script de démarrage nécessite les paramètres positionnels suivants pour votre cluster big data :

   | Paramètre | Description |
   |---|---|
   | &LT; CLUSTER_NAMESPACE &GT; | Le nom que vous avez donné votre cluster de données volumineux. |
   | &LT; SQL_MASTER_IP &GT; | L’adresse IP de votre instance principale. |
   | &LT; SQL_MASTER_SA_PASSWORD &GT; | Le mot de passe SA pour l’instance principale. |
   | &LT; KNOX_IP &GT; | L’adresse IP de la passerelle HDFS/Spark. |
   | &LT; KNOX_PASSWORD &GT; | Le mot de passe pour la passerelle HDFS/Spark. |

   > [!TIP]
   > Utilisez [kubectl](cluster-troubleshooting-commands.md) pour trouver les adresses IP pour l’instance principale de SQL Server et la Knox. Exécutez `kubectl get svc -n <your-cluster-name>` et examinez les adresses IP externe pour l’instance principale (**pool de point de terminaison principal**) et Knox (**service-sécurité-lb** ou **service-sécurité-nodeport**).

1. Exécutez le script de démarrage.

   ```cmd
   .\bootstrap-sample-db.cmd <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a id="linux"></a> Linux

Les étapes suivantes décrivent comment utiliser un client Linux pour charger les exemples de données dans votre cluster de données volumineux.

1. Téléchargez le script de démarrage et lui assigner des autorisations exécutables.

   ```bash
   curl -o bootstrap-sample-db.sh "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh"
   chmod +x bootstrap-sample-db.sh
   ```

1. Téléchargez le **bootstrap-exemples-db.sql** script Transact-SQL. Ce script est appelé par le script de démarrage.

   ```bash
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Le script de démarrage nécessite les paramètres positionnels suivants pour votre cluster big data :

   | Paramètre | Description |
   |---|---|
   | &LT; CLUSTER_NAMESPACE &GT; | Le nom que vous avez donné votre cluster de données volumineux. |
   | &LT; SQL_MASTER_IP &GT; | L’adresse IP de votre instance principale. |
   | &LT; SQL_MASTER_SA_PASSWORD &GT; | Le mot de passe SA pour l’instance principale. |
   | &LT; KNOX_IP &GT; | L’adresse IP de la passerelle HDFS/Spark. |
   | &LT; KNOX_PASSWORD &GT; | Le mot de passe pour la passerelle HDFS/Spark. |

   > [!TIP]
   > Utilisez [kubectl](cluster-troubleshooting-commands.md) pour trouver les adresses IP pour l’instance principale de SQL Server et la Knox. Exécutez `kubectl get svc -n <your-cluster-name>` et examinez les adresses IP externe pour l’instance principale (**pool de point de terminaison principal**) et Knox (**service-sécurité-lb** ou **service-sécurité-nodeport**).

1. Exécutez le script de démarrage.

   ```bash
   ./bootstrap-sample-db.sh <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a name="next-steps"></a>Étapes suivantes

Une fois le script de démarrage s’exécute, votre cluster de données volumineux a les bases de données et les données HDFS. Pour commencer à Explorer ces données et les clusters de données volumineuses, consultez le [didacticiels](tutorial-query-hdfs-storage-pool.md) dans cette section.