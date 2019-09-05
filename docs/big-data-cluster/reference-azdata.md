---
title: Informations de référence sur azdata
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7f4cecd27865b069764944021639ae1a2e553d76
ms.sourcegitcommit: 0c6c1555543daff23da9c395865dafd5bb996948
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70304717"
---
# <a name="azdata"></a>azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
|[azdata notebook](reference-azdata-notebook.md) | Commandes permettant d’afficher, d’exécuter et de gérer des notebooks à partir d’un terminal. |
|[azdata sql](reference-azdata-sql.md) | L’interface CLI SQL DB permet à l’utilisateur d’interagir avec SQL Server via T-SQL. |
|[azdata app](reference-azdata-app.md) | Créer, supprimer, exécuter et gérer des applications. |
|[azdata bdc](reference-azdata-bdc.md) | Sélectionner, gérer et utiliser des clusters Big Data SQL Server. |
|[contrôle azdata](reference-azdata-control.md) | Créer, supprimer et gérer des plans de contrôle. |
[azdata login](#azdata-login) | Se connecter au point de terminaison du contrôleur du cluster.
[azdata logout](#azdata-logout) | Se déconnecter du cluster.
## <a name="azdata-login"></a>azdata login
Quand votre cluster est déployé, il indique le point de terminaison du contrôleur lors du déploiement, que vous devez utiliser pour vous connecter.  Si vous ne connaissez pas le point de terminaison du contrôleur, vous pouvez vous connecter en faisant en sorte que la configuration Kube de votre cluster se trouve sur votre système dans l’emplacement par défaut <user home>/.kube/config ou en utilisant la variable d’environnement KUBECONFIG, par exemple exportez KUBECONFIG=path/to/.kube/configg.
```bash
azdata login [--cluster-name -n] 
             [--controller-username -u]  
             [--controller-endpoint -e]  
             [--accept-eula -a]
```
### <a name="examples"></a>Exemples
Se connecter de façon interactive. Le nom du cluster est toujours demandé s’il n’est pas spécifié comme argument. Si les variables d’environnement CONTROLLER_USERNAME, CONTROLLER_PASSWORD et ACCEPT_EULA sont définies sur votre système, elles ne sont pas demandées. Si vous avez la configuration Kube sur votre système ou si vous utilisez la variable d’environnement KUBECONFIG pour spécifier le chemin de la configuration, l’expérience interactive tente d’abord d’utiliser la configuration, puis vous demande les informations si la configuration échoue.
```bash
azdata login
```
Se connecter (de façon non interactive). Connectez-vous avec le nom du cluster, le nom d’utilisateur du contrôleur, le point de terminaison du contrôleur et l’acceptation du CLUF définis comme arguments. La variable d’environnement CONTROLLER_PASSWORD doit être définie.  Si vous ne voulez pas spécifier le point de terminaison du contrôleur, placez la configuration Kube sur votre machine dans l’emplacement par défaut <user home>/.kube/config ou utilisez la variable d’environnement KUBECONFIG, par exemple exportez KUBECONFIG=path/to/.kube/configg.
```bash
azdata login --cluster-name ClusterName --controller-user johndoe@contoso.com  --controller-endpoint https://<ip>:30080 --accept-eula yes
```
Connectez-vous avec la configuration Kube sur la machine, et les variables d’environnement définies pour CONTROLLER_USERNAME, CONTROLLER_PASSWORD et ACCEPT_EULA.
```bash
azdata login -n ClusterName
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--cluster-name -n`
Nom du cluster.
#### `--controller-username -u`
Utilisateur du compte. Si vous ne voulez pas utiliser cet argument, vous pouvez définir la variable d’environnement CONTROLLER_USERNAME.
#### `--controller-endpoint -e`
Point de terminaison du contrôleur du cluster « https://host:port  ». Si vous ne voulez pas utiliser cet argument, vous pouvez utiliser la configuration Kube sur votre machine. Vérifiez que la configuration se trouve à l’emplacement par défaut <user home>/.kube/config ou utilisez la variable d’environnement KUBECONFIG.
#### `--accept-eula -a`
Acceptez-vous les termes du contrat de licence ? [oui/non]. Si vous ne voulez pas utiliser cet argument, vous pouvez définir la variable d’environnement ACCEPT_EULA sur « oui ». 
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
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-logout"></a>azdata logout
Se déconnecter du cluster.
```bash
azdata logout 
```
### <a name="examples"></a>Exemples
Déconnectez cet utilisateur.
```bash
azdata logout
```
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

- Pour plus d’informations sur l’installation de l’outil **azdata**, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
