---
title: Notes de publication
titleSuffix: SQL Server big data clusters
description: Cet article décrit les dernières mises à jour et les problèmes connus relatifs aux clusters SQL Server 2019 Big Data (version préliminaire).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c0dd96d4a3227fda76921764429b4566e3e5dd28
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419299"
---
# <a name="release-notes-for-big-data-clusters-on-sql-server"></a>Notes de publication pour les clusters Big Data sur SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article répertorie les mises à jour et les problèmes connus pour les versions les plus récentes de SQL Server Big Data clusters.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="ctp32"></a>CTP 3,2 (juillet)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 3,2.

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Version préliminaire publique |Avant la version CTP 3,2, SQL Server Big Data cluster était disponible aux initiateurs précoces inscrits. Cette version permet à quiconque d’expérimenter les fonctionnalités de SQL Server les clusters Big Data. <br/><br/> Consultez [prise en main des clusters de Big Data SQL Server](deploy-get-started.md).|
|`azdata` |CTP 3,2 présente `azdata` un utilitaire de ligne de commande écrit en Python qui permet aux administrateurs de clusters de démarrer et de gérer le cluster Big Data via des API REST. `azdata`remplace `mssqlctl`. Consultez [installer `azdata` ](deploy-install-azdata.md). |
|PolyBase |Les noms de colonnes de table externe sont désormais utilisés pour interroger des sources de données SQL Server, Oracle, Teradata, MongoDB et ODBC. |
|Actualisation de la hiérarchisation HDFS |Présentation de la fonctionnalité d’actualisation pour la hiérarchisation HDFS afin qu’un montage existant puisse être actualisé pour la dernière capture instantanée des données distantes. Voir [Hiérarchisation HDFS](hdfs-tiering.md) |
|Résolution des problèmes basés sur Notebook |CTP 3,2 introduit les blocs-notes Jupyter pour faciliter le [déploiement](deploy-notebooks.md) et la [découverte, le diagnostic et la résolution des problèmes](manage-notebooks.md) pour les composants d’un cluster SQL Server Big Data. |
| &nbsp; | &nbsp; |

## <a id="ctp31"></a>CTP 3,1 (juin)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 3,1.

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Version préliminaire publique |Avant la version CTP 3,2, SQL Server Big Data cluster était disponible aux initiateurs précoces inscrits. Cette version permet à quiconque d’expérimenter les fonctionnalités de SQL Server les clusters Big Data. <br/><br/> Consultez [prise en main des clusters de Big Data SQL Server](deploy-get-started.md).|
|Résolution des problèmes basés sur Notebook.|CTP 3,2 introduit les blocs-notes Jupyter pour faciliter le [déploiement](deploy-notebooks.md), la [découverte, le diagnostic et la résolution des problèmes](manage-notebooks.md) pour les composants d’un cluster SQL Server Big Data. |
|`azdata` |CTP 3,2 présente `azdata` un utilitaire de ligne de commande écrit en Python qui permet aux administrateurs de clusters de démarrer et de gérer le cluster Big Data via des API REST. `azdata`remplace `mssqlctl`. Consultez [installer `azdata` ](deploy-install-azdata.md). |
|Actualisation de la hiérarchisation HDFS |Présentation de la fonctionnalité d’actualisation pour la hiérarchisation HDFS afin qu’un montage existant puisse être actualisé pour la dernière capture instantanée des données distantes. Voir [Hiérarchisation HDFS](hdfs-tiering.md) |
| &nbsp; | &nbsp; |

