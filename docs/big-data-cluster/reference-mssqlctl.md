---
title: mssqlctl reference
titleSuffix: SQL Server 2019 big data clusters
description: Article de référence pour les commandes de mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: be1ece46bd171370a91273c832bf89a0bf426cd3
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018365"
---
# <a name="mssqlctl"></a>mssqlctl

L’article suivant fournit la référence pour le **mssqlctl** outil pour les clusters de données volumineuses de SQL Server 2019 (version préliminaire).

## <a id="commands"></a> Commandes

|||
|---|---|
| [app](reference-mssqlctl-app.md) | Créer, supprimer, exécuter et gérer des applications. |
| [cluster](reference-mssqlctl-cluster.md) | Sélectionnez, gérer et exploiter des clusters. |
| [login](#login) | Connectez-vous au cluster. |
| [logout](#logout) | Se déconnecter de cluster. |
| [storage](reference-mssqlctl-storage.md) | Gérer le stockage de cluster. |

## <a id="login"></a> mssqlctl login

Connectez-vous au cluster.

```
mssqlctl login
   --endpoint
   --password
   --username
```

### <a name="parameters"></a>Paramètres

| Paramètre | Description |
|---|---|
|**--endpoint -e**| Cluster hôte et le port (ex) `http://host:port"`. |
|**--password -p**| Informations d’identification de mot de passe. |
|**--username -u**| Compte d’utilisateur. |

### <a name="examples"></a>Exemples

Connectez-vous de manière interactive.

```
mssqlctl login
```

Connectez-vous avec le nom d’utilisateur et mot de passe.

```
mssqlctl login -u johndoe@contoso.com -p VerySecret
```

Connectez-vous avec nom d’utilisateur, mot de passe et le point de terminaison de cluster.

```
mssqlctl login -u johndoe@contoso.com -p VerySecret --endpoint https://host.com:12800
```

## <a id="logout"></a> déconnexion de mssqlctl

Se déconnecter de cluster.

```
mssqlctl logout
   --username
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--username -u** | Utilisateur du compte, s’il est manquant, le compte actif en cours de déconnexion. |

### <a name="examples"></a>Exemples

Déconnectez-vous de cet utilisateur.

```
mssqlctl logout --username admin
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).