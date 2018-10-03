---
title: Ensembles de résultats dans la tâche d’exécution SQL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- result sets [Integration Services]
- Execute SQL task [Integration Services]
ms.assetid: 62605b63-d43b-49e8-a863-e154011e6109
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 25f917dc3831f0915b87c4a93dbb4197a3d25df0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48053365"
---
# <a name="result-sets-in-the-execute-sql-task"></a>Ensembles de résultats dans la tâche d’exécution SQL
  Dans un package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , le retour d'un jeu de résultats à la tâche d'exécution SQL dépend du type de commande SQL que la tâche utilise. Par exemple, une instruction SELECT retourne généralement un ensemble de résultats, contrairement à une instruction INSERT.  
  
 Le contenu du jeu de résultats varie également selon la commande SQL. Par exemple, l'ensemble de résultats issu d'une instruction SELECT peut contenir un nombre de lignes quelconque (aucune ligne, une ligne ou de nombreuses lignes). Toutefois, le jeu de résultats d'une instruction SELECT qui retourne un nombre ou une somme contient une seule ligne.  
  
 L'utilisation d'ensembles de résultats dans une tâche d'exécution SQL ne permet pas uniquement de savoir si la commande SQL retourne un ensemble de résultats et ce que celui-ci contient. D'autres indications et spécifications d'utilisation permettent d'utiliser avec succès des jeux de résultats dans la tâche d'exécution SQL. Le reste de cette rubrique traite de ces indications et spécifications d'utilisation.  
  