### <a name="whats-new"></a>What's New

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
| `mssqlctl` modifications de commande | `mssqlctl cluster` commandes ont été renommées par `mssqlctl bdc`. Pour plus d’informations, consultez la référence [`mssqlctl` ](reference-azdata.md). |
| Nouvelles `mssqlctl` commandes d’État et suppression du portail d’administration de cluster. | Le portail d’administration de cluster est supprimé de cette version. De nouvelles commandes d’État ont été `mssqlctl` ajoutées à qui complètent les commandes de surveillance existantes. |
| Pools de calcul Spark | Créer des nœuds supplémentaires afin d’augmenter la puissance de calcul Spark sans avoir à monter le stockage en puissance. En outre, vous pouvez démarrer les nœuds de pool de stockage qui ne sont pas utilisés pour Spark. Spark et stockage sont découplés. Pour plus d’informations, consultez [Configurer le stockage sans spark](deployment-custom-configuration.md#sparkstorage). |
| Connecteur Spark de MSSQL | Support de lecture/écriture aux tables externes de pool de données. Précédentes versions prises en charge en lecture/écriture pour les tables d’instance MASTER uniquement. Pour plus d’informations, consultez [Comment lire et écrire dans SQL Server à partir de Spark à l’aide du connecteur Spark MSSQL](spark-mssql-connector.md). |
| Machine Learning à l’aide de MLeap | [Former un modèle d’apprentissage automatique MLeap dans Spark et le noter dans SQL Server à l’aide de l’extension du langage Java](spark-create-machine-learning-model.md). |

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus et les limitations de cette version.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut s’afficher:

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo en Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans HDFS-site. xml ne sont pas prises en charge.

#### <a name="deployment"></a>Déploiement

- La mise à niveau d’un cluster de données Big Data à partir d’une version précédente n’est pas prise en charge.

   > [!IMPORTANT]
   > Vous devez sauvegarder vos données, puis supprimer votre cluster de Big Data existant (à l’aide de la version précédente de **azdata**) avant de déployer la dernière version. Pour plus d’informations, consultez [mettre à niveau vers une nouvelle version](deployment-upgrade.md).

- Après le déploiement sur AKS, vous pouvez voir les deux événements d’avertissement suivants du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner l’échec d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="external-tables"></a>Tables externes

- Le déploiement de cluster Big Data ne crée plus les sources de données externes **SqlDataPool** et **SqlStoragePool** . Vous pouvez créer ces sources de données manuellement pour prendre en charge la virtualisation des données dans le pool de données et le pool de stockage.

   > [!NOTE]
   > L’URI pour la création de ces sources de données externes est différent entre les CTP. Pour savoir comment les créer, consultez les commandes Transact-SQL ci-dessous. 

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://controller-svc/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://controller-svc/default');
   ```

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Si vous créez une table externe dans Oracle qui utilise des types de données caractères, l’Assistant Azure Data Studio Virtualization interprète ces colonnes comme VARCHAR dans la définition de la table externe. Cela entraînera un échec dans la DDL de table externe. Modifiez le schéma Oracle pour utiliser le type NVARCHAR2 ou créez des instructions de TABLE externe manuellement et spécifiez NVARCHAR au lieu d’utiliser l’Assistant.

#### <a name="application-deployment"></a>Déploiement d'applications

- Lors de l’appel d’une application R, Python ou MLeap à partir de l’API RESTful, l’appel expire en 5 minutes.

#### <a name="spark-and-notebooks"></a>Spark et Notebooks

- Les adresses IP POD peuvent changer dans l’environnement Kubernetes lors du redémarrage de Pod. Dans le scénario dans lequel le maître-Pod redémarre, la session Spark peut échouer `NoRoteToHostException`avec. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un python distinct sur Windows, les blocs-notes Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un bloc-notes, si vous cliquez sur la commande **Ajouter du texte** , la cellule de texte est ajoutée en mode aperçu plutôt que en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier de vidage de câble). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [modifier le mot de passe sa](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe SA pour les déploiements de cluster Big Data.

#### <a name="kibana-logs-dashboards"></a>Tableaux de bord Kibana logs

- Entre Aris CTP 3,0 et 3,1, la version de Kibana a été mise à niveau de 6.3.1 à 7.0.1.  Le navigateur Edge n’est pas compatible avec Kibana. Les utilisateurs verront une page vierge lors du chargement de la version actuelle des tableaux de bord Kibana dans Edge. Voir [ici]( https://www.elastic.co/support/matrix#matrix_browse) pour les navigateurs pris en charge pour Kibana.RS 


## <a id="ctp30"></a>CTP 3,0 (mai)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 3,0.

### <a name="whats-new"></a>What's New

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
| **mssqlctl** updates | Plusieurs [mises à jour de commande et de paramètre](reference-azdata.md) **mssqlctl**. Ces dernières incluent une mise à jour de la commande **mssqlctl login**, qui cible désormais le nom d’utilisateur et le point de terminaison du contrôleur. |
| Améliorations du stockage | Prise en charge de différentes configurations de stockage pour les journaux et les données. En outre, le nombre de revendications de volume persistant pour un cluster Big Data a été réduit. |
| Plusieurs instances de pool de calcul | Prise en charge de plusieurs instances de pool de calcul. |
| Nouveaux comportement et fonctionnalités pour les pools | Le pool de calcul est maintenant utilisé par défaut pour les opérations de pool de données et de pool de stockage dans une distribution **ROUND_ROBIN** uniquement. Le pool de données peut désormais utiliser un nouveau type de distribution **REPLICATED**, ce qui signifie que les mêmes données sont présentes sur toutes les instances de pool de données. |
| Améliorations des tables externes | Les tables externes de type de source de données HADOOP prennent maintenant en charge la lecture des lignes d’une taille maximale de 1 Mo. Dans les tables externes (ODBC, pool de stockage, pool de données), les lignes peuvent désormais être aussi larges que dans une table SQL Server. |

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus et les limitations de cette version.

#### <a name="hdfs"></a>HDFS

- Azure Data Studio retourne une erreur lorsque vous tentez de créer un nouveau dossier dans HDFS. Pour activer cette fonctionnalité, installez la build Insiders de Azure Data Studio:
  
   - [Programme d’installation d’utilisateur Windows- **version** Insiders](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-user/insider)
   - [Programme d’installation du système Windows- **version** Insiders](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64/insider)
   - [**Génération** de code postal Windows](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-archive/insider)
   - [**génération** de code zip-Insider MacOS](https://azuredatastudio-update.azurewebsites.net/latest/darwin/insider)
   - [TAR Linux. **Version** gz-Insiders](https://azuredatastudio-update.azurewebsites.net/latest/linux-x64/insider)

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut s’afficher:

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo en Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans HDFS-site. xml ne sont pas prises en charge.

#### <a name="deployment"></a>Déploiement

- Les procédures de déploiement précédentes pour les clusters Big Data compatibles GPU ne sont pas prises en charge dans la version CTP 3,0. Une autre procédure de déploiement est en cours d’examen. Pour l’instant, l’article «déployer un cluster Big Data avec prise en charge GPU et exécuter TensorFlow» a été temporairement annulé pour éviter toute confusion.

- La mise à niveau d’un cluster de données Big Data à partir d’une version précédente n’est pas prise en charge.

   > [!IMPORTANT]
   > Vous devez sauvegarder vos données, puis supprimer votre cluster de Big Data existant (à l’aide de la version précédente de **azdata**) avant de déployer la dernière version. Pour plus d’informations, consultez [mettre à niveau vers une nouvelle version](deployment-upgrade.md).

- Après le déploiement sur AKS, vous pouvez voir les deux événements d’avertissement suivants du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner l’échec d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="external-tables"></a>Tables externes

- Le déploiement de cluster Big Data ne crée plus les sources de données externes **SqlDataPool** et **SqlStoragePool** . Vous pouvez créer ces sources de données manuellement pour prendre en charge la virtualisation des données dans le pool de données et le pool de stockage.

   > [!NOTE]
   > L’URI pour la création de ces sources de données externes est différent entre les CTP. Pour savoir comment les créer, consultez les commandes Transact-SQL ci-dessous. 

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://controller-svc/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://controller-svc/default');
   ```

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Si vous créez une table externe dans Oracle qui utilise des types de données caractères, l’Assistant Azure Data Studio Virtualization interprète ces colonnes comme VARCHAR dans la définition de la table externe. Cela entraînera un échec dans la DDL de table externe. Modifiez le schéma Oracle pour utiliser le type NVARCHAR2 ou créez des instructions de TABLE externe manuellement et spécifiez NVARCHAR au lieu d’utiliser l’Assistant.

#### <a name="application-deployment"></a>Déploiement d'applications

- Lors de l’appel d’une application R, Python ou MLeap à partir de l’API RESTful, l’appel expire en 5 minutes.

#### <a name="spark-and-notebooks"></a>Spark et Notebooks

- Les adresses IP POD peuvent changer dans l’environnement Kubernetes lors du redémarrage de Pod. Dans le scénario dans lequel le maître-Pod redémarre, la session Spark peut échouer `NoRoteToHostException`avec. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un python distinct sur Windows, les blocs-notes Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un bloc-notes, si vous cliquez sur la commande **Ajouter du texte** , la cellule de texte est ajoutée en mode aperçu plutôt que en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier de vidage de câble). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [modifier le mot de passe sa](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe SA pour les déploiements de cluster Big Data.

## <a id="ctp25"></a>CTP 2,5 (avril)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 2,5.

### <a name="whats-new"></a>What's New

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
| Profils de déploiement | Utilisent des [fichiers JSON de configuration du déploiement](deployment-guidance.md#configfile) par défaut et personnalisés pour les déploiements de clusters big data au lieu de variables d’environnement. |
| Déploiements demandés | `azdata cluster create` demande désormais à l’utilisateur de saisir les paramètres requis pour les déploiements par défaut. |
| Changements de point de terminaison de service et de nom de pod | Les points de terminaison externes suivants ont des noms modifiés:<br/>&nbsp;&nbsp;&nbsp;- **endpoint-master-pool** => **master-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-controller** => **controller-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-service-proxy** => **mgmtproxy-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-security** => **gateway-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-app-service-proxy** => **appproxy-svc-external**|
| améliorations apportées à **azdata** | Utilisez **azdata** pour [répertorier les points de terminaison externes](deployment-guidance.md#endpoints) et vérifier la version de `--version` **azdata** avec le paramètre. |
| Installation hors connexion | Aide pour les déploiements de cluster Big Data hors connexion. |
| Améliorations concernant la hiérarchisation HDFS | La hiérarchisation S3, la mise en cache du montage et la prise en charge OAuth pour ADLS Gen2. |
| Nouveau `mssql` connecteur Spark-SQL Server | |

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus et les limitations de cette version.

#### <a name="deployment"></a>Déploiement

- La mise à niveau d’un cluster de données Big Data à partir d’une version précédente n’est pas prise en charge.

   > [!IMPORTANT]
   > Vous devez sauvegarder vos données, puis supprimer votre cluster de Big Data existant (à l’aide de la version précédente de **azdata**) avant de déployer la dernière version. Pour plus d’informations, consultez [mettre à niveau vers une nouvelle version](deployment-upgrade.md).

- Après le déploiement sur AKS, vous pouvez voir les deux événements d’avertissement suivants du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner l’échec d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="external-tables"></a>Tables externes

- Le déploiement de cluster Big Data ne crée plus les sources de données externes **SqlDataPool** et **SqlStoragePool** . Vous pouvez créer ces sources de données manuellement pour prendre en charge la virtualisation des données dans le pool de données et le pool de stockage.

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://nmnode-0-svc:50070');
   ```

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Si vous créez une table externe dans Oracle qui utilise des types de données caractères, l’Assistant Azure Data Studio Virtualization interprète ces colonnes comme VARCHAR dans la définition de la table externe. Cela entraînera un échec dans la DDL de table externe. Modifiez le schéma Oracle pour utiliser le type NVARCHAR2 ou créez des instructions de TABLE externe manuellement et spécifiez NVARCHAR au lieu d’utiliser l’Assistant.

#### <a name="application-deployment"></a>Déploiement d'applications

- Lors de l’appel d’une application R, Python ou MLeap à partir de l’API RESTful, l’appel expire en 5 minutes.

#### <a name="spark-and-notebooks"></a>Spark et Notebooks

- Les adresses IP POD peuvent changer dans l’environnement Kubernetes lors du redémarrage de Pod. Dans le scénario dans lequel le maître-Pod redémarre, la session Spark peut échouer `NoRoteToHostException`avec. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un python distinct sur Windows, les blocs-notes Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un bloc-notes, si vous cliquez sur la commande **Ajouter du texte** , la cellule de texte est ajoutée en mode aperçu plutôt que en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut s’afficher:

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo en Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans HDFS-site. xml ne sont pas prises en charge.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier de vidage de câble). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [modifier le mot de passe sa](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe SA pour les déploiements de cluster Big Data.

## <a id="ctp24"></a>CTP 2,4 (mars)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 2,4.

### <a name="whats-new"></a>What's New

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
| Conseils sur la prise en charge de GPU pour l’exécution de Deep Learning avec TensorFlow dans Spark. | [Déploie un cluster de Big Data avec prise en charge du GPU et exécute TensorFlow](spark-gpu-tensorflow.md). |
| Les sources de données **SqlDataPool** et **SqlStoragePool** ne sont plus créées par défaut. | Créez-les manuellement si besoin. Passer en revue les [problèmes connus](#externaltablesctp24). |
| Prise en charge d’`INSERT INTO SELECT` pour le pool de données. | Pour obtenir un exemple, consultez [Tutoriel : Recevoir des données dans un pool de données SQL Server avec Transact-SQL](tutorial-data-pool-ingest-sql.md). |
| Options `FORCE SCALEOUTEXECUTION` et `DISABLE SCALEOUTEXECUTION`. | Force ou désactive l’utilisation du pool de calcul pour les requêtes sur les tables externes. Par exemple, `SELECT TOP(100) * FROM web_clickstreams_hdfs_book_clicks OPTION(FORCE SCALEOUTEXECUTION)`. |
| Recommandations pour le déploiement d’AKS mises à jour. | Lorsque vous évaluez les clusters de Big Data sur AKS, nous recommandons à présent d’utiliser un seul nœud de taille **Standard_L8s**. |
| Mise à niveau du runtime Spark vers Spark 2.4. | |

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus et les limitations de cette version.

#### <a name="deployment"></a>Déploiement

- La mise à niveau d’un cluster de données Big Data à partir d’une version précédente n’est pas prise en charge.

   > [!IMPORTANT]
   > Vous devez sauvegarder vos données, puis supprimer votre cluster de Big Data existant (à l’aide de la version précédente de **azdata**) avant de déployer la dernière version. Pour plus d’informations, consultez [mettre à niveau vers une nouvelle version](deployment-upgrade.md).

- Après le déploiement sur AKS, vous pouvez voir les deux événements d’avertissement suivants du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner l’échec d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="kubeadm-deployments"></a>déploiements kubeadm

Si vous utilisez kubeadm pour déployer des Kubernetes sur plusieurs ordinateurs, le portail d’administration de cluster n’affiche pas correctement les points de terminaison nécessaires pour se connecter au cluster Big Data. Si vous rencontrez ce problème, utilisez la solution de contournement suivante pour découvrir les adresses IP des points de terminaison de service:

- Si vous vous connectez à partir du cluster, interrogez Kubernetes pour obtenir l’adresse IP du point de terminaison auquel vous souhaitez vous connecter. Par exemple, la commande **kubectl** suivante affiche l’adresse IP de l’instance principale SQL Server:

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Si vous vous connectez en dehors du cluster, procédez comme suit pour vous connecter:

   1. Récupérez l’adresse IP du nœud qui exécute l’instance maître SQL Server `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`:.

   1. Connectez-vous à SQL Server instance principale à l’aide de cette adresse IP.

   1. Interrogez le **cluster_endpoint_table** dans la base de données Master pour d’autres points de terminaison externes.

      En cas d’échec avec un délai de connexion, il est possible que le nœud respectif soit pare-feu. Dans ce cas, vous devez contacter votre administrateur de cluster Kubernetes et demander l’adresse IP du nœud exposée en externe. Il peut s’agir de n’importe quel nœud. Vous pouvez ensuite utiliser cette adresse IP et le port correspondant pour vous connecter à différents services exécutés dans le cluster. Par exemple, l’administrateur peut trouver cette adresse IP en exécutant:

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a name="delete-cluster-fails"></a>Échec de la suppression du cluster

Lorsque vous essayez de supprimer un cluster avec **azdata**, il échoue avec l’erreur suivante:

```
2019-03-26 20:38:11.0614 UTC | INFO | Deleting cluster ...
Error processing command: "TypeError"
delete_namespaced_service() takes 3 positional arguments but 4 were given
Makefile:61: recipe for target 'delete-cluster' failed
make[2]: *** [delete-cluster] Error 1
Makefile:223: recipe for target 'deploy-clean' failed
make[1]: *** [deploy-clean] Error 2
Makefile:203: recipe for target 'deploy-clean' failed
make: *** [deploy-clean] Error 2
```

Un nouveau client python Kubernetes (version 9.0.0) a modifié l’API de suppression des espaces de noms, qui interrompt actuellement **azdata**. Cela se produit uniquement si un client python Kubernetes plus récent est installé. Vous pouvez contourner ce problème en supprimant directement le cluster  à l'`kubectl delete ns <ClusterName>`aide de kubectl (), ou vous pouvez installer `sudo pip install kubernetes==8.0.1`l’ancienne version à l’aide de.

#### <a id="externaltablesctp24"></a>Tables externes

- Le déploiement de cluster Big Data ne crée plus les sources de données externes **SqlDataPool** et **SqlStoragePool** . Vous pouvez créer ces sources de données manuellement pour prendre en charge la virtualisation des données dans le pool de données et le pool de stockage.

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://service-master-pool:50070');
   ```

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Si vous créez une table externe dans Oracle qui utilise des types de données caractères, l’Assistant Azure Data Studio Virtualization interprète ces colonnes comme VARCHAR dans la définition de la table externe. Cela entraînera un échec dans la DDL de table externe. Modifiez le schéma Oracle pour utiliser le type NVARCHAR2 ou créez des instructions de TABLE externe manuellement et spécifiez NVARCHAR au lieu d’utiliser l’Assistant.

#### <a name="application-deployment"></a>Déploiement d'applications

- Lors de l’appel d’une application R, Python ou MLeap à partir de l’API RESTful, l’appel expire en 5 minutes.

#### <a name="spark-and-notebooks"></a>Spark et Notebooks

- Les adresses IP POD peuvent changer dans l’environnement Kubernetes lors du redémarrage de Pod. Dans le scénario dans lequel le maître-Pod redémarre, la session Spark peut échouer `NoRoteToHostException`avec. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un python distinct sur Windows, les blocs-notes Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un bloc-notes, si vous cliquez sur la commande **Ajouter du texte** , la cellule de texte est ajoutée en mode aperçu plutôt que en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut s’afficher:

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo en Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans HDFS-site. xml ne sont pas prises en charge.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier de vidage de câble). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [modifier le mot de passe sa](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe SA pour les déploiements de cluster Big Data.

## <a id="ctp23"></a>CTP 2,3 (février)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 2,3.

### <a name="whats-new"></a>What's New

| Nouvelle fonctionnalité ou mise à jour | Détails |
| :---------- | :------ |
| Envoyer des travaux Spark sur des clusters Big Data dans IntelliJ. | [Envoie des travaux Spark sur des clusters Big Data SQL Server dans IntelliJ](spark-submit-job-intellij-tool-plugin.md) |
| CLI courantes pour la gestion des clusters et le déploiement des applications. | [Comment déployer une application sur un cluster Big Data de SQL Server 2019 (préversion)](big-data-cluster-create-apps.md) |
| Extension de VS Code pour déployer des applications sur un cluster de Big Data. | [Comment utiliser VS Code pour déployer des applications sur les clusters Big Data de SQL Server](app-deployment-extension.md) |
| Modifications apportées à l’utilisation de la commande de l’outil **azdata** . | Pour plus d’informations, consultez les [problèmes connus pour azdata](#azdatactp23). |
| Utiliser Sparklyr dans Big Data cluster | [Utiliser Sparklyr dans des clusters Big Data SQL Server 2019](sparklyr-from-RStudio.md) |
| Monter un stockage compatible HDFS externe dans le cluster Big Data avec une **hiérarchisation HDFS**. | Consultez [Hiérarchisation HDFS](hdfs-tiering.md). |
| Nouvelle expérience de connexion unifiée pour l’instance principale de SQL Server et la passerelle HDFS/Spark. | Consultez [Instance principale de SQL Server et passerelle HDFS/Spark](connect-to-big-data-cluster.md). |
| La suppression d’un cluster avec la **suppression du cluster azdata** supprime désormais uniquement les objets de l’espace de noms qui faisaient partie du cluster Big Data. | L’espace de noms n’est pas supprimé. Toutefois, dans les versions antérieures, cette commande supprimait l’espace de noms dans son intégralité. |
| Les noms de point de terminaison de _Sécurité_ ont été modifiés et consolidés. | **service-security-lb** et **service-security-nodeport** ont été consolidés dans le point de terminaison **endpoint-security**. |
| Les noms de point de terminaison de _Proxy_ ont été modifiés et consolidés. | **service-proxy-lb** et **service-proxy-nodeport** ont été consolidés dans le point de terminaison **endpoint-service-proxy**. |
| Les noms de point de terminaison de _Contrôleur_ ont été modifiés et consolidés. | **service-mssql-controller-lb** et **service-mssql-controller-nodeport** ont été consolidés dans le point de terminaison **endpoint-controller**. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus et les limitations de cette version.

#### <a name="deployment"></a>Déploiement

- La mise à niveau d’un cluster de données Big Data à partir d’une version précédente n’est pas prise en charge.

   > [!IMPORTANT]
   > Vous devez sauvegarder vos données, puis supprimer votre cluster de Big Data existant (à l’aide de la version précédente de **azdata**) avant de déployer la dernière version. Pour plus d’informations, consultez [mettre à niveau vers une nouvelle version](deployment-upgrade.md).

- La variable d’environnement **ACCEPT_EULA** doit être «oui» ou «Oui» pour accepter le CLUF. Les versions précédentes autorisaient «y» et «Y», mais celles-ci ne sont plus acceptées et entraînera l’échec du déploiement.

- Les variables d’environnement **CLUSTER_PLATFORM** n’ont pas de valeur par défaut comme c’était le cas dans les versions précédentes.

- Après le déploiement sur AKS, vous pouvez voir les deux événements d’avertissement suivants du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner l’échec d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="kubeadm-deployments"></a>déploiements kubeadm

Si vous utilisez kubeadm pour déployer des Kubernetes sur plusieurs ordinateurs, le portail d’administration de cluster n’affiche pas correctement les points de terminaison nécessaires pour se connecter au cluster Big Data. Si vous rencontrez ce problème, utilisez la solution de contournement suivante pour découvrir les adresses IP des points de terminaison de service:

- Si vous vous connectez à partir du cluster, interrogez Kubernetes pour obtenir l’adresse IP du point de terminaison auquel vous souhaitez vous connecter. Par exemple, la commande **kubectl** suivante affiche l’adresse IP de l’instance principale SQL Server:

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Si vous vous connectez en dehors du cluster, procédez comme suit pour vous connecter:

   1. Récupérez l’adresse IP du nœud qui exécute l’instance maître SQL Server `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`:.

   1. Connectez-vous à SQL Server instance principale à l’aide de cette adresse IP.

   1. Interrogez le **cluster_endpoint_table** dans la base de données Master pour d’autres points de terminaison externes.

      En cas d’échec avec un délai de connexion, il est possible que le nœud respectif soit pare-feu. Dans ce cas, vous devez contacter votre administrateur de cluster Kubernetes et demander l’adresse IP du nœud exposée en externe. Il peut s’agir de n’importe quel nœud. Vous pouvez ensuite utiliser cette adresse IP et le port correspondant pour vous connecter à différents services exécutés dans le cluster. Par exemple, l’administrateur peut trouver cette adresse IP en exécutant:

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a id="azdatactp23"></a>azdata

- L’outil **azdata** est passé d’un ordre de commande Verb-substantif à un ordre de verbe substantif. Par exemple, `azdata create cluster` est maintenant `azdata cluster create`.

- Le `--name` paramètre est désormais requis lors de la création d' `azdata cluster create`un cluster avec.

   ```bash
   azdata cluster create --name <cluster_name>
   ```

- Pour obtenir des informations importantes sur la mise à niveau vers la dernière version de Big Data clusters et **azdata**, consultez [mise à niveau vers une nouvelle version](deployment-upgrade.md).

#### <a name="external-tables"></a>Tables externes

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Si vous créez une table externe dans Oracle qui utilise des types de données caractères, l’Assistant Azure Data Studio Virtualization interprète ces colonnes comme VARCHAR dans la définition de la table externe. Cela entraînera un échec dans la DDL de table externe. Modifiez le schéma Oracle pour utiliser le type NVARCHAR2 ou créez des instructions de TABLE externe manuellement et spécifiez NVARCHAR au lieu d’utiliser l’Assistant.

#### <a name="application-deployment"></a>Déploiement d'applications

- Lors de l’appel d’une application R, Python ou MLeap à partir de l’API RESTful, l’appel expire en 5 minutes.

#### <a name="spark-and-notebooks"></a>Spark et Notebooks

- Les adresses IP POD peuvent changer dans l’environnement Kubernetes lors du redémarrage de Pod. Dans le scénario dans lequel le maître-Pod redémarre, la session Spark peut échouer `NoRoteToHostException`avec. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un python distinct sur Windows, les blocs-notes Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un bloc-notes, si vous cliquez sur la commande **Ajouter du texte** , la cellule de texte est ajoutée en mode aperçu plutôt que en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut s’afficher:

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo en Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans HDFS-site. xml ne sont pas prises en charge.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier de vidage de câble). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [modifier le mot de passe sa](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe SA pour les déploiements de cluster Big Data.

## <a id="ctp22"></a>CTP 2,2 (2018 décembre)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 2,2.

### <a name="new-features"></a>Nouvelles fonctionnalités

- Portail d’administration de cluster `/portal` accessible avec ( **\<https://IP\>-Address: 30777/Portal**).
- Le nom du service du pool `service-master-pool-lb` principal `service-master-pool-nodeport` est `endpoint-master-pool`passé de et à.
- Nouvelle version de **azdata** et d’images mises à jour.
- Améliorations et résolutions de bogues diverses.

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus et les limitations de cette version.

#### <a name="deployment"></a>Déploiement

- La mise à niveau d’un cluster de données Big Data à partir d’une version précédente n’est pas prise en charge. Vous devez sauvegarder et supprimer tout cluster Big Data existant avant de déployer la dernière version. Pour plus d’informations, consultez [mettre à niveau vers une nouvelle version](deployment-upgrade.md).

- Après le déploiement sur AKS, vous pouvez voir les deux événements d’avertissement suivants du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner l’échec d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="cluster-administration-portal"></a>Portail d’administration du cluster

Le portail d’administration de cluster n’affiche pas le point de terminaison de l’instance maître SQL Server. Pour trouver l’adresse IP et le port de l’instance principale, utilisez la commande **kubectl** suivante:

```
kubectl get svc endpoint-master-pool -n <your-big-data-cluster-name>
```

#### <a name="external-tables"></a>Tables externes

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark et Notebooks

- Les adresses IP POD peuvent changer dans l’environnement Kubernetes lors du redémarrage de Pod. Dans le scénario dans lequel le maître-Pod redémarre, la session Spark peut échouer `NoRoteToHostException`avec. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un python distinct sur Windows, les blocs-notes Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un bloc-notes, si vous cliquez sur la commande **Ajouter du texte** , la cellule de texte est ajoutée en mode aperçu plutôt que en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut s’afficher:

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo en Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans HDFS-site. xml ne sont pas prises en charge.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier de vidage de câble). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [modifier le mot de passe sa](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe SA pour les déploiements de cluster Big Data.

## <a id="ctp21"></a>CTP 2,1 (2018 novembre)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 2,1.

### <a name="new-features"></a>Nouvelles fonctionnalités

- [Déployez des applications python et R](big-data-cluster-create-apps.md) dans un cluster Big Data.
- Nouvelle version de **azdata** et d’images mises à jour. 
- Améliorations et résolutions de bogues diverses.

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes fournissent des problèmes connus pour SQL Server Big Data clusters dans la version CTP 2,1.

#### <a name="deployment"></a>Déploiement

- La mise à niveau d’un cluster de données Big Data à partir d’une version précédente n’est pas prise en charge. Vous devez sauvegarder et supprimer tout cluster Big Data existant avant de déployer la dernière version. Pour plus d’informations, consultez [mettre à niveau vers une nouvelle version](deployment-upgrade.md).

- Après le déploiement sur AKS, vous pouvez voir les deux événements d’avertissement suivants du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner l’échec d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="admin-portal"></a>Portail d’administration

- Lorsque vous [créez une application à l’aide de la commande msqlctl-CTP](big-data-cluster-create-apps.md) et que vous la déployez sur un cluster SQL Server Big Data, le portail d’administration du cluster affiche les Pod où l’application a été déployée comme «inconnue» dans la section contrôleur de la partie administrateur.

#### <a name="external-tables"></a>Tables externes

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark et Notebooks

- Les adresses IP POD peuvent changer dans l’environnement Kubernetes lors du redémarrage de Pod. Dans le scénario dans lequel le maître-Pod redémarre, la session Spark peut échouer `NoRoteToHostException`avec. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un python distinct sur Windows, les blocs-notes Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un bloc-notes, si vous cliquez sur la commande **Ajouter du texte** , la cellule de texte est ajoutée en mode aperçu plutôt que en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut s’afficher:

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo en Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans HDFS-site. xml ne sont pas prises en charge.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier de vidage de câble). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [modifier le mot de passe sa](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe SA pour les déploiements de cluster Big Data.

## <a id="ctp20"></a>CTP 2,0 (octobre 2018)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 2,0.

### <a name="new-features"></a>Nouvelles fonctionnalités

- Expérience de déploiement simple à l’aide de l’outil de gestion azdata
- Expérience du bloc-notes native dans Azure Data Studio
- Interroger les fichiers HDFS via l’instance de stockage de SQL Server
- Virtualisation des données via Master pour SQL Server, Oracle, MongoDB et HDFS
- Assistant virtualisation des données pour SQL Server et Oracle dans Azure Data Studio
- Services ML sur le maître
- Portail d’administration de cluster que vous pouvez utiliser pour la surveillance et le dépannage
- Envoi de la tâche Spark dans Azure Data Studio 
- Interface utilisateur Spark dans le portail d’administration du cluster
- Montage du volume sur les classes de stockage
- Requêtes sur les pools de données à partir de Master
- Afficher le plan des requêtes distribuées dans SSMS
- Package PIP pour l’outil de gestion azdata
- Moteur de déploiement intégré via le service de contrôleur

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes fournissent des problèmes connus pour SQL Server Big Data clusters dans la version CTP 2,0.

#### <a name="deployment"></a>Déploiement

- Si vous utilisez Azure Kubernetes service (AKS), la version recommandée de Kubernetes est 1,10. *, qui ne prend pas en charge le redimensionnement de disque. Vous devez vous assurer que vous dimensionnez le stockage en conséquence au moment du déploiement. Pour plus d’informations sur la façon d’ajuster les tailles de stockage, consultez l’article sur la persistance des [données](concept-data-persistence.md) . Pour les Kubernetes déployés sur des machines virtuelles, la version recommandée est 1,11.

- Après le déploiement sur AKS, vous pouvez voir les deux événements d’avertissement suivants du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner l’échec d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="external-tables"></a>Tables externes

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark et Notebooks

- Les adresses IP POD peuvent changer dans l’environnement Kubernetes lors du redémarrage de Pod. Dans le scénario dans lequel le maître-Pod redémarre, la session Spark peut échouer `NoRoteToHostException`avec. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un python distinct sur Windows, les blocs-notes Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un bloc-notes, si vous cliquez sur la commande **Ajouter du texte** , la cellule de texte est ajoutée en mode aperçu plutôt que en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut s’afficher:

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo en Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans HDFS-site. xml ne sont pas prises en charge.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier de vidage de câble). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [modifier le mot de passe sa](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe SA pour les déploiements de cluster Big Data.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data SQL Server, consultez [que sont les clusters Big Data SQL Server 2019?](big-data-cluster-overview.md).
