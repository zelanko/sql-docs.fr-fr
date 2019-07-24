---
title: Référence du lot azdata BDC Spark
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de traitement par lots azdata BDC Spark.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6e242b26f439b49dbf0b3cf5ab50ea46c273f45f
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426159"
---
# <a name="azdata-bdc-spark-batch"></a>lot azdata BDC Spark

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes de **traitement par lots de BDC** dans l’outil **azdata** . Pour plus d’informations sur les autres commandes **azdata** , consultez la [référence azdata](reference-azdata.md)

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[création d’un lot azdata BDC Spark](#azdata-bdc-spark-batch-create) | Créez un lot Spark.
[Liste des lots azdata BDC Spark](#azdata-bdc-spark-batch-list) | Répertorie tous les lots dans Spark.
[informations sur le lot azdata BDC Spark](#azdata-bdc-spark-batch-info) | Obtenir des informations sur un lot Spark actif.
[Journal des lots azdata BDC Spark](#azdata-bdc-spark-batch-log) | Obtenir des journaux d’exécution pour un lot Spark.
[État du lot azdata BDC Spark](#azdata-bdc-spark-batch-state) | Obtenir l’état d’exécution d’un lot Spark.
[suppression d’un lot azdata BDC Spark](#azdata-bdc-spark-batch-delete) | Suppression d’un lot Spark.
## <a name="azdata-bdc-spark-batch-create"></a>création d’un lot azdata BDC Spark
Cela crée un nouveau travail Spark batch qui exécute le code fourni.
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
Créez un lot Spark.
```bash
azdata spark batch create --code "2+2"
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--file -f`
Chemin d’accès du fichier à exécuter.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--class-name -c`
Nom de la classe à exécuter lors du passage d’un ou de plusieurs fichiers jar.
#### `--arguments -a`
Liste d’arguments.  Pour transmettre une liste JSON, encodez les valeurs.  Exemple: «["entry1», «Entry2»]».
#### `--jar-files -j`
Liste des chemins d’accès aux fichiers jar.  Pour transmettre une liste JSON, encodez les valeurs.  Exemple: «["entry1», «Entry2»]».
#### `--py-files -p`
Liste des chemins d’accès de fichier Python.  Pour transmettre une liste JSON, encodez les valeurs.  Exemple: «["entry1», «Entry2»]».
#### `--files`
Liste des chemins d’accès aux fichiers.  Pour transmettre une liste JSON, encodez les valeurs.  Exemple: «["entry1», «Entry2»]».
#### `--driver-memory`
Quantité de mémoire à allouer au pilote.  Spécifiez les unités dans le cadre de la valeur.  Exemple 512M ou 2G.
#### `--driver-cores`
Quantité de cœurs de processeur à allouer au pilote.
#### `--executor-memory`
Quantité de mémoire à allouer à l’exécuteur.  Spécifiez les unités dans le cadre de la valeur.  Exemple 512M ou 2G.
#### `--executor-cores`
Quantité de cœurs de processeur à allouer à l’exécuteur.
#### `--executor-count`
Nombre d’instances de l’exécuteur à exécuter.
#### `--archives`
Liste des chemins d’archives.  Pour transmettre une liste JSON, encodez les valeurs.  Exemple: «["entry1», «Entry2»]».
#### `--queue -q`
Nom de la file d’attente Spark dans laquelle exécuter la session.
#### `--name -n`
Nom de la session Spark.
#### `--config`
Liste de paires nom/valeur contenant des valeurs de configuration Spark.  Encodé en tant que dictionnaire JSON.  Exemple: «{» Name»: «value», «nom2»: «value2»}».
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
## <a name="azdata-bdc-spark-batch-list"></a>Liste des lots azdata BDC Spark
Répertorie tous les lots dans Spark.
```bash
azdata bdc spark batch list 
```
### <a name="examples"></a>Exemples
Répertorie tous les lots actifs.
```bash
azdata spark batch list
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
## <a name="azdata-bdc-spark-batch-info"></a>informations sur le lot azdata BDC Spark
Cela obtient les informations pour un lot Spark avec l’ID donné.  L’ID de lot est retourné à partir de «Spark batch Create».
```bash
azdata bdc spark batch info --batch-id -i 
                            
```
### <a name="examples"></a>Exemples
Obtenir les informations de lot pour le lot avec l’ID 0.
```bash
azdata spark batch info --batch-id 0
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--batch-id -i`
Numéro d’identification du lot Spark.
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
## <a name="azdata-bdc-spark-batch-log"></a>Journal des lots azdata BDC Spark
Cela obtient les entrées de journal batch pour un lot Spark avec l’ID donné.  L’ID de lot est retourné à partir de «Spark batch Create».
```bash
azdata bdc spark batch log --batch-id -i 
                           
```
### <a name="examples"></a>Exemples
Obtient le journal des lots pour le lot avec l’ID 0.
```bash
azdata spark batch log --batch-id 0
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--batch-id -i`
Numéro d’identification du lot Spark.
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
## <a name="azdata-bdc-spark-batch-state"></a>État du lot azdata BDC Spark
Cela obtient l’état du lot pour un lot Spark avec l’ID donné.  L’ID de lot est retourné à partir de «Spark batch Create».
```bash
azdata bdc spark batch state --batch-id -i 
                             
```
### <a name="examples"></a>Exemples
Obtient l’état du lot pour le lot avec l’ID 0.
```bash
azdata spark batch state --batch-id 0
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--batch-id -i`
Numéro d’identification du lot Spark.
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
## <a name="azdata-bdc-spark-batch-delete"></a>suppression d’un lot azdata BDC Spark
Cela supprime un lot Spark. L’ID de lot est retourné à partir de «Spark batch Create».
```bash
azdata bdc spark batch delete --batch-id -i 
                              
```
### <a name="examples"></a>Exemples
Supprimer un lot.
```bash
azdata spark batch delete --batch-id 0
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--batch-id -i`
Numéro d’identification du lot Spark.
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

Pour plus d’informations sur les autres commandes **azdata** , consultez [référence azdata](reference-azdata.md). Pour plus d’informations sur l’installation de l’outil **azdata** , consultez [installer azdata pour gérer les clusters SQL Server 2019 Big Data](deploy-install-azdata.md).
