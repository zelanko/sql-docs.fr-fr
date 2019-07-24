---
title: Référence de session azdata BDC Spark
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de session azdata BDC Spark.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 20b7ac3dcf72482e80278ce0f0df922026232a6d
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426099"
---
# <a name="azdata-bdc-spark-session"></a>session azdata BDC Spark

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

L’article suivant fournit des informations de référence sur les commandes de la **session Spark BDC** dans l’outil **azdata** . Pour plus d’informations sur les autres commandes **azdata** , consultez la [référence azdata](reference-azdata.md)

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[création de la session azdata BDC Spark](#azdata-bdc-spark-session-create) | Créez une nouvelle session Spark.
[liste de sessions azdata BDC Spark](#azdata-bdc-spark-session-list) | Répertorie toutes les sessions actives dans Spark.
[informations de session azdata BDC Spark](#azdata-bdc-spark-session-info) | Obtenir des informations sur une session Spark active.
[Journal de session azdata BDC Spark](#azdata-bdc-spark-session-log) | Obtenir des journaux d’exécution pour une session Spark active.
[État de session azdata BDC Spark](#azdata-bdc-spark-session-state) | Obtenir l’état d’exécution d’une session Spark active.
[suppression de la session azdata BDC Spark](#azdata-bdc-spark-session-delete) | Supprimer une session Spark.
## <a name="azdata-bdc-spark-session-create"></a>création de la session azdata BDC Spark
Cela crée une nouvelle session Spark interactive. L’appelant doit spécifier le type de session Spark. Cette session se situe au-delà de la durée de vie d’une exécution azdata et doit être supprimée avec’Spark session Delete'
```bash
azdata bdc spark session create [--session-kind -k] 
                                [--jar-files -j]  
                                [--py-files -p]  
                                [--files -f]  
                                [--driver-memory]  
                                [--driver-cores]  
                                [--executor-memory]  
                                [--executor-cores]  
                                [--executor-count]  
                                [--archives -a]  
                                [--queue -q]  
                                [--name -n]  
                                [--config -c]  
                                [--timeout-seconds -t]
```
### <a name="examples"></a>Exemples
Créez une session.
```bash
azdata spark session create --session-kind pyspark
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--session-kind -k`
Nom du type de session à créer.  L’une des Spark, pyspark, sparkr ou SQL.
#### `--jar-files -j`
Liste des chemins d’accès aux fichiers jar.  Pour transmettre une liste JSON, encodez les valeurs.  Exemple: «["entry1», «Entry2»]».
#### `--py-files -p`
Liste des chemins d’accès de fichier Python.  Pour transmettre une liste JSON, encodez les valeurs.  Exemple: «["entry1», «Entry2»]».
#### `--files -f`
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
#### `--archives -a`
Liste des chemins d’archives.  Pour transmettre une liste JSON, encodez les valeurs.  Exemple: «["entry1», «Entry2»]».
#### `--queue -q`
Nom de la file d’attente Spark dans laquelle exécuter la session.
#### `--name -n`
Nom de la session Spark.
#### `--config -c`
Liste de paires nom/valeur contenant des valeurs de configuration Spark.  Encodé en tant que dictionnaire JSON.  Exemple: «{» Name»: «value», «nom2»: «value2»}».
#### `--timeout-seconds -t`
Délai d’inactivité de la session en secondes.
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
## <a name="azdata-bdc-spark-session-list"></a>liste de sessions azdata BDC Spark
Répertorie toutes les sessions actives dans Spark.
```bash
azdata bdc spark session list 
```
### <a name="examples"></a>Exemples
Répertorie toutes les sessions actives.
```bash
azdata spark session list
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
## <a name="azdata-bdc-spark-session-info"></a>informations de session azdata BDC Spark
Cela obtient les informations de session pour une session Spark active avec l’ID donné.  L’ID de session est retourné à partir de «Spark session Create».
```bash
azdata bdc spark session info --session-id -i 
                              
```
### <a name="examples"></a>Exemples
Obtenir les informations de session pour la session avec l’ID 0.
```bash
azdata spark session info --session-id 0
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--session-id -i`
Numéro d’ID de session Spark.
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
## <a name="azdata-bdc-spark-session-log"></a>Journal de session azdata BDC Spark
Cela obtient les entrées de journal de session pour une session Spark active avec l’ID donné.  L’ID de session est retourné à partir de «Spark session Create».
```bash
azdata bdc spark session log --session-id -i 
                             
```
### <a name="examples"></a>Exemples
Obtient le journal de session pour la session avec l’ID 0.
```bash
azdata spark session log --session-id 0
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--session-id -i`
Numéro d’ID de session Spark.
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
## <a name="azdata-bdc-spark-session-state"></a>État de session azdata BDC Spark
Cela obtient l’état de session pour une session Spark active avec l’ID donné.  L’ID de session est retourné à partir de «Spark session Create».
```bash
azdata bdc spark session state --session-id -i 
                               
```
### <a name="examples"></a>Exemples
Obtenir l’état de session pour la session avec l’ID 0.
```bash
azdata spark session state --session-id 0
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--session-id -i`
Numéro d’ID de session Spark.
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
## <a name="azdata-bdc-spark-session-delete"></a>suppression de la session azdata BDC Spark
Cela supprime une session Spark interactive. L’ID de session est retourné à partir de «Spark session Create».
```bash
azdata bdc spark session delete --session-id -i 
                                
```
### <a name="examples"></a>Exemples
Supprimer une session.
```bash
azdata spark session delete --session-id 0
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--session-id -i`
Numéro d’ID de session Spark.
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
