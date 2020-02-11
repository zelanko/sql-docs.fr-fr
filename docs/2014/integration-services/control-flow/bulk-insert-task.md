---
title: Insertion en bloc, tâche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.f1
helpviewer_keywords:
- Bulk Insert task
- copying data [Integration Services]
ms.assetid: c5166156-6b4c-4369-81ed-27c4ce7040ae
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9b5da9ff28dc658f870033a02fe88b14ea442c51
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62832871"
---
# <a name="bulk-insert-task"></a>tâche d'insertion en bloc
  La tâche d'insertion en bloc est un moyen efficace pour copier de gros volumes de données dans une table ou une vue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Par exemple, supposons que votre entreprise stocke la liste de ses produits d’un million de lignes sur un mainframe, mais que son système d’e-commerce utilise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour fournir des données à des pages web. Vous devez mettre à jour la table des produits [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] toutes les nuits, à l'aide de la liste principale des produits depuis le gros ordinateur. Pour mettre à jour la table, vous enregistrez la liste des produits dans un fichier au format délimité par des tabulations, puis vous utilisez la tâche d'insertion en bloc pour copier les données directement dans la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Pour garantir une copie de données à haute vitesse, les transformations ne peuvent s'effectuer sur les données lors de leur déplacement entre le fichier source et la table ou la vue.  
  
## <a name="usage-considerations"></a>Considérations sur l'utilisation  
 Avant d'utiliser la tâche d'insertion en bloc, tenez compte des éléments suivants :  
  
-   La tâche d'insertion en bloc ne peut transférer des données que depuis un fichier texte vers une table ou une vue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour utiliser la tâche d’insertion en bloc afin de transférer des données depuis d’autres systèmes de gestion de base de données (SGBD), vous devez exporter les données de la source vers un fichier texte, puis les importer depuis celui-ci vers une table ou une vue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   La destination doit être une table ou une vue d'une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si la table ou la vue de destination contient déjà des données, les nouvelles données sont ajoutées à la table existante lors de l'exécution de la tâche d'insertion en bloc. Si vous souhaitez remplacer les données, avant de lancer la tâche d'insertion en bloc, utilisez une tâche d'exécution SQL qui applique une instruction DELETE ou TRUNCATE. Pour plus d'informations, consultez [Execute SQL Task](execute-sql-task.md).  
  
-   Vous pouvez utiliser un fichier de format dans l'objet tâche d'insertion en bloc. Si vous avez créé un fichier de format à l'aide de l'utilitaire **bcp** , vous pouvez spécifier son chemin d'accès dans la tâche d'insertion en bloc. La tâche d'insertion en bloc prend en charge les fichiers de format XML et non-XML. Pour plus d’informations sur les fichiers de format, consultez [Fichiers de format pour l’importation ou l’exportation de données &#40;SQL Server&#41;](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).  
  
-   Seuls les membres du rôle serveur fixe sysadmin peuvent exécuter un package contenant une tâche d'insertion en bloc.  
  
## <a name="bulk-insert-task-with-transactions"></a>Tâche d'insertion en bloc avec des transactions  
 Si aucune taille de traitement n'est définie, la copie par bloc complète est traitée comme une transaction. Une taille de traitement égale à **0** indique que les données sont insérées en un seul traitement. Si une taille de traitement est définie, chaque traitement représente une transaction validée à la fin de l'exécution de ce traitement.  
  
 Le fait que la tâche d'insertion en bloc se joigne ou non à la transaction sur package détermine son comportement vis-à-vis des transactions de package. Si la tâche d'insertion en bloc ne se joint pas à la transaction de package, chaque traitement exempt d'erreurs est validé comme une unité, avant que le traitement suivant soit traité. Si la tâche d'insertion en bloc se joint à la transaction de package, les traitements d'instructions exempts d'erreurs restent dans la transaction à la fin de la tâche. Ces traitements sont soumis à la validation ou à l'annulation du package.  
  
 Un échec de la tâche d'insertion en bloc ne provoque pas automatiquement l'annulation des traitements correctement chargés ; de même, si la tâche réussit, les traitements ne sont pas automatiquement validés. La validation et l'annulation ne se produisent qu'en fonction des paramètres de propriétés du package et du flux de travail.  
  
## <a name="source-and-destination"></a>Source et destination  
 Lorsque vous spécifiez l'emplacement du fichier texte source, tenez compte des éléments suivants :  
  
-   Le serveur doit être autorisé à accéder au fichier et à la base de données de destination.  
  
-   Le serveur exécute la tâche d'insertion en bloc. Par conséquent, tout fichier de format utilisé par la tâche doit se trouver sur le serveur.  
  
-   Le fichier source chargé par la tâche d'insertion en bloc peut se trouver sur un serveur distant ou sur le même serveur que la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans laquelle les données sont insérées. Si le fichier se situe sur un serveur distant, vous devez spécifier son nom en indiquant le nom UNC (Universal Naming Convention) dans le chemin d'accès.  
  
