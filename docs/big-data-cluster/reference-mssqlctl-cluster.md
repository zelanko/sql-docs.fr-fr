---
title: référence de cluster mssqlctl
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de cluster mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c3a15fb9658f25977542754d6479b09b97323f53
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65993327"
---
# <a name="mssqlctl-cluster"></a>Cluster mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **cluster** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[mssqlctl cluster create](#mssqlctl-cluster-create) | Créer le cluster.
[mssqlctl cluster delete](#mssqlctl-cluster-delete) | Supprimer le cluster.
[mssqlctl cluster config](reference-mssqlctl-cluster-config.md) | Commandes de configuration de cluster.
[point de terminaison de cluster mssqlctl](reference-mssqlctl-cluster-endpoint.md) | Commandes de point de terminaison.
[mssqlctl cluster status](reference-mssqlctl-cluster-status.md) | Commandes d’état.
[mssqlctl cluster debug](reference-mssqlctl-cluster-debug.md) | Commandes de débogage.
[pool de stockage de cluster mssqlctl](reference-mssqlctl-cluster-storage-pool.md) | Gérer les pools de stockage de cluster.
## <a name="mssqlctl-cluster-create"></a>mssqlctl cluster create
Créer un Cluster de données volumineuses de SQL Server - Configuration de kube est requise sur votre système, ainsi que les variables d’environnement ['CONTROLLER_USERNAME', 'CONTROLLER_PASSWORD', 'DOCKER_USERNAME', 'DOCKER_PASSWORD', 'MSSQL_SA_PASSWORD', 'KNOX_PASSWORD'].
```bash
mssqlctl cluster create [--config-file -c] 
                        [--accept-eula -a]  
                        [--node-label -l]  
                        [--force -f]
```
### <a name="examples"></a>Exemples
Expérience de déploiement de cluster - dirigée vous recevrez des invites pour les valeurs nécessaires.
```bash
mssqlctl cluster create
```
Le déploiement du cluster avec des arguments.
```bash
mssqlctl cluster create --accept-eula yes --config-file aks-dev-test.json
```
Déploiement de cluster avec des arguments - aucune invite n’est indiquée en--force indicateur est utilisé.
```bash
mssqlctl cluster create --accept-eula yes --config-file aks-dev-test.json --force
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--config-file -c`
Profil de configuration, utilisé pour le déploiement du cluster du cluster : [« aks-dev-test.json', ' kubeadm-dev-test.json', ' minikube-dev-test.json']
#### `--accept-eula -a`
Acceptez-vous les termes du contrat de licence ? Oui/non. Si vous ne souhaitez pas utiliser cette arg, vous pouvez définir la variable d’environnement ACCEPT_EULA sur « Oui »
#### `--node-label -l`
Étiquette de nœud de cluster, utilisée pour désigner quels nœuds à déployer sur.
#### `--force -f`
Force à créer, l’utilisateur ne sera pas invité à entrer pour toutes les valeurs et tous les problèmes seront affichera dans le cadre de stderr.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de journalisation pour afficher que tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et de sortie.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de journalisation. Utilisez--debug pour les journaux de débogage complets.
## <a name="mssqlctl-cluster-delete"></a>mssqlctl cluster delete
Supprimer le Cluster de données volumineuses de SQL Server - Configuration de kube est requise sur votre système, ainsi que les variables d’environnement ['CONTROLLER_USERNAME', 'CONTROLLER_PASSWORD'].
```bash
mssqlctl cluster delete --name -n 
                        [--force -f]
```
### <a name="examples"></a>Exemples
Suppression de cluster où le nom d’utilisateur du contrôleur et le mot de passe sont déjà définies dans votre environnement de système.
```bash
mssqlctl cluster delete --name <cluster_name>
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--name -n`
Nom du cluster, utilisé pour l’espace de noms kubernetes.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--force -f`
Cluster de suppression de force.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de journalisation pour afficher que tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et de sortie.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de journalisation. Utilisez--debug pour les journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).
