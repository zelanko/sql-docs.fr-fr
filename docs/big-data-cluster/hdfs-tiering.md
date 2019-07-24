---
title: Configurer la hiérarchisation HDFS
titleSuffix: SQL Server big data clusters
description: Cet article explique comment configurer la hiérarchisation HDFS pour monter un système de fichiers Azure Data Lake Storage externe dans HDFS sur un cluster SQL Server 2019 Big Data (version préliminaire).
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 17eedf9f0797a0adb5eda6ca8ee090fc762e1491
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419376"
---
# <a name="configure-hdfs-tiering-on-sql-server-big-data-clusters"></a>Configurer la hiérarchisation HDFS sur les clusters Big Data SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

La hiérarchisation HDFS offre la possibilité de monter un système de fichiers externe et compatible HDFS dans HDFS. Cet article explique comment configurer la hiérarchisation HDFS pour les clusters SQL Server 2019 Big Data (version préliminaire). À ce stade, nous prenons en charge la connexion à Azure Data Lake Storage Gen2 et Amazon S3. 

## <a name="hdfs-tiering-overview"></a>Vue d’ensemble de la hiérarchisation HDFS

Avec la hiérarchisation, les applications peuvent accéder en toute transparence aux données d’un grand nombre de magasins externes comme si les données se trouvent dans le HDFS local. Le montage est une opération de métadonnées, où les métadonnées qui décrivent l’espace de noms sur le système de fichiers externe sont copiées sur votre HDFS local. Ces métadonnées incluent des informations sur les répertoires et les fichiers externes, ainsi que leurs autorisations et listes de contrôle d’accès. Les données correspondantes sont copiées uniquement à la demande, lors de l’accès aux données par l’intermédiaire d’un exemple de requête. Vous pouvez désormais accéder aux données du système de fichiers externe à partir du cluster SQL Server Big Data. Vous pouvez exécuter des travaux Spark et des requêtes SQL sur ces données de la même façon que vous les exécutez sur toutes les données locales stockées dans HDFS sur le cluster.

### <a name="caching"></a>Mise en cache
Aujourd’hui, par défaut, 1% du stockage HDFS total sera réservé à la mise en cache des données montées. La mise en cache est un paramètre global sur les montages.

> [!NOTE]
> La hiérarchisation HDFS est une fonctionnalité développée par Microsoft, et une version antérieure de celle-ci a été publiée dans le cadre de la distribution de Apache Hadoop 3,1. Pour plus d’informations, [https://issues.apache.org/jira/browse/HDFS-9806](https://issues.apache.org/jira/browse/HDFS-9806) consultez pour plus d’informations.

Les sections suivantes fournissent un exemple de configuration de la hiérarchisation HDFS avec une source de données Azure Data Lake Storage Gen2.

## <a name="refresh"></a>Actualiser

La hiérarchisation HDFS prend en charge l’actualisation. Actualisez un montage existant pour la dernière capture instantanée des données distantes.

## <a name="prerequisites"></a>Prérequis

- [Cluster Big Data déployé](deployment-guidance.md)
- [Outils Big Data](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**

## <a name="mounting-instructions"></a>Instructions de montage

Nous prenons en charge la connexion à Azure Data Lake Storage Gen2 et Amazon S3. Vous trouverez des instructions sur la façon de procéder à un montage sur ces types de stockage dans les articles suivants:

- [Comment monter ADLS Gen2 pour la hiérarchisation HDFS dans un cluster Big Data](hdfs-tiering-mount-adlsgen2.md)
- [Comment monter la hiérarchisation S3 pour HDFS dans un cluster Big Data](hdfs-tiering-mount-s3.md)

## <a id="issues"></a> Problèmes connus et limitations

La liste suivante répertorie les problèmes connus et les limitations actuelles lors de l’utilisation de la hiérarchisation HDFS dans SQL Server Big Data clusters:

- Si le montage est bloqué dans un `CREATING` État pendant une longue période, il a probablement échoué. Dans ce cas, annulez la commande et supprimez le montage si nécessaire. Vérifiez que vos paramètres et vos informations d’identification sont corrects avant de réessayer.

- Les montages ne peuvent pas être créés sur des répertoires existants.

- Les montages ne peuvent pas être créés dans des montages existants.

- Si l’un des ancêtres du point de montage n’existe pas, ceux-ci sont créés avec les autorisations par défaut r-xr-xr-x (555).

- La création du montage peut prendre un certain temps en fonction du nombre et de la taille des fichiers montés. Pendant ce processus, les fichiers sous le montage ne sont pas visibles par les utilisateurs. Pendant la création du montage, tous les fichiers sont ajoutés à un chemin d’accès temporaire, qui prend `/_temporary/_mounts/<mount-location>`par défaut la valeur.

- La commande de création de montage est asynchrone. Une fois la commande exécutée, l’état du montage peut être vérifié pour comprendre l’état du montage.

- Lors de la création du montage, l’argument utilisé pour **--Mount-Path** est essentiellement un identificateur unique du montage. La même chaîne (y compris le «/» dans la fin, le cas échéant) doit être utilisée dans les commandes suivantes.

- Les montages sont en lecture seule. Vous ne pouvez pas créer des répertoires ou des fichiers sous un montage.

- Nous vous déconseillons de monter des répertoires et des fichiers qui peuvent changer. Une fois le montage créé, les modifications ou mises à jour apportées à l’emplacement distant ne sont pas reflétées dans le montage dans HDFS. Si des modifications se produisent dans l’emplacement distant, vous pouvez choisir de supprimer et de recréer le montage pour refléter l’État mis à jour.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters SQL Server 2019 Big Data, consultez [que sont les clusters SQL Server 2019 Big Data?](big-data-cluster-overview.md).
