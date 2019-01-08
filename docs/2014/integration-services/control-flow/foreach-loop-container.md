---
title: Conteneur de boucles Foreach | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.f1
helpviewer_keywords:
- repeating control flow
- Foreach Loop containers
- foreach enumerators [Integration Services]
- containers [Integration Services], Foreach Loop
ms.assetid: dd6cc2ba-631f-4adf-89dc-29ef449c6933
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 664a338dd1d34126717b3953c54b175ffccd63e4
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53355711"
---
# <a name="foreach-loop-container"></a>Conteneur de boucles Foreach
  Le conteneur de boucles Foreach définit un flux de contrôle répétitif dans un package. La mise en œuvre de la boucle est similaire à la structure de bouclage **Foreach** des langages de programmation. Dans un package, le bouclage repose sur l'utilisation d'un énumérateur Foreach.  Le conteneur de boucles Foreach répète le flux de contrôle pour chaque membre d'un énumérateur spécifié.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] fournit les types d'énumérateur suivants :  
  
-   Foreach ADO Enumerator, pour l'énumération des lignes des tables. Par exemple, vous pouvez obtenir les lignes d'un ensemble d'enregistrements ADO.  
  
     La destination de l'ensemble d'enregistrements enregistre les données en mémoire dans un ensemble d'enregistrements stocké dans une variable de package de type `Object`. Vous devez en général utiliser un conteneur de boucles Foreach avec l'énumérateur ADO Foreach pour traiter une par une les lignes de l'ensemble d'enregistrements. La variable spécifiée pour l'énumérateur ADO Foreach doit être de type Object. Pour plus d'informations sur la destination d'un ensemble d'enregistrements, consultez [Use a Recordset Destination](../data-flow/recordset-destination.md).  
  
-   Énumérateur de l'ensemble de lignes du schéma Foreach ADO.NET, pour l'énumération des informations de schéma relatives à une source de données. Par exemple, vous pouvez énumérer les tables de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et en obtenir la liste.  
  
-   Énumérateur de fichier Foreach, pour l'énumération des fichiers d'un dossier. L'énumérateur peut parcourir les sous-dossiers. Par exemple, vous pouvez lire tous les fichiers portant l'extension de nom de fichier *.log stockés dans le dossier Windows et ses sous-dossiers.  
  
-   Foreach From Variable Enumerator, pour l'énumération de l'objet énumérable contenu dans une variable spécifiée. L'objet énumérable peut être un tableau, un `DataTable` ADO.NET, un énumérateur [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], etc. Par exemple, vous pouvez énumérer les valeurs d'un tableau qui contient des noms de serveurs.  
  
-   Énumérateur d'élément Foreach, pour l'énumération des éléments qui sont des collections. Par exemple, vous pouvez énumérer les noms d'exécutables et de répertoires de travail qu'une tâche d'exécution de processus utilise.  
  
-   Foreach NodeList Enumerator, pour l'énumération de l'ensemble de résultats d'une expression XPath (XML Path Language). Par exemple, l'expression suivante énumère tous les auteurs de la période classique et en obtient la liste : `/authors/author[@period='classical']`.  
  
-   Foreach SMO Enumerator, pour l'énumération des objets SMO ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Object). Par exemple, vous pouvez énumérer les vues d'une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et en obtenir la liste.  
  
-   Énumérateur ForEach Azure Blob pour énumérer les objets blob dans un conteneur d'objets blob dans un stockage Azure.  
  
