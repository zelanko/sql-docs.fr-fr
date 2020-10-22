---
title: Informations de référence sur azdata arc resource
titleSuffix: SQL Server big data clusters
description: Article d’informations de référence sur les commandes azdata arc resource.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 20f96bb8ce3d88e438c28b28f49deff3b5b3054c
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92358697"
---
# <a name="azdata-arc-resource"></a>azdata arc resource

S'applique à l'[!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]

L’article suivant fournit des informations de référence sur les commandes **sql ** dans l’outil **azdata**. Pour plus d’informations sur les commandes **azdata**, consultez [azdata reference](reference-azdata.md)

## <a name="commands"></a>Commandes

|Commande|Description|
| --- | --- |
[azdata arc resource-kind list](#azdata-arc-resource-kind-list) | Répertorie les types de ressources personnalisés disponibles pour Arc qui peuvent être définis et créés.
[azdata arc resource-kind get](#azdata-arc-resource-kind-get) | Obtient le fichier de modèle du type de ressource Arc.
## <a name="azdata-arc-resource-kind-list"></a>azdata arc resource-kind list
Répertorie les types de ressources personnalisés disponibles pour Arc qui peuvent être définis et créés. Après la création de la liste, vous pouvez passer à l’obtention du fichier de modèle nécessaire pour définir ou créer cette ressource personnalisée.
```bash
azdata arc resource-kind list 
```
### <a name="examples"></a>Exemples
Exemple de commande permettant de répertorier les types de ressources personnalisés disponibles pour Arc.
```bash
azdata arc resource-kind list
```
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-arc-resource-kind-get"></a>azdata arc resource-kind get
Obtient le fichier de modèle du type de ressource Arc.
```bash
azdata arc resource-kind get --kind -k 
                             [--dest -d]
```
### <a name="examples"></a>Exemples
Exemple de commande pour obtenir un fichier de modèle CRD de type de ressource Arc.
```bash
azdata arc resource-kind get --kind sqldb
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--kind -k`
Type de ressource arc pour lequel vous souhaitez obtenir le fichier de modèle.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--dest -d`
Répertoire dans lequel vous souhaitez placer les fichiers de modèle.
`template`
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres commandes **azdata**, consultez [azdata reference](reference-azdata.md). 

Pour plus d’informations sur l’installation de l’outil **azdata**, consultez [Installer azdata](..\install\deploy-install-azdata.md).

