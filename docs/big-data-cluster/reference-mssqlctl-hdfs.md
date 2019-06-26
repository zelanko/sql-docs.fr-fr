---
title: mssqlctl hdfs reference
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes hdfs mssqlctl.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9051c3630fce005572bc3b939ebef9ed8d111e07
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394211"
---
# <a name="mssqlctl-hdfs"></a>mssqlctl hdfs

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **hdfs** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[mssqlctl hdfs shell](#mssqlctl-hdfs-shell) | L’interpréteur de commandes HDFS est un interpréteur de commandes interactif simple pour le système de fichiers HDFS.
[mssqlctl hdfs ls](#mssqlctl-hdfs-ls) | Répertorie l’état du fichier donné ou du répertoire.
[mssqlctl hdfs exists](#mssqlctl-hdfs-exists) | Déterminer si un fichier ou répertoire existe.  Retourne True si existe et False sinon.
[mssqlctl hdfs mkdir](#mssqlctl-hdfs-mkdir) | Créez un répertoire au chemin spécifié.
[mssqlctl hdfs mv](#mssqlctl-hdfs-mv) | Déplacer le fichier spécifié ou le chemin d’accès à l’emplacement spécifié.
[mssqlctl hdfs create](#mssqlctl-hdfs-create) | Créer le fichier texte à l’emplacement spécifié.  Contenu de texte simple peut être ajouté via le paramètre de données.
[mssqlctl hdfs read](#mssqlctl-hdfs-read) | Lire le contenu d’un fichier.  Décalage et la longueur en octets sont des paramètres facultatifs.
[mssqlctl hdfs rm](#mssqlctl-hdfs-rm) | Supprimer un fichier ou répertoire.
[mssqlctl hdfs rmr](#mssqlctl-hdfs-rmr) | Un fichier ou répertoire suppriment de façon récursive.
[mssqlctl hdfs chmod](#mssqlctl-hdfs-chmod) | Modifier l’autorisation sur le fichier ou répertoire spécifié.
[mssqlctl hdfs chown](#mssqlctl-hdfs-chown) | Modifier le propriétaire ou le groupe du fichier spécifié.
## <a name="mssqlctl-hdfs-shell"></a>mssqlctl hdfs shell
L’interpréteur de commandes HDFS est un interpréteur de commandes interactif simple pour le système de fichiers HDFS.
```bash
mssqlctl hdfs shell 
```
### <a name="examples"></a>Exemples
Lancez l’interpréteur de commandes.
```bash
mssqlctl hdfs shell
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
## <a name="mssqlctl-hdfs-ls"></a>mssqlctl hdfs ls
Répertorie l’état du fichier donné ou du répertoire.
```bash
mssqlctl hdfs ls --path -p 
                 
```
### <a name="examples"></a>Exemples
État de la liste
```bash
mssqlctl hdfs ls --path '/tmp'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Le chemin d’accès de l’état de la liste.
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
## <a name="mssqlctl-hdfs-exists"></a>mssqlctl hdfs exists
Déterminer si un fichier ou répertoire existe.  Retourne True si existe et False sinon.
```bash
mssqlctl hdfs exists --path -p 
                     
```
### <a name="examples"></a>Exemples
Vérification de l’existence de fichier ou répertoire.
```bash
mssqlctl hdfs exists --path '/tmp'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Chemin d’accès pour vérifier l’existence.
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
## <a name="mssqlctl-hdfs-mkdir"></a>mssqlctl hdfs mkdir
Créez un répertoire au chemin spécifié.
```bash
mssqlctl hdfs mkdir --path -p 
                    
```
### <a name="examples"></a>Exemples
Créer un répertoire.
```bash
mssqlctl hdfs mkdir --path '/tmp'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Nom du répertoire à créer.
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
## <a name="mssqlctl-hdfs-mv"></a>mssqlctl hdfs mv
Déplacer le fichier spécifié ou le chemin d’accès à l’emplacement spécifié.
```bash
mssqlctl hdfs mv --source-path -s 
                 --target-path -t
```
### <a name="examples"></a>Exemples
Déplacer le fichier ou répertoire.
```bash
mssqlctl hdfs mv --source-path '/tmp' --target-path '/dest'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--source-path -s`
Répertoire à déplacer.
#### `--target-path -t`
L’emplacement de destination.
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
## <a name="mssqlctl-hdfs-create"></a>mssqlctl hdfs create
Créer le fichier texte à l’emplacement spécifié.  Contenu de texte simple peut être ajouté via le paramètre de données.
```bash
mssqlctl hdfs create --path -p 
                     --data -d
```
### <a name="examples"></a>Exemples
Créez un fichier.
```bash
mssqlctl hdfs create --path '/tmp/test.txt' --data "This is a test."
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Nom du fichier à créer.
#### `--data -d`
Contenu du fichier.  Conçu pour le contenu de texte simple.
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
## <a name="mssqlctl-hdfs-read"></a>mssqlctl hdfs read
Lire le contenu d’un fichier.  Décalage et la longueur en octets sont des paramètres facultatifs.
```bash
mssqlctl hdfs read --path -p 
                   --offset  
                   --length -l
```
### <a name="examples"></a>Exemples
Lire le fichier.
```bash
mssqlctl hdfs read --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Nom du fichier à lire.
#### `--offset`
Nombre d’octets de décalage dans le fichier à lire.
#### `--length -l`
Longueur des données à lire.
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
## <a name="mssqlctl-hdfs-rm"></a>mssqlctl hdfs rm
Supprimer un fichier ou répertoire.
```bash
mssqlctl hdfs rm --path -p 
                 
```
### <a name="examples"></a>Exemples
Supprimer un fichier ou répertoire.
```bash
mssqlctl hdfs rm --path '/tmp'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Nom du fichier à supprimer.
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
## <a name="mssqlctl-hdfs-rmr"></a>mssqlctl hdfs rmr
Un fichier ou répertoire suppriment de façon récursive.
```bash
mssqlctl hdfs rmr --path -p 
                  
```
### <a name="examples"></a>Exemples
Supprimer le répertoire récursive.
```bash
mssqlctl hdfs rmr --path '/tmp'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Nom du fichier à supprimer de manière récursive.
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
## <a name="mssqlctl-hdfs-chmod"></a>mssqlctl hdfs chmod
Modifier l’autorisation sur le fichier ou répertoire spécifié.
```bash
mssqlctl hdfs chmod --path -p 
                    --permission
```
### <a name="examples"></a>Exemples
Modifier les autorisations de fichier ou répertoire.
```bash
mssqlctl hdfs chmod --permission 775 --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Nom du fichier ou du répertoire pour définir les autorisations sur.
#### `--permission`
Octets d’autorisation à définir.  Exemple « 775 ».
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
## <a name="mssqlctl-hdfs-chown"></a>mssqlctl hdfs chown
Modifier le propriétaire ou le groupe du fichier spécifié.
```bash
mssqlctl hdfs chown --path -p 
                    --owner  
                    --group -g
```
### <a name="examples"></a>Exemples
Modifier le propriétaire et le groupe.
```bash
mssqlctl hdfs chown --owner hdfs --group superusergroup --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Nom du fichier ou du répertoire pour modifier le propriétaire de.
#### `--owner`
Le nom du propriétaire de la valeur.
#### `--group -g`
Nom du groupe à la valeur.
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