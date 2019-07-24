---
title: référence d’instruction azdata BDC Spark
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de l’instruction azdata BDC Spark.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 778980ac6b93e7db79d59182fbd18ab4cfdb8b75
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426089"
---
# <a name="azdata-bdc-spark-statement"></a>instruction azdata BDC Spark

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

L’article suivant fournit des informations de référence sur les commandes de l' **instruction Spark BDC** dans l’outil **azdata** . Pour plus d’informations sur les autres commandes **azdata** , consultez la [référence azdata](reference-azdata.md)

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[liste d’instructions azdata BDC Spark](#azdata-bdc-spark-statement-list) | Répertorie toutes les instructions dans la session Spark donnée.
[création d’une instruction azdata BDC Spark](#azdata-bdc-spark-statement-create) | Créer une nouvelle instruction Spark dans la session donnée.
[informations sur l’instruction azdata BDC Spark](#azdata-bdc-spark-statement-info) | Obtient des informations sur l’instruction demandée dans la session Spark donnée.
[annulation de l’instruction azdata BDC Spark](#azdata-bdc-spark-statement-cancel) | Annule une instruction dans la session Spark donnée.
## <a name="azdata-bdc-spark-statement-list"></a>liste d’instructions azdata BDC Spark
Répertorie toutes les instructions dans la session Spark donnée.
```bash
azdata bdc spark statement list --session-id -i 
                                
```
### <a name="examples"></a>Exemples
Répertorie toutes les instructions de session.
```bash
azdata spark statement list --session-id 0
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
## <a name="azdata-bdc-spark-statement-create"></a>création d’une instruction azdata BDC Spark
Cela crée et exécute une nouvelle instruction dans la session donnée.  Si l’instruction EXECUTE est rapide, le résultat contient la sortie de l’exécution.  Sinon, le résultat peut être récupéré à l’aide de «informations de session Spark» une fois l’instruction terminée.
```bash
azdata bdc spark statement create --session-id -i 
                                  --code -c
```
### <a name="examples"></a>Exemples
Exécutez une instruction.
```bash
azdata spark statement create --session-id 0 --code "2+2"
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--session-id -i`
Numéro d’ID de session Spark.
#### `--code -c`
Chaîne contenant le code à exécuter dans le cadre de l’instruction.
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
## <a name="azdata-bdc-spark-statement-info"></a>informations sur l’instruction azdata BDC Spark
Cela permet d’obtenir l’état d’exécution et les résultats de l’exécution si l’instruction est terminée. L’ID d’instruction est retourné à partir de «Spark Statement Create».
```bash
azdata bdc spark statement info --session-id -i 
                                --statement-id -s
```
### <a name="examples"></a>Exemples
Obtient les informations d’instruction pour la session avec l’ID 0 et l’ID d’instruction égal à 0.
```bash
azdata spark statement info --session-id 0 --statement-id 0
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--session-id -i`
Numéro d’ID de session Spark.
#### `--statement-id -s`
Numéro d’identification de l’instruction Spark dans l’ID de session donné.
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
## <a name="azdata-bdc-spark-statement-cancel"></a>annulation de l’instruction azdata BDC Spark
Cela annule une instruction dans la session Spark donnée. L’ID d’instruction est retourné à partir de «Spark Statement Create».
```bash
azdata bdc spark statement cancel --session-id -i 
                                  --statement-id -s
```
### <a name="examples"></a>Exemples
Annuler une instruction.
```bash
azdata spark statement cancel --session-id 0 --statement-id 0
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--session-id -i`
Numéro d’ID de session Spark.
#### `--statement-id -s`
Numéro d’identification de l’instruction Spark dans l’ID de session donné.
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
