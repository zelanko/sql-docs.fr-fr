---
title: Référence mssqlctl
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de mssqlctl.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: acc25e6b3deca199ad774378318e17991614dcaa
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779239"
---
# <a name="mssqlctl"></a>mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **mssqlctl** outil pour [clusters de données volumineuses de SQL Server 2019 (version préliminaire)](big-data-cluster-overview.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
|[mssqlctl app](reference-mssqlctl-app.md) | Créer, supprimer, exécuter et gérer des applications. |
|[mssqlctl cluster](reference-mssqlctl-cluster.md) | Sélectionnez, gérer et exploiter des clusters. |
[mssqlctl login](#mssqlctl-login) | Connectez-vous au point de terminaison de contrôleur du cluster.
[déconnexion de mssqlctl](#mssqlctl-logout) | Se déconnecter de cluster.
## <a name="mssqlctl-login"></a>mssqlctl login
Lorsque votre cluster est déployé, il répertorie le point de terminaison du contrôleur au cours du déploiement, vous devez utiliser pour vous connecter.  Si vous ne connaissez pas le point de terminaison du contrôleur, vous pouvez la connexion en utilisant la configuration de kube de votre cluster sur votre système dans l’emplacement par défaut de <user home>/.kube/config ou utiliser le var env KUBECONFIG, par exemple, exporter KUBECONFIG=path/to/.kube/config.
```bash
mssqlctl login [--cluster-name -n] 
               [--controller-username -u]  
               [--controller-endpoint -e]  
               [--accept-eula -a]
```
### <a name="examples"></a>Exemples
Connectez-vous de manière interactive. Nom du cluster est toujours invité à indiquer si n’est pas spécifié en tant qu’argument. Si vous avez les variables env CONTROLLER_USERNAME, CONTROLLER_PASSWORD et ACCEPT_EULA sur votre système, ces pas demandera. Si vous avez la configuration de kube sur votre système ou que vous utilisez le var env KUBECONFIG pour spécifier le chemin d’accès à la configuration, l’expérience interactive tente tout d’abord utiliser la configuration et vous demande si la configuration échoue.
```bash
mssqlctl login
```
Se connecter (en mode non interactif). Connectez-vous avec le nom du cluster, nom d’utilisateur de contrôleur, point de terminaison de contrôleur et l’acceptation du CLUF défini en tant qu’arguments. La variable d’environnement CONTROLLER_PASSWORD doit être définie.  Si vous ne souhaitez pas spécifier le point de terminaison du contrôleur, demandez à la configuration de kube sur votre ordinateur dans l’emplacement par défaut de <user home>/.kube/config ou utiliser le var env KUBECONFIG, par exemple, exporter KUBECONFIG=path/to/.kube/config.
```bash
mssqlctl login --cluster-name ClusterName --controller-user johndoe@contoso.com  --controller-endpoint https://<ip>:30080 --accept-eula yes
```
Connectez-vous avec le fichier de configuration kube sur l’ordinateur et var env définie pour CONTROLLER_USERNAME, CONTROLLER_PASSWORD et ACCEPT_EULA.
```bash
mssqlctl login -n ClusterName
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--cluster-name -n`
Nom du cluster.
#### `--controller-username -u`
Compte d’utilisateur. Si vous ne souhaitez pas utiliser cette arg, vous pouvez définir la variable d’environnement CONTROLLER_USERNAME.
#### `--controller-endpoint -e`
Point de terminaison de contrôleur de cluster « https://host:port». Si vous ne souhaitez pas utiliser cette arg, vous pouvez utiliser la configuration de kube sur votre ordinateur. Vérifiez que la configuration se trouve à l’emplacement par défaut de <user home>/.kube/config ou utilisez le KUBECONFIG env-var.
#### `--accept-eula -a`
Acceptez-vous les termes du contrat de licence ? Oui/non. Si vous ne souhaitez pas utiliser cette arg, vous pouvez définir la variable d’environnement ACCEPT_EULA sur « Oui »
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
## <a name="mssqlctl-logout"></a>déconnexion de mssqlctl
Se déconnecter de cluster.
```bash
mssqlctl logout 
```
### <a name="examples"></a>Exemples
Déconnectez-vous de cet utilisateur.
```bash
mssqlctl logout
```
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

Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).