## <a name="performance-optimization"></a>Optimisation des performances  
 Pour optimiser les performances, tenez compte des éléments suivants :  
  
-   Si le fichier texte est situé sur le même ordinateur que la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans laquelle les données sont insérées, la copie a lieu à une vitesse plus rapide puisque les données n'ont pas à transiter par le réseau.  
  
-   La tâche d'insertion en bloc n'enregistre pas les lignes à l'origine d'erreurs. Si vous devez capturer ces informations, utilisez les sorties d'erreur des composants de flux de données afin de récupérer dans un fichier d'exception les lignes à l'origine des erreurs.  
  
## <a name="custom-log-entries-available-on-the-bulk-insert-task"></a>Entrées de journal personnalisées disponibles dans la tâche d'insertion en bloc  
 Le tableau suivant répertorie les entrées de journal personnalisées de la tâche d'insertion en bloc. Pour plus d’informations, consultez [Journalisation d’Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../custom-messages-for-logging.md).  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`BulkInsertTaskBegin`|Indique que l'insertion en bloc a commencé.|  
|`BulkInsertTaskEnd`|Indique que l'insertion en bloc est terminée.|  
|`BulkInsertTaskInfos`|Fournit des informations détaillées concernant la tâche.|  
  
## <a name="bulk-insert-task-configuration"></a>Configuration de la tâche d'insertion en bloc  
 Vous pouvez configurer la tâche d'insertion en bloc comme suit :  
  
-   Spécifiez le gestionnaire de connexions OLE DB à utiliser pour établir la connexion à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de destination et la table ou vue dans laquelle les données sont insérées. La tâche d'insertion en bloc prend uniquement en charge les connexions OLE DB de la base de données de destination.  
  
-   Indiquez le gestionnaire de connexions de fichiers ou de fichiers plats pour accéder au fichier source. La tâche d'insertion en bloc utilise le gestionnaire de connexions uniquement pour l'emplacement du fichier source. La tâche ignore les autres options que vous sélectionnez dans l'éditeur de gestionnaire de connexions.  
  
-   Définissez le format adopté par la tâche d'insertion en bloc, soit en utilisant un fichier de format, soit en configurant les séparateurs de colonnes et de lignes des données source. Si vous utilisez un fichier de format, indiquez le gestionnaire de connexions de fichiers permettant d'y accéder.  
  
-   Spécifiez les actions à réaliser dans la table ou la vue de destination au moment où la tâche insère les données. Les options comprennent la vérification éventuelle des contraintes, l'activation des insertions d'identité, la conservation des valeurs NULL, l'exécution des déclencheurs ou le verrouillage de la table.  
  
-   Indiquez les informations relatives au traitement de données à insérer, telles que la taille du traitement, les première et dernière lignes à insérer depuis le fichier, le nombre d'erreurs d'insertion pouvant se produire avant que la tâche arrête d'insérer des lignes et les noms des colonnes à trier.  
  
 Si la tâche d'insertion en bloc se sert d'un gestionnaire de connexions de fichiers plats pour accéder au fichier source, elle n'utilise pas le format spécifié dans ce gestionnaire. Elle utilise à la place le format spécifié dans un fichier de format, ou les valeurs des propriétés RowDelimiter et ColumnDelimiter de la tâche.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche d’insertion en bloc &#40;page général&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Éditeur de tâche d’insertion en bloc &#40;page connexion&#41;](../bulk-insert-task-editor-connection-page.md)  
  
-   [Éditeur de tâche d’insertion en bloc &#40;page Options&#41;](../bulk-insert-task-editor-options-page.md)  
  
-   [Page Expressions](../expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="programmatic-configuration-of-the-bulk-insert-task"></a>Configuration par programme de la tâche d'insertion en bloc  
 Pour plus d'informations sur la définition par programmation de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask>  
  
## <a name="related-tasks"></a>Tâches associées  
 [Définir les propriétés d'une tâche ou d'un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-content"></a>Contenu associé  
  
-   Article technique, [You may get "Unable to prepare the SSIS bulk insert for data insertion" error on UAC enabled systems](https://go.microsoft.com/fwlink/?LinkId=233693)(Vous pouvez obtenir l’erreur « Impossible de préparer l’insertion en bloc SSIS pour l’insertion de données »sur les systèmes UAC), sur support.microsoft.com.  
  
-   Article technique, [Guide des performances de chargement des données](https://go.microsoft.com/fwlink/?LinkId=233700), sur le site msdn.microsoft.com.  
  
-   Article technique, [Using SQL Server Integration Services to Bulk Load Data](https://go.microsoft.com/fwlink/?LinkId=233701), sur le site simple-talk.com.  
  
  
