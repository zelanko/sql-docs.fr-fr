---
title: Configurer la hiérarchisation HDFS
titleSuffix: SQL Server big data clusters
description: Cet article explique comment configurer HDFS la hiérarchisation pour monter un système de fichiers externe Azure Data Lake Storage dans HDFS sur un cluster de données volumineuses de SQL Server 2019 (version préliminaire).
author: nelgson
ms.author: negust
ms.reviewer: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ccafa7914d09971e33d60fc9d25c7b812983aa98
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64775008"
---
# <a name="configure-hdfs-tiering-on-sql-server-big-data-clusters"></a>Configurer HDFS hiérarchisation sur les clusters de données volumineuses de SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

La hiérarchisation HDFS fournit la capacité à monter externe, le système de fichiers compatible HDFS dans HDFS. Cet article explique comment configurer HDFS réduits pour les clusters de données volumineuses de SQL Server 2019 (version préliminaire). À ce stade, nous prenons en charge de connexion à Azure Data Lake Storage Gen2 et Amazon S3. 

## <a name="hdfs-tiering-overview"></a>Vue d’ensemble de la hiérarchisation HDFS

Avec une hiérarchisation, les applications peuvent accéder en toute transparence les données dans un large éventail de magasins externes comme si les données résident dans le stockage HDFS local. Le montage est une opération de métadonnées, où les métadonnées qui décrivent l’espace de noms sur le système de fichiers externe sont copiée dans votre stockage HDFS local. Ces métadonnées incluent des informations sur les répertoires externes et les fichiers, ainsi que leurs autorisations et les ACL. Les données correspondantes sont uniquement copié à la demande, lorsque les données lui-même sont accessible via par exemple une requête. Les données de système de fichiers externe sont maintenant accessible à partir du cluster de données volumineuses de SQL Server. Vous pouvez exécuter Spark travaux et des requêtes SQL sur ces données dans la même façon que les exécuter sur toutes les données locales stockées dans HDFS sur le cluster.

### <a name="caching"></a>Mise en cache
Aujourd'hui, par défaut, 1 % du stockage HDFS total est réservée pour la mise en cache de données montés. La mise en cache est un paramètre global entre les montages.

> [!NOTE]
> HDFS la hiérarchisation est une fonctionnalité développée par Microsoft, et une version antérieure de celui-ci a été publiée dans le cadre de la distribution d’Apache Hadoop 3.1. Pour plus d’informations, consultez [ https://issues.apache.org/jira/browse/HDFS-9806 ](https://issues.apache.org/jira/browse/HDFS-9806) pour plus d’informations.

Les sections suivantes fournissent un exemple de configuration HDFS la hiérarchisation avec une source de données Azure Data Lake Storage Gen2.

## <a name="prerequisites"></a>Prérequis

- [Cluster de données volumineux déployé](deployment-guidance.md)
- [Outils de données volumineuses](deploy-big-data-tools.md)
  - **mssqlctl**
  - **kubectl**

## <a name="mounting-instructions"></a>Instructions de montage

Nous prenons en charge la connexion à Azure Data Lake Storage Gen2 et Amazon S3. Vous trouverez des instructions sur la procédure de montage par rapport à ces types de stockage dans les articles suivants :

- [Comment Gen2 ADLS de montage de fichiers HDFS la hiérarchisation d’un cluster de données volumineuses](hdfs-tiering-mount-adlsgen2.md)
- [Comment S3 de montage de fichiers HDFS la hiérarchisation d’un cluster de données volumineuses](hdfs-tiering-mount-s3.md)

## <a id="issues"></a> Limitations et problèmes connus

La liste suivante fournit les problèmes connus et limitations actuelles lors de l’utilisation de HDFS la hiérarchisation dans les clusters de données volumineuses de SQL Server :

- Si le montage est bloqué dans un `CREATING` état pendant une longue période, il a probablement échoué. Dans ce cas, annuler la commande et supprimer le montage si nécessaire. Vérifiez que vos paramètres et les informations d’identification sont correctes avant de réessayer.

- Montages ne peut pas être créés dans les répertoires existants.

- Impossible de créer les montages au sein de montages existants.

- Si un des ancêtres du point de montage n’existent pas, ils seront créés avec les autorisations par défaut la valeur r-xr-xr-x (555).

- La création de montage peut prendre un certain temps selon le nombre et la taille des fichiers qui est monté. Pendant ce processus, les fichiers sous le montage ne sont pas visibles aux utilisateurs. Pendant la création, le montage tous les fichiers seront ajoutés à un chemin d’accès temporaire, qui utilise par défaut `/_temporary/_mounts/<mount-location>`.

- La commande de création de montage est asynchrone. Une fois que la commande est exécutée, l’état de montage peut être vérifié à comprendre l’état du montage.

- Lorsque vous créez le montage, l’argument utilisé pour **--chemin de montage** est essentiellement un identificateur unique du montage. La même chaîne (y compris la « / » en fin de compte, le cas échéant) doit être utilisée dans les commandes suivantes.

- Les montages sont en lecture seule. Impossible de créer les répertoires ou les fichiers sous un montage.

- Nous ne recommandons pas de fichiers et répertoires de montage qui peuvent changer. Une fois le montage est créé, les modifications ou les mises à jour vers l’emplacement distant seront répercutées dans le montage dans HDFS. Si les modifications se produisent dans l’emplacement distant, vous pouvez choisir de supprimer et recréer le montage pour refléter l’état mis à jour.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses de SQL Server 2019, consultez [que sont les clusters de données volumineuses de SQL Server 2019 ?](big-data-cluster-overview.md).
