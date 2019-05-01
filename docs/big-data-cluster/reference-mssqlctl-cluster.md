---
title: référence de cluster mssqlctl
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de cluster mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c69aeced2378e018376172e1fb6370d56706ecb7
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473326"
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
[mssqlctl cluster debug](reference-mssqlctl-cluster-debug.md) | Commandes de débogage.
## <a name="mssqlctl-cluster-create"></a>mssqlctl cluster create
Créer un Cluster SQL Server Big Data.
```bash
mssqlctl cluster create [--config-file -f] 
                        [--accept-eula -e]  
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--config-file -f`
Profil de configuration, utilisé pour le déploiement du cluster du cluster : [« aks-dev-test.json', ' kubeadm-dev-test.json', ' minikube-dev-test.json']
#### `--accept-eula -e`
Acceptez-vous les termes du contrat de licence ? Oui/non.
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
Supprimer le Cluster SQL Server Big Data.
```bash
mssqlctl cluster delete --name -n 
                        [--force -f]
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
