---
title: Création de fichiers de valeurs de variables (MySQLToSQL) | Microsoft Docs
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
ms.openlocfilehash: be1530bdec1c1523a873dc93b1d70e6e72c880ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103023"
---
# <a name="creating-variable-value-files-mysqltosql"></a>Création de fichiers de valeurs de variables (MySQLToSQL)
Le fichier de valeurs de variable est un fichier XML comprenant les valeurs de paramètres des commandes, telles que le nom du serveur source ou de destination qui changent fréquemment d’une migration de serveur à une autre. En cas de migration d’un grand nombre de bases de données, plusieurs fichiers de variables pour stocker la valeur de chaque serveur source sont créés et référencés dans un fichier de script principal avec le commutateur **-v** à la ligne de commande. Cela permet de conserver des valeurs statiques dans quelques fichiers de script avec les valeurs des variables dans plusieurs fichiers de variables.  
  
> [!NOTE]  
> 1.  Les noms de variables sont préfixés et suffixés par un symbole $ (dollar). Si aucune valeur n’est assignée aux variables dans le fichier de valeurs de variable, vous rencontrerez une erreur lors de l’analyse du fichier de script, ce qui entraînera le blocage du processus d’exécution de la console.  
> 2.  Le caractère d’échappement **$** pour **$$** est. Si la valeur d’une variable ou d’une valeur statique d’un **$** paramètre contient un symbole (dollar **$$** ), doit être spécifié pour le traiter en tant que caractère au lieu d’une variable.  
> 3.  À des fins de maintenabilité, les variables peuvent `'variable-group'` être déclarées à l’intérieur d’éléments pour la séparation logique des variables définies par l’utilisateur.  L’utilisation de cet élément n’est pas obligatoire.  
  
**Exemples :**  
  
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
  
## <a name="variable-value-file-validation"></a>Validation de fichier de valeur de variable  
L’utilisateur peut facilement valider son fichier de valeurs de variable par rapport au fichier de définition de schéma **« ConsoleScriptVariablesSchema. xsd »** disponible dans le dossier « schemas ».  
  
## <a name="next-step"></a>étape suivante  
L’étape suivante de l’utilisation de la console consiste à [créer les fichiers de connexion au serveur &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Création des fichiers de connexion au serveur (MySQL)](https://msdn.microsoft.com/df0e970c-da0b-4118-b359-c9dcbbad16d6)  
  
