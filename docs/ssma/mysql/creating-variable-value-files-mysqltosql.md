---
title: Création de fichiers de la valeur de la Variable (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Creating variable value files
- variable value file validation
ms.assetid: 1dc56a7b-8e3a-4576-ad4f-47050bf7e28a
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 43dc992457245de08785afb16e6c8cf71572716e
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51659168"
---
# <a name="creating-variable-value-files-mysqltosql"></a>Création de fichiers de valeurs de variables (MySQLToSQL)
Fichier de valeurs variable est un fichier XML contenant les valeurs de paramètre des commandes telles que : le nom du serveur source ou de destination qui changent fréquemment à partir de la migration d’un serveur vers un autre. En cas d’un grand nombre de migrations de base de données, plusieurs fichiers de variables pour stocker la valeur de chaque serveur source seront créés et référencés dans un fichier de script principal avec la **– v** passer à la ligne de commande. Cela permet de conserver des valeurs statiques dans quelques fichiers de script avec les valeurs des variables dans plusieurs fichiers de variables.  
  
> [!NOTE]  
> 1.  Les noms de variables ont le préfixe et suffixe avec le symbole $ (dollar). Si les variables ne sont pas attribués une valeur dans le fichier de la valeur de la variable, vous rencontrerez une erreur lors de l’analyse du fichier de script résultant dans bloquées le processus d’exécution de console.  
> 2.  Le caractère d’échappement **$** est **$$**. Si la valeur d’une valeur d’un paramètre de variable ou statique contient **$** symbole (dollar), puis **$$** doit être spécifié pour le traiter comme un caractère au lieu d’une variable.  
> 3.  À des fins de facilité de maintenance, les variables peuvent être déclarées à l’intérieur de `‘variable-group’` variables définies par des éléments pour une séparation logique de l’utilisateur.  Utilisation de cet élément n’est pas obligatoire.  
  
**Exemples :**  
  
**Exemple 1 :**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$project_folder$" value="<folder-name>"/>  
  
    <variable name="$project_name$" value="<project-name>"/>  
  
    <variable name="$project_overwrite$" value="<true/false>"/>  
  
    <variable name="$project_type$" value="<project-type>"/>  
  
  </variable-group>  
  
</variables>  
```  
**Exemple 2 :**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetUserName$ value="<user-name>"/>  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
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
  
## <a name="variable-value-file-validation"></a>Validation des fichiers de valeur de la variable  
L’utilisateur peut valider facilement son fichier de la valeur de la variable par rapport au fichier de définition de schéma **'ConsoleScriptVariablesSchema.xsd'** disponibles dans le dossier « Schémas ».  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante de d’exploitation de la console est [création des fichiers de connexion de serveur &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Création des fichiers de connexion de serveur (MySQL)](https://msdn.microsoft.com/df0e970c-da0b-4118-b359-c9dcbbad16d6)  
  
