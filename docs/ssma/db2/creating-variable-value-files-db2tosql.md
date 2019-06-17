---
title: Création de fichiers de la valeur de la Variable (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 122f3fbe-46a0-40df-ac3b-d43bf33d96ba
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: cf62d09de1180687598d817ff9199d7098008829
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63299141"
---
# <a name="creating-variable-value-files-db2tosql"></a>Création de fichiers de la valeur de la Variable (DB2ToSQL)
Fichier de valeurs variable est un fichier XML contenant les valeurs de paramètre des commandes telles que : le nom du serveur source ou de destination qui changent fréquemment à partir de la migration d’un serveur vers un autre. En cas d’un grand nombre de migrations de base de données, plusieurs fichiers de variables pour stocker la valeur de chaque serveur source seront créés et référencés dans un fichier de script principal avec la **- v** passer à la ligne de commande. Cela permet de conserver des valeurs statiques dans quelques fichiers de script avec les valeurs des variables dans plusieurs fichiers de variables.  
  
> [!NOTE]  
> 1.  Les noms de variables ont le préfixe et suffixe avec le symbole $ (dollar). Si les variables ne sont pas attribués une valeur dans le fichier de la valeur de la variable, vous rencontrerez une erreur lors de l’analyse du fichier de script résultant dans bloquées le processus d’exécution de console.  
> 2.  Le caractère d’échappement **$** est **$$** . Si la valeur d’une valeur d’un paramètre de variable ou statique contient **$** symbole (dollar), puis **$$** doit être spécifié pour le traiter comme un caractère au lieu d’une variable.  
> 3.  À des fins de facilité de maintenance, les variables peuvent être déclarées à l’intérieur de `'variable-group'` variables définies par des éléments pour une séparation logique de l’utilisateur.  Utilisation de cet élément n’est pas obligatoire.  
  
**Exemples :**  
  
**Exemple 1 :**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$project_folder$" value="<project-folder>"/>  
  
    <variable name="$project_name$" value="<project-name>"/>  
  
    <variable name="$project_overwrite$" value="<true/false>"/>  
  
    <variable name="$project_type$" value="<project-type>"/>  
  
  </variable-group>  
  
</variables>  
```  
**Exemple 2 :**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
      <variable name="$TargetUserName$" value="<user-name>"/>  
  
      <variable name="$TargetPassword$" value="<password>"/>  
  
      <variable name="$TrustedConnection$" value="<true/false>"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="<object-name>"/>  
  
      <variable name="$ObjectName2$" value="<object-name>"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante de d’exploitation de la console est [création des fichiers de connexion de serveur &#40;DB2ToSQL&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Création des fichiers de connexion de serveur](../oracle/creating-the-server-connection-files-oracletosql.md)  
  
