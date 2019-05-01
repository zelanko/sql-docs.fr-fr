---
title: Référence mssqlctl
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ebd3b63d641c77dae1afbff21264ec4fe34df4d0
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473472"
---
# <a name="mssqlctl"></a>mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **mssqlctl** outil pour [clusters de données volumineuses de SQL Server 2019 (version préliminaire)](big-data-cluster-overview.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
|[mssqlctl app](reference-mssqlctl-app.md) | Créer, supprimer, exécuter et gérer des applications. |
|[mssqlctl cluster](reference-mssqlctl-cluster.md) | Sélectionnez, gérer et exploiter des clusters. |
[mssqlctl login](#mssqlctl-login) | Connectez-vous au cluster.
[déconnexion de mssqlctl](#mssqlctl-logout) | Se déconnecter de cluster.
|[stockage de mssqlctl](reference-mssqlctl-storage.md) | Gérer le stockage de cluster. |
## <a name="mssqlctl-login"></a>mssqlctl login
Connectez-vous au cluster.
```bash
mssqlctl login [--username -u] 
               [--password -p]  
               [--endpoint -e]
```
### <a name="examples"></a>Exemples
Connectez-vous de manière interactive.
```bash
mssqlctl login
```
Connectez-vous avec le nom d’utilisateur et mot de passe.
```bash
mssqlctl login -u johndoe@contoso.com -p VerySecret
```
Connectez-vous avec nom d’utilisateur, mot de passe et le point de terminaison de cluster.
```bash
mssqlctl login -u johndoe@contoso.com -p VerySecret --endpoint https://host.com:12800
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--username -u`
Compte d’utilisateur.
#### `--password -p`
Informations d’identification de mot de passe.
#### `--endpoint -e`
Cluster hôte et le port (ex) « http://host:port».
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