-   Énumérateur ForEach ADLS File pour énumérer les fichiers dans un répertoire ADLS.
  
 Le schéma suivant montre un conteneur de boucles Foreach ayant une tâche de système de fichiers. La boucle Foreach utilise l'énumérateur de fichier Foreach, tandis que la tâche de système de fichiers est configurée pour copier un fichier. Si le dossier spécifié par l'énumérateur contient quatre fichiers, la boucle se répète quatre fois et copie quatre fichiers.  
  
 ![Conteneur de boucles Foreach énumérant un dossier](../media/ssis-foreachloop.gif "Conteneur de boucles Foreach énumérant un dossier")  
  
 Vous pouvez utiliser une combinaison de variables et d'expressions de propriété pour mettre à jour la propriété de l'objet de package avec la valeur de la collection de l'énumérateur. Vous mappez la valeur de la collection avec une variable définie par l'utilisateur, puis vous mettez en œuvre une expression de propriété sur la propriété qui utilise la variable. Par exemple, la valeur de la collection de l’énumérateur Foreach File est mappée à une variable appelée `MyFile` et la variable est ensuite utilisée dans l’expression de propriété pour la propriété Subject d’une tâche Envoyer un message. À l’exécution du package, la propriété Subject est mise à jour avec le nom d’un fichier à chaque répétition de la boucle. Pour plus d’informations, consultez [Expressions de propriété dans des packages](../expressions/use-property-expressions-in-packages.md).  
  
 Vous pouvez également utiliser dans des expressions et des scripts les variables mappées à la valeur de la collection de l'énumérateur.  
  
 Un conteneur de boucles Foreach peut comprendre plusieurs tâches et conteneurs, mais il ne peut utiliser qu'un type d'énumérateur. Si le conteneur de boucles Foreach comprend plusieurs tâches, vous pouvez mapper la valeur de la collection de l'énumérateur avec plusieurs propriétés de chaque tâche.  
  
 Vous pouvez configurer un attribut de transaction sur le conteneur de boucles Foreach afin de définir une transaction pour un sous-ensemble du flux de contrôle du package. Cela vous permet de gérer les transactions au niveau de la boucle Foreach plutôt qu'au niveau du package. Par exemple, si un conteneur de boucles Foreach répète un flux de contrôle qui met à jour des dimensions et des tables de faits dans un schéma en étoile, vous pouvez configurer une transaction de manière à ce que toutes les tables de faits soient correctement mises à jour ou à ce qu'aucune des tables ne soit actualisée. Pour plus d’informations, consultez [Transactions Integration Services](../integration-services-transactions.md).  
  
## <a name="enumerator-types"></a>Types d'énumérateur  
 Vous pouvez configurer les énumérateurs en indiquant différentes informations pour chacun d'eux.  
  
 Le tableau suivant récapitule les informations requises pour chaque type d'énumérateur.  
  
|Énumérateur|Configuration requise|  
|----------------|--------------------------------|  
|Foreach ADO|Spécifiez la variable source de l'objet ADO et le mode de l'énumérateur. La variable doit être du type Object.|  
|Foreach ADO.NET Schema Rowset|Spécifiez la connexion à une base de données et le schéma à énumérer.|  
|Fichier Foreach|Spécifiez un dossier et les fichiers à énumérer, le format du nom des fichiers extraits, et indiquez si l'opération doit parcourir les sous-dossiers.|  
|Foreach From Variable|Spécifiez la variable qui contient les objets à énumérer.|  
|Élément Foreach|Définissez les éléments de la collection d'éléments Foreach, notamment les colonnes et leur type de données.|  
|Foreach NodeList|Spécifiez la source du document XML et configurez l'opération XPath.|  
|Foreach SMO|Spécifiez la connexion à une base de données et les objets SMO à énumérer.|  
|Objet blob Azure foreach|Spécifiez le conteneur d’objets blob Azure qui contient des objets BLOB à énumérer.|  
|Foreach ADLS File|Spécifiez le répertoire ADLS qui contient les fichiers à énumérer, ainsi que certains filtres.|
  
## <a name="property-expressions-in-foreach-loop-containers"></a>Expressions de propriété dans des conteneurs de boucles Foreach  
 Les packages peuvent être configurés pour exécuter simultanément plusieurs exécutables. Cette configuration doit être utilisée avec précaution lorsque le package inclut un conteneur de boucles Foreach qui implémente des expressions de propriété.  
  
 Il est souvent pratique d’implémenter une expression de propriété pour définir la valeur de la propriété ConnectionString des gestionnaires de connexions que les énumérateurs de boucles Foreach utilisent. L’expression de la propriété ConnectionString est définie par une variable qui est mappée à la valeur de la collection de l’énumérateur et mise à jour à chaque itération de la boucle.  
  
 Pour éviter les conséquences négatives d'une synchronisation non déterminante d'une exécution parallèle de tâches dans la boucle, le package doit être configuré pour exécuter un seul exécutable à la fois. Par exemple, si un package peut exécuter plusieurs tâches simultanément, un conteneur de boucles Foreach qui énumère les fichiers dans le dossier, récupère les noms de fichiers, puis utilise une tâche d'exécution SQL pour insérer les noms de fichiers dans une table peut provoquer des conflits d'écriture lorsque deux instances de la tâche d'exécution SQL tentent d'écrire simultanément. Pour plus d’informations, consultez [Expressions de propriété dans des packages](../expressions/use-property-expressions-in-packages.md).  
  
## <a name="related-tasks"></a>Tâches associées  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Configurer un conteneur de boucles Foreach](foreach-loop-container.md)  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
 Pour plus d'informations sur la définition par programmation de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>  
  
## <a name="related-content"></a>Contenu associé  
 Entrée de blog, [SSIS For Each Node List Enumerator](https://go.microsoft.com/fwlink/?LinkId=220671), sur bidn.com.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de contrôle](control-flow.md)   
 [Conteneurs Integration Services](integration-services-containers.md)  
  
  