-   [Spécification d'un type d'ensemble de résultats](#Result_set_type)  
  
-   [Remplir une variable à l’aide d’un jeu de résultats](#Populate_variable_with_result_set)  
  
-   [Configuration des résultats définit dans Execute SQL Task Editor](#Configure_result_sets)  
  
##  <a name="Result_set_type"></a> Spécification d’un résultat de Type d’ensemble  
 La tâche d'exécution SQL prend en charge les types de jeux de résultats suivants :  
  
-   L'ensemble de résultats **Aucun** est utilisé lorsque la requête ne retourne aucun résultat. Par exemple, cet ensemble de résultats est utilisé pour les requêtes qui ajoutent, modifient et suppriment des enregistrements dans une table.  
  
-   L'ensemble de résultats **Ligne unique** est utilisé lorsque la requête ne retourne qu'une seule ligne. Par exemple, ce jeu de résultats est utilisé pour une instruction SELECT qui retourne un nombre ou une somme.  
  
-   Le jeu de résultats **Ensemble de résultats complet** est utilisé lorsque la requête retourne plusieurs lignes. Par exemple, ce jeu de résultats est utilisé pour une instruction SELECT qui extrait toutes les lignes d'une table.  
  
-   L'ensemble de résultats **XML** est utilisé lorsque la requête retourne un ensemble de résultats dans un format XML. Par exemple, ce jeu de résultats est utilisé pour une instruction SELECT qui comprend une clause FOR XML.  
  
 Si la tâche d'exécution SQL utilise l'ensemble de résultats **Ensemble de résultats complet** et que la requête retourne plusieurs ensemble de lignes, la tâche ne retourne que le premier. Si cet ensemble de lignes génère une erreur, la tâche la signale. En revanche, si d'autres ensembles de lignes génèrent des erreurs, la tâche ne les signale pas.  
  
##  <a name="Populate_variable_with_result_set"></a> Remplissage d’une Variable avec un jeu de résultats  
 Vous pouvez lier le jeu de résultats retourné par une requête à une variable définie par l'utilisateur si le type du jeu de résultats est une ligne unique, un ensemble de lignes ou des données XML.  
  
 Si le type de l'ensemble de résultats est **Ligne unique**, vous pouvez lier une colonne du résultat obtenu à une variable en utilisant le nom de colonne comme nom d'ensemble de résultats. Vous pouvez également utiliser comme nom la position ordinale de la colonne dans la liste des colonnes. Par exemple, le nom de l'ensemble de résultats de la requête `SELECT Color FROM Production.Product WHERE ProductID = ?` pourrait être **Color** ou **0**. Si la requête retourne plusieurs colonnes et que vous souhaitez accéder aux valeurs de toutes les colonnes, vous devez lier chaque colonne à une variable différente. Si vous mappez des colonnes à des variables en utilisant des numéros comme noms de jeux de résultats, ces numéros reflètent l'ordre d'apparition des colonnes dans la liste des colonnes de la requête. Par exemple, dans la requête `SELECT Color, ListPrice, FROM Production.Product WHERE ProductID = ?`, vous utilisez 0 pour la colonne **Color** et 1 pour la colonne **ListPrice** . La possibilité d'utiliser un nom de colonne comme nom d'ensemble de résultats dépend du fournisseur que la tâche a été configurée pour utiliser. Tous les fournisseurs ne rendent pas les noms de colonnes disponibles.  
  
 Certaines requêtes qui retournent une valeur unique peuvent ne pas inclure de noms de colonnes. Par exemple, l'instruction `SELECT COUNT (*) FROM Production.Product` ne retourne aucun nom de colonne. Vous pouvez accéder à l'ensemble de résultats en utilisant la position ordinale, 0, comme nom de résultat. Pour accéder au résultat de retour par nom de colonne, la requête doit inclure une clause AS \<nom alias> pour fournir un nom de colonne. L'instruction `SELECT COUNT (*)AS CountOfProduct FROM Production.Product`, fournit la colonne **CountOfProduct** . Vous pouvez ensuite accéder à la colonne de résultat de retour en utilisant le nom de colonne **CountOfProduct** ou la position ordinale, 0.  
  
 Si le type de l'ensemble de résultats est **Ensemble de résultats complet** ou **XML**, vous devez utiliser 0 comme nom de jeu de résultats.  
  
 Lorsque vous associez une variable à un ensemble de résultats à l'aide du type **Ligne unique** , la variable doit être d'un type de données compatible avec celui de la colonne contenue dans l'ensemble de résultats. Par exemple, vous ne pouvez pas associer un ensemble de résultats contenant un type de données `String` à une variable de type de données numérique. Lorsque vous définissez la **TypeConversionMode** propriété `Allowed`, la tâche d’exécution SQL tente de convertir le paramètre de sortie et le type de résultats aux données de la variable les résultats de requête sont affectés.  
  
 Un ensemble de résultats XML ne peut être associé qu'à une variable de type de données `String` ou `Object`. Si la variable a la `String` de type de données, la tâche d’exécution SQL retourne une chaîne et la source XML peuvent consommer les données XML. Si la variable a la `Object` type de données, la tâche d’exécution SQL retourne un objet de modèle DOM (Document Object).  
  
 Un **ensemble de résultats complet** doit correspondre à une variable de la `Object` type de données. Le résultat obtenu est un objet d'ensemble de lignes. Vous pouvez utiliser un conteneur de boucles Foreach pour extraire les valeurs de ligne de table qui sont stockées dans la variable Object dans les variables de package, et utiliser une tâche de script pour écrire dans un fichier les données stockées dans les variables de package. Pour une démonstration de l'utilisation d'un conteneur de boucles Foreach et d'une tâche de script, voir l'exemple CodePlex, [Execute SQL Parameters and Result Sets](http://go.microsoft.com/fwlink/?LinkId=157863)(en anglais), sur msftisprodsamples.codeplex.com.  
  
 Le tableau suivant récapitule les types de données des variables pouvant correspondre à des ensembles de résultats.  
  
|Type d'ensemble de résultats|Type de données de la variable|Type d'objet|  
|---------------------|---------------------------|--------------------|  
|Ligne unique|Tout type compatible avec la colonne de type contenue dans l'ensemble de résultats.|Non applicable|  
|Ensemble de résultats complet|`Object`|Si la tâche utilise un gestionnaire de connexions natif, y compris les gestionnaires de connexions ADO, OLE DB, Excel et ODBC, l’objet retourné est ADO `Recordset`.<br /><br /> Si la tâche utilise un gestionnaire de connexions managées, telles que la [!INCLUDE[vstecado](../includes/vstecado-md.md)] Gestionnaire de connexions, l’objet retourné est un `System.Data.DataSet`.<br /><br /> Vous pouvez utiliser une tâche de Script pour accéder à la `System.Data.DataSet` de l’objet, comme indiqué dans l’exemple suivant.<br /><br /> `Dim dt As Data.DataTable` <br /> `Dim ds As Data.DataSet = CType(Dts.Variables("Recordset").Value, DataSet)` <br /> `dt = ds.Tables(0)`|  
|XML|`String`|`String`|  
|XML|`Object`|Si la tâche utilise un gestionnaire de connexions natif, y compris les gestionnaires de connexions ADO, OLE DB, Excel et ODBC, l’objet retourné est un `MSXML6.IXMLDOMDocument`.<br /><br /> Si la tâche utilise un gestionnaire de connexions managées, telles que la [!INCLUDE[vstecado](../includes/vstecado-md.md)] Gestionnaire de connexions, l’objet retourné est un `System.Xml.XmlDocument`.|  
  
 Vous pouvez définir la variable dans l'étendue de la tâche d'exécution SQL ou dans celle du package. Si la variable a l'étendue d'un package, le jeu de résultats est disponible pour les autres tâches et conteneurs figurant dans le package, ainsi que pour les packages exécutés par les tâches d'exécution de package ou d'exécution de package DTS 2000.  
  
 Quand vous mappez une variable à un jeu de résultats **Ligne unique** , les valeurs qui ne sont pas des chaînes et qui sont retournées par l’instruction SQL sont converties en chaînes quand les conditions suivantes sont réunies :  
  
-   La propriété **TypeConversionMode** a la valeur true. Définissez la valeur de propriété dans la fenêtre Propriétés ou à l'aide de l' **éditeur de tâche d'exécution de requêtes SQL**.  
  
-   La conversion n'entraîne pas de troncation des données.  
  
 Pour plus d’informations sur le chargement d’un jeu de résultats dans une variable, consultez [Mapper des ensembles de résultats à des variables dans une tâche d’exécution SQL](control-flow/execute-sql-task.md).  
  
##  <a name="Configure_result_sets"></a> Résultat de configuration définit la tâche d’exécution SQL  
 Pour plus d'informations sur les propriétés de jeux de résultats que vous pouvez définir dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Éditeur de tâche SQL exécution &#40;Page ensemble de résultats&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d’une tâche ou d’un conteneur](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 [Mapper des ensembles de résultats à des variables dans une tâche d’exécution SQL](control-flow/execute-sql-task.md)  
  
## <a name="related-content"></a>Contenu associé  
  
-   Exemple CodePlex, [Execute SQL Parameters and Result Sets](http://go.microsoft.com/fwlink/?LinkId=157863)(en anglais), sur msftisprodsamples.codeplex.com  
  
  
