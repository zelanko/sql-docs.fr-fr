---
title: Référence du contrôle azdata
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de contrôle azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2ce02ef0b212070b4a52944e055404137c78c98b
ms.sourcegitcommit: 0c6c1555543daff23da9c395865dafd5bb996948
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70304721"
---
# <a name="azdata-control"></a>contrôle azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Cet article est un article de référence pour **azdata**. 

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[création de contrôle azdata](#azdata-control-create) | Créer un plan de contrôle.
[suppression du contrôle azdata](#azdata-control-delete) | Supprimer le plan de contrôle.
## <a name="azdata-control-create"></a>création de contrôle azdata
Créer un plan de contrôle : la configuration de Kube est requise sur votre système avec les variables d’environnement suivantes [« CONTROLLER_USERNAME », « CONTROLLER_PASSWORD », « MSSQL_SA_PASSWORD », « KNOX_PASSWORD »].
```bash
azdata control create [--name -n] 
                      [--config-profile -c]  
                      [--accept-eula -a]  
                      [--node-label -l]  
                      [--force -f]
```
### <a name="examples"></a>Exemples
Contrôle du déploiement.
```bash
azdata control create
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--name -n`
Nom du plan de contrôle, utilisé pour les espaces de noms kubernetes.
#### `--config-profile -c`
Profil de configuration de cluster, utilisé pour le déploiement du cluster : ['AKS-dev-test', 'kubeadm-Prod', 'minikube-dev-test', 'kubeadm-dev-test']
#### `--accept-eula -a`
Acceptez-vous les termes du contrat de licence ? [oui/non]. Si vous ne voulez pas utiliser cet argument, vous pouvez définir la variable d’environnement ACCEPT_EULA sur « oui ». 
#### `--node-label -l`
Étiquette de nœud, utilisée pour désigner les nœuds vers lesquels effectuer le déploiement.
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
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.
## <a name="azdata-control-delete"></a>suppression du contrôle azdata
Supprimer le plan de contrôle : la configuration de Kube est requise sur votre système.
```bash
azdata control delete --name -n 
                      [--force -f]
```
### <a name="examples"></a>Exemples
Contrôle du déploiement.
```bash
azdata control delete
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--name -n`
Nom du plan de contrôle, utilisé pour l’espace de noms kubernetes.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--force -f`
Forcer le plan de contrôle de suppression.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur les autres commandes **azdata**, consultez [azdata reference](reference-azdata.md). 

- Pour plus d’informations sur l’installation de l’outil **azdata**, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
