---
title: Référence azdata
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a8136c85f8c32e08423f3d199a021d4f60353b39
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425989"
---
# <a name="azdata"></a>azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur l’outil **azdata** pour les [clusters SQL Server 2019 Big Data (version préliminaire)](big-data-cluster-overview.md). Pour plus d’informations sur l’installation de l’outil **azdata** , consultez [installer azdata pour gérer les clusters SQL Server 2019 Big Data](deploy-install-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
|[application azdata](reference-azdata-app.md) | Créer, supprimer, exécuter et gérer des applications. |
|[azdata BDC](reference-azdata-bdc.md) | Sélectionner, gérer et utiliser des clusters de données SQL Server Big Data. |
|[bloc-notes azdata](reference-azdata-notebook.md) | Commandes permettant d’afficher, d’exécuter et de gérer les blocs-notes à partir d’un terminal. |
[connexion azdata](#azdata-login) | Connectez-vous au point de terminaison du contrôleur du cluster.
[déconnexion azdata](#azdata-logout) | Déconnectez-vous du cluster.
|[azdata SQL](reference-azdata-sql.md) | L’interface CLI de SQL DB permet à l’utilisateur d’interagir avec SQL Server via T-SQL. |
## <a name="azdata-login"></a>connexion azdata
Lorsque votre cluster est déployé, il répertorie le point de terminaison de contrôleur lors du déploiement, que vous devez utiliser pour vous connecter.  Si vous ne connaissez pas le point de terminaison du contrôleur, vous pouvez vous connecter en faisant en sorte que la configuration Kube de votre cluster <user home>se trouve dans l’emplacement par défaut de/.Kube/config ou utiliser la var KUBECONFIG env, c.-à-d. Export KUBECONFIG = Path/to/. Kube/config.
```bash
azdata login [--cluster-name -n] 
             [--controller-username -u]  
             [--controller-endpoint -e]  
             [--accept-eula -a]
```
### <a name="examples"></a>Exemples
Connectez-vous de manière interactive. Le nom du cluster est toujours demandé s’il n’est pas spécifié en tant qu’argument. Si les variables CONTROLLER_USERNAME, CONTROLLER_PASSWORD et ACCEPT_EULA env sont définies sur votre système, celles-ci ne seront pas demandées. Si vous avez la configuration Kube sur votre système ou si vous utilisez la variable KUBECONFIG env var pour spécifier le chemin d’accès à la configuration, l’expérience interactive tente d’abord d’utiliser la configuration, puis vous demande si la configuration échoue.
```bash
azdata login
```
Connectez-vous (de manière non interactive). Connectez-vous avec le nom du cluster, le nom d’utilisateur du contrôleur, le point de terminaison du contrôleur et l’acceptation du CLUF définis comme arguments. La variable d’environnement CONTROLLER_PASSWORD doit être définie.  Si vous ne souhaitez pas spécifier le point de <user home>terminaison du contrôleur, utilisez la configuration Kube sur votre ordinateur à l’emplacement par défaut/.Kube/config ou utilisez la variable KUBECONFIG env, c’est-à-dire Export KUBECONFIG = Path/to/. Kube/config.
```bash
azdata login --cluster-name ClusterName --controller-user johndoe@contoso.com  --controller-endpoint https://<ip>:30080 --accept-eula yes
```
Connectez-vous avec Kube config sur l’ordinateur et env var définie pour CONTROLLER_USERNAME, CONTROLLER_PASSWORD et ACCEPT_EULA.
```bash
azdata login -n ClusterName
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--cluster-name -n`
Nom du cluster.
#### `--controller-username -u`
Utilisateur du compte. Si vous ne souhaitez pas utiliser ce ARG, vous pouvez définir la variable d’environnement CONTROLLER_USERNAME.
#### `--controller-endpoint -e`
Point de terminaison du https://host:port contrôleur de cluster «». Si vous ne souhaitez pas utiliser ce ARG, vous pouvez utiliser la configuration Kube sur votre ordinateur. Vérifiez que la configuration se trouve à l’emplacement par défaut <user home>de/.Kube/config ou utilisez la var KUBECONFIG env.
#### `--accept-eula -a`
Acceptez-vous les termes du contrat de licence? [Oui/non]. Si vous ne souhaitez pas utiliser ce ARG, vous pouvez définir la variable d’environnement ACCEPT_EULA sur «Yes». Vous pouvez consulter les termes du contrat de licence de https://aka.ms/azdata-eula ce produit à l’adresse.
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
## <a name="azdata-logout"></a>déconnexion azdata
Déconnectez-vous du cluster.
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

Pour plus d’informations sur l’installation de l’outil **azdata** , consultez [installer azdata pour gérer les clusters SQL Server 2019 Big Data](deploy-install-azdata.md).
