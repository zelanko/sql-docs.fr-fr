---
title: Informations de référence sur azdata bdc
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata bdc.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a4b619396c2dcdad589deff3f9fc6a03fe37c1d5
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531692"
---
# <a name="azdata-bdc"></a>azdata bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

L’article suivant fournit des références sur les commandes `sql` dans l’outil `azdata`. Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md)

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata bdc create](#azdata-bdc-create) | Crée un cluster Big Data.
[azdata bdc delete](#azdata-bdc-delete) | Supprime un cluster Big Data.
[azdata bdc upgrade](#azdata-bdc-upgrade) | Mettez à jour les images déployées dans chaque conteneur dans le cluster Big Data SQL Server.
[azdata bdc config](reference-azdata-bdc-config.md) | Commandes de configuration.
[azdata bdc endpoint](reference-azdata-bdc-endpoint.md) | Commandes relatives aux points de terminaison.
[azdata bdc debug](reference-azdata-bdc-debug.md) | Commandes de débogage.
[azdata bdc status](reference-azdata-bdc-status.md) | Commandes d’état du cluster Big Data.
[azdata bdc control](reference-azdata-bdc-control.md) | Commandes du service de contrôle.
[azdata bdc sql](reference-azdata-bdc-sql.md) | Commandes du service SQL.
[azdata bdc hdfs](reference-azdata-bdc-hdfs.md) | Commandes du service HDFS.
[azdata bdc spark](reference-azdata-bdc-spark.md) | Commandes du service Spark.
[azdata bdc gateway](reference-azdata-bdc-gateway.md) | Commandes du service de passerelle.
[azdata bdc app](reference-azdata-bdc-app.md) | Commandes du service App Service.
[azdata bdc spark](reference-azdata-bdc-spark.md) | Les commandes Spark permettent à l’utilisateur d’interagir avec le système Spark en créant et en gérant des sessions, des instructions et des lots.
[azdata bdc hdfs](reference-azdata-bdc-hdfs.md) | Le module HDFS fournit des commandes pour accéder à un système de fichiers HDFS.
## <a name="azdata-bdc-create"></a>azdata bdc create
Créez un cluster Big Data SQL Server. La configuration Kubernetes est requise sur votre système avec les variables d’environnement suivantes ['AZDATA_USERNAME', 'AZDATA_PASSWORD'].
```bash
azdata bdc create [--name -n] 
                  [--config-profile -c]  
                  [--accept-eula -a]  
                  [--node-label -l]  
                  [--force -f]
```
### <a name="examples"></a>Exemples
Déploiement guidé de BDC : vous serez invité à entrer les valeurs nécessaires.
```bash
azdata bdc create
```
Déploiement de BDC avec des arguments.
```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test
```
Déploiement de BDC avec le nom spécifié au lieu du nom par défaut du profil.
```bash
azdata bdc create --name <cluster_name> --accept-eula yes --config-profile aks-dev-test --force
```
Déploiement de BDC avec des arguments : aucune invite ne s’affiche, car l’indicateur --force est utilisé.
```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test --force
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--name -n`
Nom du cluster Big Data, utilisé pour les espaces de noms Kubernetes.
#### `--config-profile -c`
Profil de configuration de cluster Big Data, utilisé pour le déploiement du cluster : ['kubeadm-dev-test', 'kubeadm-prod', 'aks-dev-test', 'aks-dev-test-ha']
#### `--accept-eula -a`
Acceptez-vous les termes du contrat de licence ? [oui/non]. Si vous ne voulez pas utiliser cet argument, vous pouvez définir la variable d’environnement ACCEPT_EULA sur « oui ». Les termes du contrat de licence pour azdata sont visibles à l’adresse https://aka.ms/eula-azdata-en et les termes du contrat de licence pour le cluster Big Data sont visibles pour Entreprise à l’adresse https://go.microsoft.com/fwlink/?linkid=2104292, pour Standard à l’adresse https://go.microsoft.com/fwlink/?linkid=2104294 et pour Developer à l’adresse https://go.microsoft.com/fwlink/?linkid=2104079.
#### `--node-label -l`
Étiquette de nœud de cluster Big Data, utilisée pour désigner les nœuds sur lesquels effectuer le déploiement.
#### `--force -f`
Création forcée. L’utilisateur ne sera pas invité à entrer des valeurs, et les éventuels problèmes seront affichés dans le cadre d’une erreur standard.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour obtenir des journaux de débogage complets.
## <a name="azdata-bdc-delete"></a>azdata bdc delete
Supprimez le cluster Big Data SQL Server. La configuration Kubernetes est requise sur votre système.
```bash
azdata bdc delete --name -n 
                  [--force -f]
```
### <a name="examples"></a>Exemples
Suppression du cluster Big Data.
```bash
azdata bdc delete --name <cluster_name>
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--name -n`
Nom du cluster Big Data, utilisé pour l’espace de noms Kubernetes.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--force -f`
Suppression forcée du cluster Big Data.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-bdc-upgrade"></a>azdata bdc upgrade
Mettez à jour les images déployées dans chaque conteneur dans le cluster Big Data SQL Server. Les images mises à jour sont basées sur l’image Docker transmise. Si les images mises à jour proviennent d’un dépôt d’images Docker différent des images actuellement déployées, le paramètre « repository » est également requis.
```bash
azdata bdc upgrade --name -n 
                   --tag -t  
                   [--repository -r]
```
### <a name="examples"></a>Exemples
Mise à niveau de cluster Big Data vers une nouvelle balise d’image « cu2 » à partir du même dépôt.
```bash
azdata bdc upgrade -t cu2
```
Mise à niveau de cluster Big Data vers une nouvelle image avec la balise « cu2 » à partir d’un nouveau dépôt « foo/bar/baz ».
```bash
azdata bdc upgrade -t cu2 -r foo/bar/baz
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--name -n`
Nom du cluster Big Data, utilisé pour les espaces de noms Kubernetes.
#### `--tag -t`
Balise d’image Docker cible vers laquelle mettre à niveau tous les conteneurs du cluster.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--repository -r`
Dépôt Docker à partir duquel tous les conteneurs du cluster doivent extraire leurs images.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md). Pour plus d’informations sur l’installation de l’outil `azdata`, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
