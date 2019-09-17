---
title: Notes de publication
titleSuffix: SQL Server big data clusters
description: Cet article décrit les dernières mises à jour et les problèmes connus [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] pour (version préliminaire).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bcbc3537a6ba26dc907bf348c565939ff869ea43
ms.sourcegitcommit: da8bb7abd256b2bebee7852dc0164171eeff11be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988095"
---
# <a name="release-notes-for-sql-server-big-data-clusters"></a>Notes de publication pour les clusters Big Data SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article répertorie les mises à jour et les problèmes connus pour les versions les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]plus récentes de.

## <a id="rc"></a>Version Release Candidate (août)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server version Release candidate 2019.

### <a name="whats-new"></a>What's New

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|SQL Server Always On groupe de disponibilité |Lorsque vous déployez un cluster SQL Server Big Data, vous pouvez configurer le déploiement pour créer un groupe de disponibilité à fournir :<br/><br/>-Haute disponibilité <br/><br/>-Lecture-montée en puissance parallèle <br/><br/>-Insertion de données avec montée en puissance parallèle dans le pool de données<br/><br>Consultez [déployer avec une haute disponibilité](../big-data-cluster/deployment-high-availability.md). |
|`azdata` |Installation simplifiée de l’outil avec le [Gestionnaire d’installation](./deploy-install-azdata-linux-package.md)<br/><br/>[`azdata notebook`commande](./reference-azdata-notebook.md)<br/><br/>[`azdata bdc status`commande](./reference-azdata-bdc-status.md) |
|Azure Data Studio|[Téléchargez la version Release candidate de Azure Data Studio](deploy-big-data-tools.md#download-and-install-azure-data-studio-sql-server-2019-release-candidate-rc).<br/><br/>Ajout de bloc-notes pour la résolution des problèmes via 2019 SQL Server livre Jupyter guide.<br/><br/>Expérience de connexion du contrôleur ajoutée.<br/><br/>Ajout d’un tableau de bord de contrôleur pour afficher les points de terminaison de service, afficher l’état d’intégrité du cluster et accéder aux blocs-notes de dépannage.<br/><br/>Amélioration des performances de sortie/modification des cellules du bloc-notes.|
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Problèmes connus

* Le numéro de build de l’actualisation des clusters de Big `15.0.1900.47`Data SQL Server 2019 est.

* Le profil de déploiement « kubeadm-prod » n’est pas pris en charge dans les clusters Big Data SQL Server 2019 avec le numéro de version ci-dessus. Au lieu de cela, utilisez le profil « kubeadm-dev-test » pour les déploiements Kubeadm.

## <a id="ctp32"></a> CTP 3.2 (juillet)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 3.2.

### <a name="whats-new"></a>What's New

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Préversion publique |Avant la version CTP 3.2, les clusters Big Data SQL Server n’étaient disponibles que pour les utilisateurs précoces inscrits. Cette version permet désormais à tout le monde d’utiliser les fonctionnalités des clusters Big Data SQL Server. <br/><br/> Consultez [prise en main [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]de ](deploy-get-started.md).|
|`azdata` |CTP 3.2 comprend `azdata`, un nouvel utilitaire de ligne de commande écrit en Python qui permet aux administrateurs de clusters de démarrer et de gérer les clusters Big Data via des API REST. `azdata` remplace `mssqlctl`. Voir [Installer `azdata`](deploy-install-azdata.md). |
|PolyBase |Les noms des colonnes de table externe sont désormais utilisés pour interroger les sources de données SQL Server, Oracle, Teradata, MongoDB et ODBC. Dans les versions CTP précédentes, les colonnes de la source de données externe étaient liées en fonction de la position ordinale uniquement et les noms spécifiés dans la définition EXTERNAL TABLE n’étaient pas utilisés. |
|Actualisation de la hiérarchisation HDFS |Nous avons ajouté une fonctionnalité d’actualisation pour la hiérarchisation HDFS afin qu’un montage existant puisse être actualisé en fonction de la dernière capture instantanée des données distantes. Voir [Hiérarchisation HDFS](hdfs-tiering.md). |
|Résolution des problèmes liés aux notebooks |La version CTP 3.2 comprend des notebooks Jupyter qui facilitent le [déploiement](deploy-notebooks.md), ainsi que la [découverte, le diagnostic et la résolution des problèmes](manage-notebooks.md) au niveau des composants des clusters Big Data SQL Server. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus et les limitations de cette version.

#### <a name="polybase"></a>PolyBase

- Un push vers le bas de la clause TOP lorsque le nombre est supérieur à 1 000 n’est pas pris en charge dans cette version. Dans ce cas, toutes les lignes sont lues à partir de la source de données distante. (Résolu dans la version Release Candidate)

- Un push vers le bas de jointures colocalisées vers des sources de données externes n’est pas pris en charge dans cette version. Par exemple, le push vers le bas de deux tables de pool de données de type de distribution ROUND_ROBIN permet d’envoyer les données à une instance SQL Master ou à une instance de pool de calcul pour effectuer l’opération de jointure.

#### <a name="compute-pool"></a>Pool de calcul

- Le déploiement de cluster Big Data ne prend en charge que le pool de calcul avec une seule instance. (Résolu dans la version Release Candidate)

#### <a name="storage-pool"></a>Pool de stockage

- L’interrogation des fichiers parquet dans le pool de stockage ne prend pas en charge certains types de données.

- Il est impossible d’interroger les colonnes parentes de mappage (MAP) et de liste (LIST), ainsi que les colonnes parentes sans type attaché. Cela retourne une erreur.

- Les nœuds RÉPÉTÉS ne peuvent pas être interrogés et peuvent retourner des résultats incorrects.

## <a id="ctp31"></a> CTP 3.1 (juin)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 3.1.

### <a name="whats-new"></a>What's New

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
| `mssqlctl` modifications de commande | `mssqlctl cluster` commandes ont été renommées par `mssqlctl bdc`. Pour plus d’informations, consultez la référence [`mssqlctl` ](reference-azdata.md). |
| Nouvelles commandes d’état `mssqlctl` et suppression du portail d’administration des clusters. | Le portail d’administration des clusters est supprimé de cette version. De nouvelles commandes d’état ont été ajoutées à `mssqlctl` pour compléter les commandes de surveillance existantes. |
| Pools de calcul Spark | Créer des nœuds supplémentaires afin d’augmenter la puissance de calcul Spark sans avoir à monter le stockage en puissance. En outre, vous pouvez démarrer les nœuds de pool de stockage qui ne sont pas utilisés pour Spark. Spark et stockage sont découplés. Pour plus d’informations, consultez [Configurer le stockage sans spark](deployment-custom-configuration.md#sparkstorage). |
| Connecteur Spark de MSSQL | Support de lecture/écriture aux tables externes de pool de données. Précédentes versions prises en charge en lecture/écriture pour les tables d’instance MASTER uniquement. Pour plus d’informations, consultez [Comment lire et écrire dans SQL Server à partir de Spark à l’aide du connecteur Spark MSSQL](spark-mssql-connector.md). |
| Machine Learning à l’aide de MLeap | [Former un modèle d’apprentissage automatique MLeap dans Spark et le noter dans SQL Server à l’aide de l’extension du langage Java](spark-create-machine-learning-model.md). |

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus et les limitations de cette version.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut apparaître :

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo dans Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans hdfs-site.xml ne sont pas prises en charge.

#### <a name="deployment"></a>Déploiement

- La mise à niveau d’un cluster de données Big Data à partir d’une version précédente n’est pas prise en charge.

   > [!IMPORTANT]
   > Vous devez sauvegarder vos données puis supprimer votre cluster Big Data existant (à l’aide de la version précédente de **azdata**) avant de déployer la dernière version. Pour plus d’informations, consultez [Mise à niveau vers une nouvelle version](deployment-upgrade.md).

- Après le déploiement sur AKS, les deux événements d’avertissement suivants peuvent s’afficher à partir du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner la présence d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="external-tables"></a>Tables externes

- Le déploiement de clusters Big Data ne crée plus les sources de données externes **SqlDataPool** et **SqlStoragePool**. Vous pouvez créer ces sources de données manuellement pour prendre en charge la virtualisation des données dans le pool de données et le pool de stockage.

   > [!NOTE]
   > L’URI pour la création de ces sources de données externes est différent entre les versions CTP. Pour savoir comment les créer, consultez les commandes Transact-SQL ci-dessous. 

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://controller-svc/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://controller-svc/default');
   ```

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit :

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Si vous créez une table externe dans Oracle qui utilise des types de données caractères, l’Assistant Virtualisation Azure Data Studio interprète ces colonnes comme des éléments VARCHAR dans la définition de la table externe. Cela entraîne un échec dans la DDL de table externe. Modifiez le schéma Oracle pour utiliser le type NVARCHAR2 ou créez des instructions EXTERNAL TABLE manuellement et spécifiez NVARCHAR au lieu d’utiliser l’Assistant.

#### <a name="application-deployment"></a>Déploiement d'applications

- Lors de l’appel d’une application R, Python ou MLeap à partir de l’API RESTful, l’appel expire en 5 minutes.

#### <a name="spark-and-notebooks"></a>Spark et notebooks

- Les adresses IP de pod peuvent changer dans l’environnement Kubernetes lors du redémarrage des pods. Dans le scénario où le pod principal redémarre, la session Spark peut échouer avec `NoRoteToHostException`. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un Python distinct sur Windows, les notebooks Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un notebook, si vous cliquez sur la commande **Ajouter du texte**, la cellule de texte est ajoutée en mode aperçu plutôt qu’en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier cord dump). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [Modifier le mot de passe AS](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe AS pour les déploiements de clusters Big Data.

#### <a name="kibana-logs-dashboards"></a>Tableaux de bord de journaux Kibana

- Entre Aris CTP 3.0 et 3.1, la version de Kibana a été mise à niveau de 6.3.1 vers 7.0.1.  Le navigateur Microsoft Edge n’est pas compatible avec Kibana. Les utilisateurs verront une page vierge lors du chargement de la version actuelle des tableaux de bord Kibana dans Microsoft Edge. Consultez [ici]( https://www.elastic.co/support/matrix#matrix_browse) les navigateurs pris en charge pour Kibana.rs 


## <a id="ctp30"></a> CTP 3.0 (mai)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 3.0.

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

- Azure Data Studio retourne une erreur lorsque vous tentez de créer un nouveau dossier dans HDFS. Pour activer cette fonctionnalité, installez la build Insiders d’Azure Data Studio:
  
   - [Windows User Installer - **Build Insiders**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-user/insider)
   - [Windows System Installer - **Build Insiders**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64/insider)
   - [Windows ZIP - **Build Insiders**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-archive/insider)
   - [macOS ZIP - **Build Insiders**](https://azuredatastudio-update.azurewebsites.net/latest/darwin/insider)
   - [Linux TAR.GZ - **Build Insiders**](https://azuredatastudio-update.azurewebsites.net/latest/linux-x64/insider)

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut apparaître :

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo dans Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans hdfs-site.xml ne sont pas prises en charge.

#### <a name="deployment"></a>Déploiement

- Les procédures de déploiement précédentes pour les clusters Big Data compatibles GPU ne sont pas prises en charge dans la version CTP 3.0. Une autre procédure de déploiement est en cours d’examen. Pour l’instant, l’article « Déployer un cluster Big Data avec prise en charge GPU et exécuter TensorFlow » a été temporairement supprimé pour éviter toute confusion.

- La mise à niveau d’un cluster de données Big Data à partir d’une version précédente n’est pas prise en charge.

   > [!IMPORTANT]
   > Vous devez sauvegarder vos données puis supprimer votre cluster Big Data existant (à l’aide de la version précédente de **azdata**) avant de déployer la dernière version. Pour plus d’informations, consultez [Mise à niveau vers une nouvelle version](deployment-upgrade.md).

- Après le déploiement sur AKS, les deux événements d’avertissement suivants peuvent s’afficher à partir du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner la présence d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="external-tables"></a>Tables externes

- Le déploiement de clusters Big Data ne crée plus les sources de données externes **SqlDataPool** et **SqlStoragePool**. Vous pouvez créer ces sources de données manuellement pour prendre en charge la virtualisation des données dans le pool de données et le pool de stockage.

   > [!NOTE]
   > L’URI pour la création de ces sources de données externes est différent entre les versions CTP. Pour savoir comment les créer, consultez les commandes Transact-SQL ci-dessous. 

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://controller-svc/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://controller-svc/default');
   ```

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit :

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Si vous créez une table externe dans Oracle qui utilise des types de données caractères, l’Assistant Virtualisation Azure Data Studio interprète ces colonnes comme des éléments VARCHAR dans la définition de la table externe. Cela entraîne un échec dans la DDL de table externe. Modifiez le schéma Oracle pour utiliser le type NVARCHAR2 ou créez des instructions EXTERNAL TABLE manuellement et spécifiez NVARCHAR au lieu d’utiliser l’Assistant.

#### <a name="application-deployment"></a>Déploiement d'applications

- Lors de l’appel d’une application R, Python ou MLeap à partir de l’API RESTful, l’appel expire en 5 minutes.

#### <a name="spark-and-notebooks"></a>Spark et notebooks

- Les adresses IP de pod peuvent changer dans l’environnement Kubernetes lors du redémarrage des pods. Dans le scénario où le pod principal redémarre, la session Spark peut échouer avec `NoRoteToHostException`. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un Python distinct sur Windows, les notebooks Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un notebook, si vous cliquez sur la commande **Ajouter du texte**, la cellule de texte est ajoutée en mode aperçu plutôt qu’en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier cord dump). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [Modifier le mot de passe AS](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe AS pour les déploiements de clusters Big Data.

## <a id="ctp25"></a> CTP 2.5 (avril)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 2.5.

### <a name="whats-new"></a>What's New

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
| Profils de déploiement | Utilisent des [fichiers JSON de configuration du déploiement](deployment-guidance.md#configfile) par défaut et personnalisés pour les déploiements de clusters big data au lieu de variables d’environnement. |
| Déploiements demandés | `azdata cluster create` demande désormais à l’utilisateur de saisir les paramètres requis pour les déploiements par défaut. |
| Changements de point de terminaison de service et de nom de pod | Les points de terminaison externes suivants ont des noms modifiés :<br/>&nbsp;&nbsp;&nbsp;- **endpoint-master-pool** => **master-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-controller** => **controller-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-service-proxy** => **mgmtproxy-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-security** => **gateway-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-app-service-proxy** => **appproxy-svc-external**|
| Améliorations apportées à **azdata** | Utilisez **azdata** pour [faire la liste des points de terminaison externes](deployment-guidance.md#endpoints) et vérifier la version de **azdata** avec le paramètre `--version`. |
| Installation hors connexion | Conseils pour les déploiements de cluster Big Data hors connexion. |
| Améliorations concernant la hiérarchisation HDFS | Hiérarchisation S3, mise en cache du montage et prise en charge OAuth pour ADLS Gen2. |
| Nouveau connecteur `mssql` Spark-SQL Server | |

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus et les limitations de cette version.

#### <a name="deployment"></a>Déploiement

- La mise à niveau d’un cluster de données Big Data à partir d’une version précédente n’est pas prise en charge.

   > [!IMPORTANT]
   > Vous devez sauvegarder vos données puis supprimer votre cluster Big Data existant (à l’aide de la version précédente de **azdata**) avant de déployer la dernière version. Pour plus d’informations, consultez [Mise à niveau vers une nouvelle version](deployment-upgrade.md).

- Après le déploiement sur AKS, les deux événements d’avertissement suivants peuvent s’afficher à partir du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner la présence d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="external-tables"></a>Tables externes

- Le déploiement de clusters Big Data ne crée plus les sources de données externes **SqlDataPool** et **SqlStoragePool**. Vous pouvez créer ces sources de données manuellement pour prendre en charge la virtualisation des données dans le pool de données et le pool de stockage.

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://nmnode-0-svc:50070');
   ```

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit :

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Si vous créez une table externe dans Oracle qui utilise des types de données caractères, l’Assistant Virtualisation Azure Data Studio interprète ces colonnes comme des éléments VARCHAR dans la définition de la table externe. Cela entraîne un échec dans la DDL de table externe. Modifiez le schéma Oracle pour utiliser le type NVARCHAR2 ou créez des instructions EXTERNAL TABLE manuellement et spécifiez NVARCHAR au lieu d’utiliser l’Assistant.

#### <a name="application-deployment"></a>Déploiement d'applications

- Lors de l’appel d’une application R, Python ou MLeap à partir de l’API RESTful, l’appel expire en 5 minutes.

#### <a name="spark-and-notebooks"></a>Spark et notebooks

- Les adresses IP de pod peuvent changer dans l’environnement Kubernetes lors du redémarrage des pods. Dans le scénario où le pod principal redémarre, la session Spark peut échouer avec `NoRoteToHostException`. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un Python distinct sur Windows, les notebooks Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un notebook, si vous cliquez sur la commande **Ajouter du texte**, la cellule de texte est ajoutée en mode aperçu plutôt qu’en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut apparaître :

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo dans Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans hdfs-site.xml ne sont pas prises en charge.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier cord dump). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [Modifier le mot de passe AS](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe AS pour les déploiements de clusters Big Data.

## <a id="ctp24"></a> CTP 2.4 (mars)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 2.4.

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
   > Vous devez sauvegarder vos données puis supprimer votre cluster Big Data existant (à l’aide de la version précédente de **azdata**) avant de déployer la dernière version. Pour plus d’informations, consultez [Mise à niveau vers une nouvelle version](deployment-upgrade.md).

- Après le déploiement sur AKS, les deux événements d’avertissement suivants peuvent s’afficher à partir du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner la présence d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="kubeadm-deployments"></a>Déploiements kubeadm

Si vous utilisez kubeadm pour déployer Kubernetes sur plusieurs machines, le portail d’administration des clusters n’affiche pas correctement les points de terminaison nécessaires pour la connexion au cluster Big Data. Si vous rencontrez ce problème, utilisez la solution de contournement suivante pour découvrir les adresses IP des points de terminaison de service :

- Si vous vous connectez à partir du cluster, interrogez Kubernetes pour obtenir l’adresse IP du point de terminaison auquel vous souhaitez vous connecter. Par exemple, la commande **kubectl** suivante affiche l’adresse IP de l’instance principale SQL Server :

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Pour vous connecter depuis l’extérieur du cluster, procédez comme suit :

   1. Récupérez l’adresse IP du nœud qui exécute l’instance principale SQL Server : `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`.

   1. Connectez-vous à l’instance principale SQL Server à l’aide de cette adresse IP.

   1. Interrogez le **cluster_endpoint_table** dans la base de données Master pour trouver d’autres points de terminaison externes.

      En cas d’échec avec expiration de la connexion, il est possible que le nœud respectif soit bloqué par un pare-feu. Dans ce cas, vous devez contacter votre administrateur de cluster Kubernetes et demander l’adresse IP de nœud exposée en externe. Il peut s’agir de n’importe quel nœud. Vous pouvez ensuite utiliser cette adresse IP et le port correspondant pour vous connecter à différents services exécutés dans le cluster. Par exemple, l’administrateur peut trouver cette adresse IP en exécutant :

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a name="delete-cluster-fails"></a>Échec de la suppression du cluster

Lorsque vous essayez de supprimer un cluster avec **azdata**, il échoue avec l’erreur suivante :

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

Un nouveau client Python Kubernetes (version 9.0.0) a modifié l’API de suppression des espaces de noms, ce qui bloque actuellement **azdata**. Cela se produit uniquement si un client Python Kubernetes plus récent est installé. Vous pouvez contourner ce problème en supprimant directement le cluster à l’aide de **kubectl** (`kubectl delete ns <ClusterName>`), ou vous pouvez installer l’ancienne version à l’aide de `sudo pip install kubernetes==8.0.1`.

#### Tables externes <a id="externaltablesctp24"></a>

- Le déploiement de clusters Big Data ne crée plus les sources de données externes **SqlDataPool** et **SqlStoragePool**. Vous pouvez créer ces sources de données manuellement pour prendre en charge la virtualisation des données dans le pool de données et le pool de stockage.

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://service-master-pool:50070');
   ```

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit :

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Si vous créez une table externe dans Oracle qui utilise des types de données caractères, l’Assistant Virtualisation Azure Data Studio interprète ces colonnes comme des éléments VARCHAR dans la définition de la table externe. Cela entraîne un échec dans la DDL de table externe. Modifiez le schéma Oracle pour utiliser le type NVARCHAR2 ou créez des instructions EXTERNAL TABLE manuellement et spécifiez NVARCHAR au lieu d’utiliser l’Assistant.

#### <a name="application-deployment"></a>Déploiement d'applications

- Lors de l’appel d’une application R, Python ou MLeap à partir de l’API RESTful, l’appel expire en 5 minutes.

#### <a name="spark-and-notebooks"></a>Spark et notebooks

- Les adresses IP de pod peuvent changer dans l’environnement Kubernetes lors du redémarrage des pods. Dans le scénario où le pod principal redémarre, la session Spark peut échouer avec `NoRoteToHostException`. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un Python distinct sur Windows, les notebooks Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un notebook, si vous cliquez sur la commande **Ajouter du texte**, la cellule de texte est ajoutée en mode aperçu plutôt qu’en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut apparaître :

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo dans Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans hdfs-site.xml ne sont pas prises en charge.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier cord dump). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [Modifier le mot de passe AS](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe AS pour les déploiements de clusters Big Data.

## <a id="ctp23"></a> CTP 2.3 (février)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 2.3.

### <a name="whats-new"></a>What's New

| Nouvelle fonctionnalité ou mise à jour | Détails |
| :---------- | :------ |
| Envoyer des travaux Spark sur des clusters Big Data dans IntelliJ. | [Envoyer des travaux Spark [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] sur dans IntelliJ](spark-submit-job-intellij-tool-plugin.md) |
| CLI courantes pour la gestion des clusters et le déploiement des applications. | [Comment déployer une application sur[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](big-data-cluster-create-apps.md) |
| Extension de VS Code pour déployer des applications sur un cluster de Big Data. | [Comment utiliser VS Code pour déployer des applications sur[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](app-deployment-extension.md) |
| Modifications apportées à l’utilisation des commandes de l’outil **azdata**. | Pour plus d’informations, consultez les [problèmes connus pour azdata](#azdatactp23). |
| Utiliser Sparklyr dans les clusters Big Data | [Utiliser Sparklyr dans des clusters Big Data SQL Server 2019](sparklyr-from-RStudio.md) |
| Monter un stockage compatible HDFS externe dans le cluster Big Data avec une **hiérarchisation HDFS**. | Consultez [Hiérarchisation HDFS](hdfs-tiering.md). |
| Nouvelle expérience de connexion unifiée pour l’instance principale de SQL Server et la passerelle HDFS/Spark. | Consultez [Instance principale de SQL Server et passerelle HDFS/Spark](connect-to-big-data-cluster.md). |
| La suppression d’un cluster avec **azdata cluster delete** supprime à présent uniquement les objets dans l’espace de noms qui faisaient partie du cluster Big Data. | L’espace de noms n’est pas supprimé. Toutefois, dans les versions antérieures, cette commande supprimait l’espace de noms dans son intégralité. |
| Les noms de point de terminaison de _Sécurité_ ont été modifiés et consolidés. | **service-security-lb** et **service-security-nodeport** ont été consolidés dans le point de terminaison **endpoint-security**. |
| Les noms de point de terminaison de _Proxy_ ont été modifiés et consolidés. | **service-proxy-lb** et **service-proxy-nodeport** ont été consolidés dans le point de terminaison **endpoint-service-proxy**. |
| Les noms de point de terminaison de _Contrôleur_ ont été modifiés et consolidés. | **service-mssql-controller-lb** et **service-mssql-controller-nodeport** ont été consolidés dans le point de terminaison **endpoint-controller**. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus et les limitations de cette version.

#### <a name="deployment"></a>Déploiement

- La mise à niveau d’un cluster de données Big Data à partir d’une version précédente n’est pas prise en charge.

   > [!IMPORTANT]
   > Vous devez sauvegarder vos données puis supprimer votre cluster Big Data existant (à l’aide de la version précédente de **azdata**) avant de déployer la dernière version. Pour plus d’informations, consultez [Mise à niveau vers une nouvelle version](deployment-upgrade.md).

- La variable d’environnement **ACCEPT_EULA** doit être définie sur « yes » ou « Yes » pour accepter le CLUF. Les versions précédentes autorisaient « y » et « Y », mais celles-ci ne sont plus acceptées et entraînent l’échec du déploiement.

- Les variables d’environnement **CLUSTER_PLATFORM** n’ont pas de valeur par défaut comme c’était le cas dans les versions précédentes.

- Après le déploiement sur AKS, les deux événements d’avertissement suivants peuvent s’afficher à partir du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner la présence d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="kubeadm-deployments"></a>Déploiements kubeadm

Si vous utilisez kubeadm pour déployer Kubernetes sur plusieurs machines, le portail d’administration des clusters n’affiche pas correctement les points de terminaison nécessaires pour la connexion au cluster Big Data. Si vous rencontrez ce problème, utilisez la solution de contournement suivante pour découvrir les adresses IP des points de terminaison de service :

- Si vous vous connectez à partir du cluster, interrogez Kubernetes pour obtenir l’adresse IP du point de terminaison auquel vous souhaitez vous connecter. Par exemple, la commande **kubectl** suivante affiche l’adresse IP de l’instance principale SQL Server :

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- Pour vous connecter depuis l’extérieur du cluster, procédez comme suit :

   1. Récupérez l’adresse IP du nœud qui exécute l’instance principale SQL Server : `kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`.

   1. Connectez-vous à l’instance principale SQL Server à l’aide de cette adresse IP.

   1. Interrogez le **cluster_endpoint_table** dans la base de données Master pour trouver d’autres points de terminaison externes.

      En cas d’échec avec expiration de la connexion, il est possible que le nœud respectif soit bloqué par un pare-feu. Dans ce cas, vous devez contacter votre administrateur de cluster Kubernetes et demander l’adresse IP de nœud exposée en externe. Il peut s’agir de n’importe quel nœud. Vous pouvez ensuite utiliser cette adresse IP et le port correspondant pour vous connecter à différents services exécutés dans le cluster. Par exemple, l’administrateur peut trouver cette adresse IP en exécutant :

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a id="azdatactp23"></a> azdata

- L’outil **azdata** est passé d’un ordre de commande verbe-substantif à un ordre nom-verbe. Par exemple, `azdata create cluster` est maintenant `azdata cluster create`.

- Le paramètre `--name` est maintenant requis lors de la création d’un cluster avec `azdata cluster create`.

   ```bash
   azdata cluster create --name <cluster_name>
   ```

- Pour obtenir des informations importantes sur la mise à niveau vers la dernière version des clusters Big Data et **azdata**, consultez [Mise à niveau vers une nouvelle version](deployment-upgrade.md).

#### <a name="external-tables"></a>Tables externes

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit :

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- Si vous créez une table externe dans Oracle qui utilise des types de données caractères, l’Assistant Virtualisation Azure Data Studio interprète ces colonnes comme des éléments VARCHAR dans la définition de la table externe. Cela entraîne un échec dans la DDL de table externe. Modifiez le schéma Oracle pour utiliser le type NVARCHAR2 ou créez des instructions EXTERNAL TABLE manuellement et spécifiez NVARCHAR au lieu d’utiliser l’Assistant.

#### <a name="application-deployment"></a>Déploiement d'applications

- Lors de l’appel d’une application R, Python ou MLeap à partir de l’API RESTful, l’appel expire en 5 minutes.

#### <a name="spark-and-notebooks"></a>Spark et notebooks

- Les adresses IP de pod peuvent changer dans l’environnement Kubernetes lors du redémarrage des pods. Dans le scénario où le pod principal redémarre, la session Spark peut échouer avec `NoRoteToHostException`. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un Python distinct sur Windows, les notebooks Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un notebook, si vous cliquez sur la commande **Ajouter du texte**, la cellule de texte est ajoutée en mode aperçu plutôt qu’en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut apparaître :

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo dans Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans hdfs-site.xml ne sont pas prises en charge.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier cord dump). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [Modifier le mot de passe AS](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe AS pour les déploiements de clusters Big Data.

## <a id="ctp22"></a> CTP 2.2 (décembre 2018)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 2.2.

### <a name="new-features"></a>Nouvelles fonctionnalités

- Portail d’administration des clusters accessible avec `/portal` (**https://\<ip-address\>:30777/portal**)
- Le nom du service du pool principal est passé de `service-master-pool-lb` et `service-master-pool-nodeport` à `endpoint-master-pool`.
- Nouvelle version de **azdata** et images mises à jour.
- Améliorations et résolutions de bogues divers.

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus et les limitations de cette version.

#### <a name="deployment"></a>Déploiement

- La mise à niveau d’un cluster de données Big Data à partir d’une version précédente n’est pas prise en charge. Vous devez sauvegarder et supprimer tout cluster Big Data existant avant de déployer la dernière version. Pour plus d’informations, consultez [Mise à niveau vers une nouvelle version](deployment-upgrade.md).

- Après le déploiement sur AKS, les deux événements d’avertissement suivants peuvent s’afficher à partir du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner la présence d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="cluster-administration-portal"></a>Portail d’administration du cluster

Le portail d’administration des clusters n’affiche pas le point de terminaison de l’instance principale SQL Server. Pour trouver l’adresse IP et le port de l’instance principale, utilisez la commande **kubectl** suivante :

```
kubectl get svc endpoint-master-pool -n <your-big-data-cluster-name>
```

#### <a name="external-tables"></a>Tables externes

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit :

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark et notebooks

- Les adresses IP de pod peuvent changer dans l’environnement Kubernetes lors du redémarrage des pods. Dans le scénario où le pod principal redémarre, la session Spark peut échouer avec `NoRoteToHostException`. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un Python distinct sur Windows, les notebooks Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un notebook, si vous cliquez sur la commande **Ajouter du texte**, la cellule de texte est ajoutée en mode aperçu plutôt qu’en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut apparaître :

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo dans Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans hdfs-site.xml ne sont pas prises en charge.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier cord dump). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [Modifier le mot de passe AS](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe AS pour les déploiements de clusters Big Data.

## <a id="ctp21"></a> CTP 2.1 (novembre 2018)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 2.1.

### <a name="new-features"></a>Nouvelles fonctionnalités

- [Déployez des applications Python et R](big-data-cluster-create-apps.md) dans un cluster Big Data.
- Nouvelle version de **azdata** et images mises à jour. 
- Améliorations et résolutions de bogues divers.

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes fournissent des problèmes connus [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] pour dans la version CTP 2,1.

#### <a name="deployment"></a>Déploiement

- La mise à niveau d’un cluster de données Big Data à partir d’une version précédente n’est pas prise en charge. Vous devez sauvegarder et supprimer tout cluster Big Data existant avant de déployer la dernière version. Pour plus d’informations, consultez [Mise à niveau vers une nouvelle version](deployment-upgrade.md).

- Après le déploiement sur AKS, les deux événements d’avertissement suivants peuvent s’afficher à partir du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner la présence d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="admin-portal"></a>Portail d’administration

- Lorsque vous [créez une application à l’aide de la commande msqlctl-ctp](big-data-cluster-create-apps.md) et que vous la déployez sur un cluster Big Data SQL Server, le portail d’administration des clusters affiche les pods où l’application a été déployée comme « inconnus » dans la section Contrôleur de la partie administrateur.

#### <a name="external-tables"></a>Tables externes

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit :

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark et notebooks

- Les adresses IP de pod peuvent changer dans l’environnement Kubernetes lors du redémarrage des pods. Dans le scénario où le pod principal redémarre, la session Spark peut échouer avec `NoRoteToHostException`. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un Python distinct sur Windows, les notebooks Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un notebook, si vous cliquez sur la commande **Ajouter du texte**, la cellule de texte est ajoutée en mode aperçu plutôt qu’en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut apparaître :

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo dans Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans hdfs-site.xml ne sont pas prises en charge.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier cord dump). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [Modifier le mot de passe AS](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe AS pour les déploiements de clusters Big Data.

## <a id="ctp20"></a> CTP 2.0 (octobre 2018)

Les sections suivantes décrivent les nouvelles fonctionnalités et les problèmes connus pour les clusters Big Data dans SQL Server 2019 CTP 2.0.

### <a name="new-features"></a>Nouvelles fonctionnalités

- Simple expérience de déploiement à l’aide de l’outil de gestion azdata
- Expérience de notebook native dans Azure Data Studio
- Interroger les fichiers HDFS via l’instance de stockage de SQL Server
- Virtualisation des données via Master pour SQL Server, Oracle, MongoDB et HDFS
- Assistant Virtualisation des données pour SQL Server et Oracle dans Azure Data Studio
- Services ML sur Master
- Portail d’administration des clusters que vous pouvez utiliser pour la surveillance et la résolution des problèmes
- Envoi de travaux Spark dans Azure Data Studio 
- Interface utilisateur Spark dans le portail d’administration des clusters
- Montage du volume sur les classes de stockage
- Requêtes sur les pools de données à partir de Master
- Afficher le plan des requêtes distribuées dans SSMS
- Package PIP pour l’outil de gestion azdata
- Moteur de déploiement intégré via le service de contrôleur

### <a name="known-issues"></a>Problèmes connus

Les sections suivantes fournissent des problèmes connus [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] pour dans la version CTP 2,0.

#### <a name="deployment"></a>Déploiement

- Si vous utilisez Azure Kubernetes Service (AKS), la version recommandée de Kubernetes est 1.10.*, qui ne prend pas en charge le redimensionnement de disque. Vous devez vous assurer que vous dimensionnez le stockage en conséquence au moment du déploiement. Pour plus d’informations sur la façon d’ajuster les tailles de stockage, consultez l’article sur la [persistance des données](concept-data-persistence.md). Pour Kubernetes déployé sur des machines virtuelles, la version recommandée est 1.11.

- Après le déploiement sur AKS, les deux événements d’avertissement suivants peuvent s’afficher à partir du déploiement. Ces deux événements sont des problèmes connus, mais ils ne vous empêchent pas de déployer correctement le cluster Big Data sur AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- En cas d’échec du déploiement d’un cluster Big Data, l’espace de noms associé n’est pas supprimé. Cela peut entraîner la présence d’un espace de noms orphelin sur le cluster. Une solution de contournement consiste à supprimer manuellement l’espace de noms avant de déployer un cluster portant le même nom.

#### <a name="external-tables"></a>Tables externes

- Il est possible de créer une table externe de pool de données pour une table qui a des types de colonnes non pris en charge. Si vous interrogez la table externe, vous recevez un message similaire à ce qui suit :

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Si vous interrogez une table externe de pool de stockage, vous pouvez obtenir une erreur si le fichier sous-jacent est copié dans HDFS en même temps.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark et notebooks

- Les adresses IP de pod peuvent changer dans l’environnement Kubernetes lors du redémarrage des pods. Dans le scénario où le pod principal redémarre, la session Spark peut échouer avec `NoRoteToHostException`. Cela est dû au fait que les caches JVM ne sont pas actualisés avec les nouvelles adresses IP.

- Si vous avez déjà installé Jupyter et un Python distinct sur Windows, les notebooks Spark peuvent échouer. Pour contourner ce problème, mettez à niveau Jupyter vers la dernière version.

- Dans un notebook, si vous cliquez sur la commande **Ajouter du texte**, la cellule de texte est ajoutée en mode aperçu plutôt qu’en mode édition. Vous pouvez cliquer sur l’icône d’aperçu pour basculer en mode édition et modifier la cellule.

#### <a name="hdfs"></a>HDFS

- Si vous cliquez avec le bouton droit sur un fichier dans HDFS pour l’afficher, l’erreur suivante peut apparaître :

   `Error previewing file: File exceeds max size of 30MB`

   Actuellement, il n’existe aucun moyen d’afficher un aperçu des fichiers de plus de 30 Mo dans Azure Data Studio.

- Les modifications de configuration apportées à HDFS qui impliquent des modifications dans hdfs-site.xml ne sont pas prises en charge.

#### <a name="security"></a>Sécurité

- SA_PASSWORD fait partie de l’environnement et peut être découvert (par exemple dans un fichier cord dump). Vous devez réinitialiser le SA_PASSWORD sur l’instance principale après le déploiement. Ce n’est pas un bogue, mais une étape de sécurité. Pour plus d’informations sur la façon de modifier le SA_PASSWORD dans un conteneur Linux, consultez [Modifier le mot de passe AS](../linux/quickstart-install-connect-docker.md#sapassword).

- Les journaux AKS peuvent contenir un mot de passe AS pour les déploiements de clusters Big Data.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]sur, consultez [que [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]sont ?](big-data-cluster-overview.md).
