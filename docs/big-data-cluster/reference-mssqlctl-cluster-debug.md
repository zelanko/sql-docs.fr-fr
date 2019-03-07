---
title: mssqlctl cluster debug reference
titleSuffix: SQL Server 2019 big data clusters
description: Article de référence pour les commandes de cluster mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9312e972dfcb439f4ef19a4e72d8d66454622096
ms.sourcegitcommit: d7ed341b2c635dcdd6b0f5f4751bb919a75a6dfe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57527232"
---
# <a name="mssqlctl-cluster-debug"></a>mssqlctl cluster debug

L’article suivant fournit la référence pour le **débogage de cluster** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a id="commands"></a> Commandes

|||
|---|---|
| [copy-logs](#copy-logs) | Copier les journaux. |
| [dump](#dump) | Vidage de journalisation de déclencheur. |

## <a id="copy-logs"></a> journaux de copie du débogage de cluster

Copier les journaux.

```
mssqlctl cluster debug copy-logs
   --namespace
   [--container]
   [--pod]
   [--target-folder]
   [--timeout]
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--namespace -n** | Nom du cluster, utilisé pour l’espace de noms kubernetes. Obligatoire. |
| **--container -c** | Copier les journaux pour les conteneurs avec un nom similaire, facultatif, par défaut copie des journaux de tous les conteneurs. Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, dernier un sera utilisé. |
| **--pod -p** | Copier les journaux pour les pods avec un nom similaire. Facultatif, par défaut, les journaux des copies pour tous les pods. Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, dernier un sera utilisé. |
| **--target-folder -d** | Chemin du dossier cible pour copier les journaux. Facultatif, par défaut crée le résultat dans le dossier local.  Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, dernier un sera utilisé. |
| **--timeout -t** | Le nombre de secondes d’attente de la commande se termine. La valeur par défaut est 0, ce qui est illimité. |

## <a id="dump"></a> vidage de débogage de cluster

Vidage de journalisation de déclencheur.

```
mssqlctl cluster debug dump
   [--container]
   [--namespace]
   --target-folder
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--container -c** | Copier les journaux pour les conteneurs avec un nom similaire, facultatif, par défaut copie des journaux de tous les conteneurs. Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, dernier un sera utilisé.  Valeurs autorisées : mssql-controller. |
| **--namespace -n** | Nom du cluster, utilisé pour l’espace de noms kubernetes. Obligatoire. |
| **--target-folder -d** | Chemin du dossier cible pour copier les journaux. Facultatif, par défaut crée le résultat dans le dossier local.  Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, dernier un sera utilisé.  Par défaut : `./output/dump`. Obligatoire. |

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).