---
title: Référence azdata HDFS BDC
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes azdata BDC HDFS.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8e892c2d501902ef915a297440ae5a6ffda83bce
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426179"
---
# <a name="azdata-bdc-hdfs"></a>azdata BDC HDFS

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes **HDFS BDC** dans l’outil **azdata** . Pour plus d’informations sur les autres commandes **azdata** , consultez [référence azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[interpréteur de commandes HDFS BDC azdata](#azdata-bdc-hdfs-shell) | L’interpréteur de commandes HDFS est un interpréteur de commandes interactif simple pour le système de fichiers HDFS.
[azdata BDC HDFS ls](#azdata-bdc-hdfs-ls) | Répertorie l’état du fichier ou du répertoire donné.
[azdata HDFS BDC existe](#azdata-bdc-hdfs-exists) | Déterminez si un fichier ou un répertoire existe.  Retourne la valeur true si Exists et false dans le cas contraire.
[azdata BDC HDFS mkdir](#azdata-bdc-hdfs-mkdir) | Crée un répertoire au chemin d’accès spécifié.
[azdata BDC HDFS MV](#azdata-bdc-hdfs-mv) | Déplacer le fichier ou le chemin d’accès spécifié vers l’emplacement spécifié.
[azdata BDC HDFS créer](#azdata-bdc-hdfs-create) | Créez le fichier texte à l’emplacement spécifié.  Un contenu de texte simple peut être ajouté par le biais du paramètre Data.
[azdata BDC HDFS CAT](#azdata-bdc-hdfs-cat) | Lire le contenu d’un fichier.  Le décalage et la longueur en octets sont des paramètres facultatifs.
[azdata BDC HDFS RM](#azdata-bdc-hdfs-rm) | Suppression d’un fichier ou d’un répertoire.
[azdata BDC HDFS RMR](#azdata-bdc-hdfs-rmr) | Supprimez de manière récursive un fichier ou un répertoire.
[azdata BDC HDFS chmod](#azdata-bdc-hdfs-chmod) | Modifiez l’autorisation sur le fichier ou le répertoire spécifié.
[azdata BDC HDFS chown](#azdata-bdc-hdfs-chown) | Modifiez le propriétaire ou le groupe du fichier spécifié.
[montage HDFS BDC azdata](reference-azdata-bdc-hdfs-mount.md) | Gérer le montage des magasins distants dans HDFS.
## <a name="azdata-bdc-hdfs-shell"></a>interpréteur de commandes HDFS BDC azdata
L’interpréteur de commandes HDFS est un interpréteur de commandes interactif simple pour le système de fichiers HDFS.
```bash
azdata bdc hdfs shell 
```
### <a name="examples"></a>Exemples
Lancez l’interpréteur de commandes.
```bash
azdata bdc hdfs shell
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
## <a name="azdata-bdc-hdfs-ls"></a>azdata BDC HDFS ls
Répertorie l’état du fichier ou du répertoire donné.
```bash
azdata bdc hdfs ls --path -p 
                   
```
### <a name="examples"></a>Exemples
Afficher l’État
```bash
azdata bdc hdfs ls --path '/tmp'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Chemin d’accès à la liste d’État.
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
## <a name="azdata-bdc-hdfs-exists"></a>azdata HDFS BDC existe
Déterminez si un fichier ou un répertoire existe.  Retourne la valeur true si Exists et false dans le cas contraire.
```bash
azdata bdc hdfs exists --path -p 
                       
```
### <a name="examples"></a>Exemples
Vérifiez l’existence d’un fichier ou d’un répertoire.
```bash
azdata bdc hdfs exists --path '/tmp'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Chemin d’accès pour vérifier l’existence.
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
## <a name="azdata-bdc-hdfs-mkdir"></a>azdata BDC HDFS mkdir
Crée un répertoire au chemin d’accès spécifié.
```bash
azdata bdc hdfs mkdir --path -p 
                      
```
### <a name="examples"></a>Exemples
Créez un répertoire.
```bash
azdata bdc hdfs mkdir --path '/tmp'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Nom du répertoire à créer.
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
## <a name="azdata-bdc-hdfs-mv"></a>azdata BDC HDFS MV
Déplacer le fichier ou le chemin d’accès spécifié vers l’emplacement spécifié.
```bash
azdata bdc hdfs mv --source-path -s 
                   --target-path -t
```
### <a name="examples"></a>Exemples
Déplacer un fichier ou un répertoire.
```bash
azdata bdc hdfs mv --source-path '/tmp' --target-path '/dest'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--source-path -s`
Répertoire à déplacer.
#### `--target-path -t`
Emplacement vers lequel se déplacer.
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
## <a name="azdata-bdc-hdfs-create"></a>azdata BDC HDFS créer
Créez le fichier texte à l’emplacement spécifié.  Un contenu de texte simple peut être ajouté par le biais du paramètre Data.
```bash
azdata bdc hdfs create --path -p 
                       --data -d
```
### <a name="examples"></a>Exemples
Créer un fichier.
```bash
azdata bdc hdfs create --path '/tmp/test.txt' --data "This is a test."
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Nom du fichier à créer.
#### `--data -d`
Contenu du fichier.  Destiné à un contenu de texte simple.
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
## <a name="azdata-bdc-hdfs-cat"></a>azdata BDC HDFS CAT
Lire le contenu d’un fichier.  Le décalage et la longueur en octets sont des paramètres facultatifs.
```bash
azdata bdc hdfs cat --path -p 
                    --offset  
                    --length -l
```
### <a name="examples"></a>Exemples
Lire le fichier.
```bash
azdata bdc hdfs cat --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Nom du fichier à lire.
#### `--offset`
Nombre d’octets décalés dans le fichier à lire.
#### `--length -l`
Longueur des données à lire.
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
## <a name="azdata-bdc-hdfs-rm"></a>azdata BDC HDFS RM
Suppression d’un fichier ou d’un répertoire.
```bash
azdata bdc hdfs rm --path -p 
                   
```
### <a name="examples"></a>Exemples
Suppression d’un fichier ou d’un répertoire.
```bash
azdata bdc hdfs rm --path '/tmp'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Nom du fichier à supprimer.
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
## <a name="azdata-bdc-hdfs-rmr"></a>azdata BDC HDFS RMR
Supprimez de manière récursive un fichier ou un répertoire.
```bash
azdata bdc hdfs rmr --path -p 
                    
```
### <a name="examples"></a>Exemples
Répertoire de suppression récursive.
```bash
azdata bdc hdfs rmr --path '/tmp'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Nom du fichier à supprimer de manière récursive.
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
## <a name="azdata-bdc-hdfs-chmod"></a>azdata BDC HDFS chmod
Modifiez l’autorisation sur le fichier ou le répertoire spécifié.
```bash
azdata bdc hdfs chmod --path -p 
                      --permission
```
### <a name="examples"></a>Exemples
Modifiez l’autorisation du fichier ou du répertoire.
```bash
azdata bdc hdfs chmod --permission 775 --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Nom du fichier ou du répertoire sur lequel définir les autorisations.
#### `--permission`
Octets d’autorisation à définir.  Exemple: «775».
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
## <a name="azdata-bdc-hdfs-chown"></a>azdata BDC HDFS chown
Modifiez le propriétaire ou le groupe du fichier spécifié.
```bash
azdata bdc hdfs chown --path -p 
                      --owner  
                      --group -g
```
### <a name="examples"></a>Exemples
Modifiez le propriétaire et le groupe.
```bash
azdata bdc hdfs chown --owner hdfs --group superusergroup --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Nom du fichier ou du répertoire dont le propriétaire doit être modifié.
#### `--owner`
Nom du propriétaire à affecter à la valeur.
#### `--group -g`
Nom du groupe à affecter à la valeur.
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
