---
title: "Création de fichiers de la valeur de la Variable (AccessToSQL) | Documents Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 08/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 808595c3-8ef1-40bd-a93e-5cf237950e08
caps.latest.revision: "15"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a04787fdf99c804a7ec304ae4f022583a192508f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="creating-variable-value-files-accesstosql"></a>Création de fichiers de la valeur de la Variable (AccessToSQL)
Un fichier de valeurs de Variable est un fichier XML contenant les valeurs de paramètre des commandes qui changent fréquemment sur les migrations de serveurs (par exemple, le nom du serveur source ou de destination). En cas d’un grand nombre de migrations de la base de données, plusieurs fichiers de variables pour stocker la valeur de chaque serveur source sont créés et référencés dans un fichier de script principal avec le **– v** passer à la ligne de commande. Ce comportement permet de conserver des valeurs statiques dans plusieurs fichiers de script avec les valeurs des variables dans plusieurs fichiers de variable.  
  
> [!NOTE]  
> -  Les noms de variables ont le préfixe et suffixe avec un symbole $ (dollar). Si une variable n’est pas attribuée une valeur dans le fichier de la valeur de la variable, une erreur lors de l’analyse du fichier de script se produit, de bloquer le processus d’exécution de console.  
> -  The escape character for **$** is **$$**. Si la valeur d’une valeur d’un paramètre de variable ou statique contient un  **$**  symbole (dollar), puis  **$$**  doit être spécifié pour le traiter comme un caractère au lieu d’une variable.  
> -  À des fins de facilité de maintenance, les variables peuvent être déclarées à l’intérieur de `‘variable-group’` éléments pour une séparation logique entre les variables définies par l’utilisateur.  L’utilisation de cet élément n’est pas obligatoire.  
  
**Exemples :**  
  
**Exemple 1 :**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$type$" value="MyProject"/>  
  
    <variable name="$project_folder$" value=".\$project_name$"/>  
  
    <variable name="$project_name$" value="$type$ConsoleProject"/>  
  
    <variable name="$project_overwrite$" value="true"/>  
  
    <variable name="$project_type$" value="sql-server-2008"/>  
  
  </variable-group>  
  
</variables>  
```  
**Exemple 2 :**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="xxx"/>  
  
      <variable name="$TargetDB$" value="xxx"/>  
  
      <variable name="$TargetUserName$" value="xxx"/>  
  
      <variable name="$TargetPassword$" value="xxx"/>  
  
      <variable name="$TargetIsTrusted$" value="xxx"/>  
  
      <variable name="$TrustedConnection$" value="xxx"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="TestTable1"/>  
  
      <variable name="$ObjectName2$" value="TestProc1"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="variable-value-file-validation"></a>Validation des fichiers de valeur de la variable  
L’utilisateur peut valider facilement son fichier de la valeur de la variable par rapport au fichier de définition de schéma **ConsoleScriptVariablesSchema.xsd** disponibles dans le dossier « Schémas ».  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante d’exploitation de la console est [créer les fichiers de connexion de serveur &#40; AccessToSQL &#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Création des fichiers de connexion de serveur (accès)](http://msdn.microsoft.com/829153be-aa8e-4162-87e8-69882feecf19)  
  
