---
description: Création de fichiers de valeurs de variables (OracleToSQL)
title: Création de fichiers de valeurs de variables (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Variable Value File Creation
- Variable Value File, Variable Value File Validation
ms.assetid: f583d81a-8e34-41b1-8100-ee3a6a82213b
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: b97455172dbed11a8d29168946decca7b3b919e4
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039203"
---
# <a name="creating-variable-value-files-oracletosql"></a>Création de fichiers de valeurs de variables (OracleToSQL)
Le fichier de valeurs de variable est un fichier XML comprenant les valeurs de paramètres des commandes, telles que le nom du serveur source ou de destination qui changent fréquemment d’une migration de serveur à une autre. En cas de migration d’un grand nombre de bases de données, plusieurs fichiers de variables pour stocker la valeur de chaque serveur source sont créés et référencés dans un fichier de script principal avec le commutateur **-v** à la ligne de commande. Cela permet de conserver des valeurs statiques dans quelques fichiers de script avec les valeurs des variables dans plusieurs fichiers de variables.  
  
> [!NOTE]  
> 1.  Les noms de variables sont préfixés et suffixés par un symbole $ (dollar). Si aucune valeur n’est assignée aux variables dans le fichier de valeurs de variable, vous rencontrerez une erreur lors de l’analyse du fichier de script, ce qui entraînera le blocage du processus d’exécution de la console.  
> 2.  Le caractère d’échappement pour **$** est **$$** . Si la valeur d’une variable ou d’une valeur statique d’un paramètre contient un **$** symbole (dollar), **$$** doit être spécifié pour le traiter en tant que caractère au lieu d’une variable.  
> 3.  À des fins de maintenabilité, les variables peuvent être déclarées à l’intérieur d' `'variable-group'` éléments pour la séparation logique des variables définies par l’utilisateur.  L’utilisation de cet élément n’est pas obligatoire.  
  
**Exemples :**  
  
**Exemple 1 :**  
  
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
**Exemple 2 :**  
  
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
  
## <a name="next-step"></a>étape suivante  
L’étape suivante de l’utilisation de la console consiste à [créer les fichiers de connexion au serveur &#40;OracleToSQL&#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Création des fichiers du serveur (Oracle)](./creating-the-server-connection-files-oracletosql.md)  
