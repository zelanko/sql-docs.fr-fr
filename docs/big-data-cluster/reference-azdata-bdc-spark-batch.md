---
title: azdata bdc spark batch reference
description: Article de référence sur les commandes azdata bdc spark batch.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5d141669313a90bd04cda2e54d5a9e9d5a3c68f6
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75258631"
---
# <a name="azdata-bdc-spark-batch"></a>azdata bdc spark batch

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

L’article suivant fournit des références sur les commandes `bdc spark batch` disponibles dans l’outil `azdata`. Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata bdc spark batch create](#azdata-bdc-spark-batch-create) | Créez un nouveau lot Spark.
[azdata bdc spark batch list](#azdata-bdc-spark-batch-list) | Répertoriez tous les lots dans Spark.
[azdata bdc spark batch info](#azdata-bdc-spark-batch-info) | Obtenez des informations sur un lot Spark actif.
[azdata bdc spark batch log](#azdata-bdc-spark-batch-log) | Obtenez des journaux d’exécution pour un lot Spark.
[azdata bdc spark batch state](#azdata-bdc-spark-batch-state) | Obtenez un état d’exécution pour un lot Spark.
[azdata bdc spark batch delete](#azdata-bdc-spark-batch-delete) | Supprimez un lot Spark.
## <a name="azdata-bdc-spark-batch-create"></a>azdata bdc spark batch create
Cela crée un nouveau lot de tâches Spark qui exécute le code fourni.
```bash
azdata bdc spark batch create --file -f 
                              [--class-name -c]  
                              [--arguments -a]  
                              [--jar-files -j]  
                              [--py-files -p]  
                              [--files]  
                              [--driver-memory]  
                              [--driver-cores]  
                              [--executor-memory]  
                              [--executor-cores]  
                              [--executor-count]  
                              [--archives]  
                              [--queue -q]  
                              [--name -n]  
                              [--config]
```
### <a name="examples"></a>Exemples
Créez un nouveau lot Spark.
```bash
azdata spark batch create --code "2+2"
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--file -f`
Chemin d’accès au fichier à exécuter.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--class-name -c`
Nom de la classe à exécuter lors du passage d’un ou de plusieurs fichiers jar.
#### `--arguments -a`
Liste d'arguments.  Pour transmettre dans une liste JSON, encodez les valeurs.  Exemple : « [« entry1 », « entry2 »] ».
#### `--jar-files -j`
Liste des chemins d’accès aux fichiers jar.  Pour transmettre dans une liste JSON, encodez les valeurs.  Exemple : « [« entry1 », « entry2 »] ».
#### `--py-files -p`
Liste des chemins d’accès de fichier Python.  Pour transmettre dans une liste JSON, encodez les valeurs.  Exemple : « [« entry1 », « entry2 »] ».
#### `--files`
Liste des chemins d’accès de fichier.  Pour transmettre dans une liste JSON, encodez les valeurs.  Exemple : « [« entry1 », « entry2 »] ».
#### `--driver-memory`
Quantité de mémoire à allouer au pilote.  Spécifiez les unités dans le cadre de la valeur.  Exemple 512 M ou 2 G.
#### `--driver-cores`
Quantité de cœurs UC à allouer au pilote.
#### `--executor-memory`
Quantité de mémoire à allouer à l’exécuteur.  Spécifiez les unités dans le cadre de la valeur.  Exemple 512 M ou 2 G.
#### `--executor-cores`
Quantité de cœurs UC à allouer à l’exécuteur.
#### `--executor-count`
Nombre d'instances de l’exécuteur à exécuter.
#### `--archives`
Liste des chemins d’accès à l’archive.  Pour transmettre dans une liste JSON, encodez les valeurs.  Exemple : « [« entry1 », « entry2 »] ».
#### `--queue -q`
Nom de la file d’attente Spark dans laquelle exécuter la session.
#### `--name -n`
Nom de la session Spark.
#### `--config`
Liste de paires nom/valeur contenant des valeurs de configuration Spark.  Encodé en tant que dictionnaire JSON.  Exemple : « {"name":"value", "name2":"value2"} ».
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-bdc-spark-batch-list"></a>azdata bdc spark batch list
Répertoriez tous les lots dans Spark.
```bash
azdata bdc spark batch list 
```
### <a name="examples"></a>Exemples
Répertoriez tous les lots actifs.
```bash
azdata spark batch list
```
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-bdc-spark-batch-info"></a>azdata bdc spark batch info
Permet d’obtenir les informations pour un lot Spark avec l’ID donné.  L’ID de lot est retourné à partir de « spark batch create ».
```bash
azdata bdc spark batch info --batch-id -i 
          ```
### Examples
Get batch info for batch with ID of 0.
```bash
azdata spark batch info --batch-id 0
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--batch-id -i`
Numéro d’ID du lot Spark.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-bdc-spark-batch-log"></a>azdata bdc spark batch log
Permet d’obtenir les entrées du journal de lots pour un lot Spark avec l’ID donné.  L’ID de lot est retourné à partir de « spark batch create ».
```bash
azdata bdc spark batch log --batch-id -i 
         ```
### Examples
Get batch log for batch with ID of 0.
```bash
azdata spark batch log --batch-id 0
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--batch-id -i`
Numéro d’ID du lot Spark.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-bdc-spark-batch-state"></a>azdata bdc spark batch state
Permet d’obtenir l’état du lot pour un lot Spark avec l’ID donné.  L’ID de lot est retourné à partir de « spark batch create ».
```bash
azdata bdc spark batch state --batch-id -i 
           ```
### Examples
Get batch state for batch with ID of 0.
```bash
azdata spark batch state --batch-id 0
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--batch-id -i`
Numéro d’ID du lot Spark.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-bdc-spark-batch-delete"></a>azdata bdc spark batch delete
Cela supprime un lot Spark. L’ID de lot est retourné à partir de « spark batch create ».
```bash
azdata bdc spark batch delete --batch-id -i 
            ```
### Examples
Delete a batch.
```bash
azdata spark batch delete --batch-id 0
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--batch-id -i`
Numéro d’ID du lot Spark.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md). Pour plus d’informations sur l’installation de l’outil `azdata`, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
