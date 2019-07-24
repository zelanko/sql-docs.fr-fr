---
title: Référence de configuration azdata BDC
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes BDC azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ed777391af3695da69e04c0e2693cff912c76771
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426289"
---
# <a name="azdata-bdc-config"></a>configuration du BDC azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes de **configuration BDC** dans l’outil **azdata** . Pour plus d’informations sur les autres commandes **azdata** , consultez [référence azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[init de configuration azdata BDC](#azdata-bdc-config-init) | Initialise un profil de configuration de cluster Big Data qui peut être utilisé avec la création du cluster.
[liste de configuration azdata BDC](#azdata-bdc-config-list) | Répertorie les choix de profil de configuration disponibles.
[affichage de la configuration azdata BDC](#azdata-bdc-config-show) | Affiche la configuration actuelle du BDC ou la configuration d’un fichier local que vous spécifiez, par exemple Custom/cluster. JSON.
[ajout de la configuration azdata BDC](#azdata-bdc-config-add) | Ajoutez une valeur pour un chemin d’accès JSON dans un fichier de configuration.
[suppression de la configuration azdata BDC](#azdata-bdc-config-remove) | Supprimer une valeur pour un chemin d’accès JSON dans un fichier de configuration.
[remplacement de la configuration azdata BDC](#azdata-bdc-config-replace) | Remplacez une valeur pour un chemin d’accès JSON dans un fichier de configuration.
[correctif de configuration azdata BDC](#azdata-bdc-config-patch) | Corrige un fichier de configuration basé sur un fichier de correctif JSON.
## <a name="azdata-bdc-config-init"></a>init de configuration azdata BDC
Initialise un profil de configuration de cluster Big Data qui peut être utilisé avec la création du cluster. La source spécifique du profil de configuration peut être spécifiée dans les arguments de 3 choix.
```bash
azdata bdc config init [--target -t] 
                       [--source -s]  
                       [--force -f]  
                       [--accept-eula -a]
```
### <a name="examples"></a>Exemples
Initialisation de la configuration de BDC guidée-vous recevrez des invites pour les valeurs nécessaires.
```bash
azdata bdc config init
```
L’initialisation de la configuration BDC avec des arguments crée un profil de configuration AKS-dev-test dans./Custom.
```bash
azdata bdc config init --source aks-dev-test --target custom
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--target -t`
Chemin de fichier de l’emplacement où vous souhaitez placer le profil de configuration, par défaut CWD avec Custom-config. JSON.
#### `--source -s`
Source du profil de configuration: ['AKS-dev-test', 'kubeadm-dev-test', 'minikube-dev-test']
#### `--force -f`
Forcer le remplacement du fichier cible.
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
## <a name="azdata-bdc-config-list"></a>liste de configuration azdata BDC
Répertorie les choix de profil de configuration disponibles pour une utilisation dans`bdc config init`
```bash
azdata bdc config list [--config-profile -c] 
                       [--type -t]  
                       [--accept-eula -a]
```
### <a name="examples"></a>Exemples
Affiche tous les noms de profil de configuration disponibles.
```bash
azdata bdc config list
```
Affiche JSON d’un profil de configuration spécifique.
```bash
azdata bdc config list --config-profile aks-dev-test
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--config-profile -c`
Profil de configuration par défaut: ['AKS-dev-test', 'kubeadm-dev-test', 'minikube-dev-test']
#### `--type -t`
Le type de configuration que vous souhaitez afficher.
`cluster`
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
## <a name="azdata-bdc-config-show"></a>affichage de la configuration azdata BDC
Affiche la configuration actuelle du BDC ou la configuration d’un fichier local que vous spécifiez, par exemple Custom/cluster. JSON. La commande peut également utiliser un chemin d’accès JSON si vous souhaitez obtenir une section uniquement.  Vous pouvez également spécifier un fichier cible vers lequel effectuer la sortie.  Si un fichier cible n’est pas spécifié, il sera simplement sorti sur le terminal.
```bash
azdata bdc config show [--config-file -c] 
                       [--target -t]  
                       [--json-path -j]  
                       [--force -f]
```
### <a name="examples"></a>Exemples
Afficher la configuration du BDC dans votre console
```bash
azdata bdc config show
```
Dans un fichier de configuration local, obtenez une valeur à la fin d’un chemin d’accès de clé JSON simple.
```bash
azdata bdc config show --config-file custom-config/cluster.json --json-path 'metadata.name' --target section.json
```
Dans un fichier de configuration local, obtient une valeur à la fin d’un chemin d’accès de clé JSON avec une condition
```bash
azdata bdc config show --config-file custom-config/cluster.json  --json-path '$.spec.pools[?(@.spec.type=="Storage")].spec' --target section.json
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--config-file -c`
Chemin du fichier de configuration du cluster Big Data si vous ne voulez pas la configuration du cluster dans lequel vous currentlylogged, par exemple, Custom/cluster. JSON
#### `--target -t`
Fichier de sortie dans lequel stocker le résultat. Valeur par défaut: dirigée vers stdout.
#### `--json-path -j`
Chemin d’accès de la clé JSON qui donne la section ou la valeur que vous souhaitez dans la configuration, c.-à-d. touche1. key2. key3. Utilise le langage de requête jsonpath https://jsonpath.com/ ,, par exemple:-j' $. spec. pools [? ( @.spec.type = = "Master")].. terminaison
#### `--force -f`
Forcer le remplacement du fichier cible.
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
## <a name="azdata-bdc-config-add"></a>ajout de la configuration azdata BDC
Ajoute la valeur au chemin d’accès JSON dans le fichier de configuration.  Tous les exemples ci-dessous sont fournis dans bash.  Si vous utilisez une autre ligne de commande, sachez que vous devrez peut-être escapequotations de manière appropriée.  Vous pouvez également utiliser la fonctionnalité de fichier de correctif logiciel.
```bash
azdata bdc config add --config-file -c 
                      --json-values -j
```
### <a name="examples"></a>Exemples
Ex 1-ajouter un stockage de plan de contrôle.
```bash
azdata bdc config add --config-file custom/control.json --json-values 'spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--config-file -c`
Chemin du fichier de configuration du cluster Big Data de la configuration que vous souhaitez définir, c.-à-d. Custom/cluster. JSON
#### `--json-values -j`
Liste de paires clé/valeur de chemins d’accès JSON aux valeurs: key1. SubKey1 = value1, key2. SubKey2 = value2. Vous pouvez fournir des valeurs JSON Inline, telles que: Key = «{» Kind»: «cluster», «Name»: «test-cluster»}» ou fournir un chemin d’accès de fichier, tel que Key =./Values.JSON. Add ne prend pas en charge les conditions.  Pour obtenir http://jsonpatch.com/ des exemples d’utilisation de votre chemin d’accès, consultez.  Si vous souhaitez accéder à un tableau, vous devez le faire en indiquant l’index, tel que Key. 0 = value
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
## <a name="azdata-bdc-config-remove"></a>suppression de la configuration azdata BDC
Supprime la valeur au niveau du chemin d’accès JSON dans le fichier de configuration.  Tous les exemples ci-dessous sont fournis dans bash.  Si vous utilisez une autre ligne de commande, sachez que vous devrez peut-être escapequotations de manière appropriée.  Vous pouvez également utiliser la fonctionnalité de fichier de correctif logiciel.
```bash
azdata bdc config remove --config-file -c 
                         --json-path -j
```
### <a name="examples"></a>Exemples
Ex 1-supprimer le stockage du plan de contrôle.
```bash
azdata bdc config remove --config-file custom/control.json --json-path '.spec.storage'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--config-file -c`
Chemin du fichier de configuration du cluster Big Data de la configuration que vous souhaitez définir, c.-à-d. Custom/cluster. JSON
#### `--json-path -j`
Liste de chemins d’accès JSON basés sur la bibliothèque jsonpatch qui indique les valeurs que vous souhaitez supprimer, par exemple: key1. SubKey1, key2. SubKey2. Remove ne prend pas en charge les conditions. Pour obtenir http://jsonpatch.com/ des exemples d’utilisation de votre chemin d’accès, consultez.  Si vous souhaitez accéder à un tableau, vous devez le faire en indiquant l’index, tel que Key. 0 = value
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
## <a name="azdata-bdc-config-replace"></a>remplacement de la configuration azdata BDC
Remplace la valeur au niveau du chemin d’accès JSON dans le fichier de configuration.  Toutes les examplesbelow sont fournies dans bash.  Si vous utilisez une autre ligne de commande, sachez que vous devrez peut-être escapequotations de manière appropriée.  Vous pouvez également utiliser la fonctionnalité de fichier de correctif logiciel.
```bash
azdata bdc config replace --config-file -c 
                          --json-values -j
```
### <a name="examples"></a>Exemples
Ex 1-remplacer le port d’un point de terminaison unique (point de terminaison de contrôleur).
```bash
azdata bdc config replace --config-file custom/control.json --json-values '$.spec.endpoints[?(@.name=="Controller")].port=30080'
```
Ex 2-remplacer le stockage du plan de contrôle.
```bash
azdata bdc config replace --config-file custom/control.json --json-values 'spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
Ex 3-remplacer le stockage du pool, y compris les réplicas (pool de stockage).
```bash
azdata bdc config replace --config-file custom/cluster.json --json-values '$.spec.pools[?(@.spec.type == "Storage")].spec={"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--config-file -c`
Chemin du fichier de configuration du cluster Big Data de la configuration que vous souhaitez définir, c.-à-d. Custom/cluster. JSON
#### `--json-values -j`
Liste de paires clé/valeur de chemins d’accès JSON aux valeurs: key1. SubKey1 = value1, key2. SubKey2 = value2. Vous pouvez fournir des valeurs JSON Inline, telles que: Key = «{» Kind»: «cluster», «Name»: «test-cluster»}» ou fournir un chemin d’accès de fichier, tel que Key =./Values.JSON. Replace prend en charge les conditions dans la bibliothèque jsonpath.  Pour ce faire, démarrez votre chemin d’accès avec un $. Cela vous permettra d’effectuer une condition conditionnelle telle que-j $. key1. Key2 [? ( @.key3= = 'SomeValue']. Key4 = valeur. Vous pouvez voir des exemples ci-dessous. Pour obtenir de l’aide supplémentaire, consultez: https://jsonpath.com/
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
## <a name="azdata-bdc-config-patch"></a>correctif de configuration azdata BDC
Corrige le fichier de configuration en fonction du fichier correctif donné. Pour mieux http://jsonpatch.com/ comprendre comment les chemins d’accès doivent être composés, consultez. L’opération de remplacement peut utiliser des conditions dans son chemin d’accès en raison https://jsonpath.com/ de la bibliothèque jsonpath. Tous les fichiers JSON des correctifs doivent commencer par une clé «patch» qui contient un ensemble de correctifs avec les opérations (ajouter, remplacer, supprimer), le chemin d’accès et la valeur correspondants. L’opération «Remove» ne requiert pas de valeur, juste un chemin d’accès. Veuillez consulter les exemples ci-dessous.
```bash
azdata bdc config patch --config-file -c 
                        --patch-file -p
```
### <a name="examples"></a>Exemples
Ex 1-remplacer le port d’un point de terminaison unique (point de terminaison de contrôleur) par le fichier correctif.
```bash
azdata bdc config patch --config-file custom/control.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.endpoints[?(@.name=='Controller')].port","value":30080}]}
```
Ex 2-remplacer le stockage du plan de contrôle par le fichier correctif.
```bash
azdata bdc config patch --config-file custom/control.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":".spec.storage","value":{"accessMode":"ReadWriteMany","className":"managed-premium","size":"10Gi"}}]}
```
Ex 3-remplacer le stockage du pool, y compris les réplicas (pool de stockage) par le fichier correctif.
```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.pools[?(@.spec.type == 'Storage')].spec","value":{"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}}]}
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--config-file -c`
Chemin du fichier de configuration du cluster Big Data de la configuration que vous souhaitez définir, c.-à-d. Custom/cluster. JSON
#### `--patch-file -p`
Chemin d’un fichier JSON de correctif basé sur la bibliothèque jsonpatch: http://jsonpatch.com/. Vous devez démarrer votre fichier JSON de patch avec une clé appelée «correctif», dont la valeur est un tableau d’opérations correctives que vous envisagez de créer. Pour le chemin d’une opération de correction, vous pouvez utiliser la notation par points, telle que key1. Key2 pour la plupart des opérations. Si vous souhaitez effectuer une opération de remplacement et que vous remplacez une valeur dans un tableau qui requiert une condition conditionnelle, utilisez la notation jsonpath en commençant votre chemin avec un $. Cela vous permettra d’effectuer une condition conditionnelle telle que $. key1. Key2 [? ( @.key3= = 'SomeValue']. Key4. Veuillez consulter les exemples ci-dessous. Pour obtenir une aide supplémentaire sur les conditions, consultez https://jsonpath.com/:.
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