---
title: Référence azdata BDC
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes BDC azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 488394cbf4b52a952ffc46ab2ec6c9a273466bd5
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426039"
---
# <a name="azdata-bdc"></a>azdata BDC

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes **BDC** dans l’outil **azdata** . Pour plus d’informations sur les autres commandes **azdata** , consultez [référence azdata](reference-azdata.md).

## <a name="commands"></a>Commandes

|     |     |
| --- | --- |
[création de azdata BDC](#azdata-bdc-create) | Créez un cluster Big Data.
[supprimer azdata BDC](#azdata-bdc-delete) | Supprimer le cluster Big Data.
[configuration du BDC azdata](reference-azdata-bdc-config.md) | Commandes de configuration.
[point de terminaison BDC azdata](reference-azdata-bdc-endpoint.md) | Commandes de point de terminaison.
[État du contrôleur de domaine azdata](reference-azdata-bdc-status.md) | Commandes d’État.
[débogage azdata BDC](reference-azdata-bdc-debug.md) | Commandes de débogage.
[contrôle BDC azdata](reference-azdata-bdc-control.md) | Commandes de contrôle.
[Pool BDC azdata](reference-azdata-bdc-pool.md) | Commandes de pool.
[azdata BDC HDFS](reference-azdata-bdc-hdfs.md) | Le module HDFS fournit des commandes pour accéder à un système de fichiers HDFS.
[azdata BDC Spark](reference-azdata-bdc-spark.md) | Les commandes Spark permettent à l’utilisateur d’interagir avec le système Spark en créant et en gérant des sessions, des instructions et des lots.
## <a name="azdata-bdc-create"></a>création de azdata BDC
Créez un cluster SQL Server Big Data-Kube config est requis sur votre système avec les variables d’environnement suivantes [«CONTROLLER_USERNAME», «CONTROLLER_PASSWORD», «MSSQL_SA_PASSWORD», «KNOX_PASSWORD»].
```bash
azdata bdc create [--name -n] 
                  [--config-profile -c]  
                  [--accept-eula -a]  
                  [--node-label -l]  
                  [--force -f]
```
### <a name="examples"></a>Exemples

Expérience de déploiement du BDC guidé: vous recevrez des invites pour les valeurs nécessaires.

```bash
azdata bdc create
```

Déploiement du BDC avec des arguments.

```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test
```
Déploiement du BDC avec le nom spécifié au lieu du nom par défaut dans le profil.
```bash
azdata bdc create --name <cluster_name> --accept-eula yes --config-profile aks-dev-test --force
```

Déploiement du BDC avec arguments-aucune invite n’est fournie, car l’indicateur--Force est utilisé.

```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test --force
```

### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--name -n`
Nom du cluster Big Data, utilisé pour les espaces de noms kubernetes.
#### `--config-profile -c`
Profil de configuration de cluster Big Data, utilisé pour le déploiement du cluster: ['AKS-dev-test', 'kubeadm-dev-test', 'minikube-dev-test']
#### `--accept-eula -a`
Acceptez-vous les termes du contrat de licence? [Oui/non]. Si vous ne souhaitez pas utiliser ce ARG, vous pouvez définir la variable d’environnement ACCEPT_EULA sur «Yes». Vous pouvez consulter les termes du contrat de licence de https://aka.ms/azdata-eula ce https://go.microsoft.com/fwlink/?LinkId=2002534 produit à l’adresse et.
#### `--node-label -l`
Étiquette de nœud de cluster Big Data, utilisée pour désigner les nœuds vers lesquels effectuer le déploiement.
#### `--force -f`
Force Create, l’utilisateur ne sera pas invité à entrer des valeurs et tous les problèmes seront imprimés dans le cadre de stderr.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées: JSON, jsonc, table, TSV.  Valeur par défaut: JSON.
#### `--query -q`
Chaîne de requête JMESPath. Pour [http://jmespath.org/](http://jmespath.org/]) plus d’informations et d’exemples, consultez.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.
## <a name="azdata-bdc-delete"></a>supprimer azdata BDC
Supprimez le cluster SQL Server Big Data-Kube config est requis sur votre système avec les variables d’environnement suivantes [«CONTROLLER_USERNAME», «CONTROLLER_PASSWORD»].
```bash
azdata bdc delete --name -n 
                  [--force -f]
```
### <a name="examples"></a>Exemples
Suppression du BDC où le nom d’utilisateur et le mot de passe du contrôleur sont déjà définis dans votre environnement système.
```bash
azdata bdc delete --name <cluster_name>
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--name -n`
Nom du cluster Big Data, utilisé pour l’espace de noms kubernetes.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--force -f`
Forcez la suppression du cluster Big Data.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées: JSON, jsonc, table, TSV.  Valeur par défaut: JSON.
#### `--query -q`
Chaîne de requête JMESPath. Pour [http://jmespath.org/](http://jmespath.org/]) plus d’informations et d’exemples, consultez.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres commandes **azdata** , consultez [référence azdata](reference-azdata.md). Pour plus d’informations sur l’installation de l’outil **azdata** , consultez [installer azdata pour gérer les clusters SQL Server 2019 Big Data](deploy-install-azdata.md).
