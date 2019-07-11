---
title: mssqlctl bdc reference
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de bdc mssqlctl.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 96ecf1c987baffec0ff71b8b6ef5eccb204b3108
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727484"
---
# <a name="mssqlctl-bdc"></a>mssqlctl bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **bdc** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[mssqlctl bdc create](#mssqlctl-bdc-create) | Créer un Cluster de données volumineux.
[mssqlctl bdc delete](#mssqlctl-bdc-delete) | Supprimer le Cluster de données volumineux.
[mssqlctl bdc config](reference-mssqlctl-bdc-config.md) | Commandes de configuration.
[mssqlctl bdc endpoint](reference-mssqlctl-bdc-endpoint.md) | Commandes de point de terminaison.
[mssqlctl bdc status](reference-mssqlctl-bdc-status.md) | Commandes d’état.
[mssqlctl bdc debug](reference-mssqlctl-bdc-debug.md) | Commandes de débogage.
[mssqlctl bdc storage-pool](reference-mssqlctl-bdc-storage-pool.md) | Commandes de pool de stockage.
[mssqlctl bdc control](reference-mssqlctl-bdc-control.md) | Commandes de contrôle.
[mssqlctl bdc pool](reference-mssqlctl-bdc-pool.md) | Commandes de pool.
## <a name="mssqlctl-bdc-create"></a>mssqlctl bdc create
Créer un Cluster de données volumineuses de SQL Server - Configuration de kube est requise sur votre système, ainsi que les variables d’environnement ['CONTROLLER_USERNAME', 'CONTROLLER_PASSWORD', 'DOCKER_USERNAME', 'DOCKER_PASSWORD', 'MSSQL_SA_PASSWORD', 'KNOX_PASSWORD'].
```bash
mssqlctl bdc create [--config-profile -c] 
                    [--accept-eula -a]  
                    [--node-label -l]  
                    [--force -f]
```
### <a name="examples"></a>Exemples
Expérience de déploiement BDC interactive - vous allez recevoir des invites pour les valeurs nécessaires.
```bash
mssqlctl bdc create
```
Déploiement du BDC avec des arguments.
```bash
mssqlctl bdc create --accept-eula yes --config-profile aks-dev-test
```
Déploiement du BDC avec arguments - aucune invite n’est indiquée en--force indicateur est utilisé.
```bash
mssqlctl bdc create --accept-eula yes --config-profile aks-dev-test --force
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--config-profile -c`
Profil de configuration du BDC, utilisé pour déployer le cluster : [« aks-dev-test », « kubeadm-dev-test », « minikube-dev-test »]
#### `--accept-eula -a`
Acceptez-vous les termes du contrat de licence ? Oui/non. Si vous ne souhaitez pas utiliser cette arg, vous pouvez définir la variable d’environnement ACCEPT_EULA sur « Oui »
#### `--node-label -l`
Étiquette du nœud BDC, utilisée pour désigner quels nœuds à déployer sur.
#### `--force -f`
Force à créer, l’utilisateur ne sera pas invité à entrer pour toutes les valeurs et tous les problèmes seront affichera dans le cadre de stderr.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.
## <a name="mssqlctl-bdc-delete"></a>mssqlctl bdc delete
Supprimer le Cluster de données volumineuses de SQL Server - Configuration de kube est requise sur votre système, ainsi que les variables d’environnement ['CONTROLLER_USERNAME', 'CONTROLLER_PASSWORD'].
```bash
mssqlctl bdc delete --name -n 
                    [--force -f]
```
### <a name="examples"></a>Exemples
Suppression de BDC où le nom d’utilisateur du contrôleur et le mot de passe sont déjà définies dans votre environnement de système.
```bash
mssqlctl bdc delete --name <cluster_name>
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--name -n`
Nom BDC, utilisé pour l’espace de noms kubernetes.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--force -f`
Forcer la suppression BDC.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).
