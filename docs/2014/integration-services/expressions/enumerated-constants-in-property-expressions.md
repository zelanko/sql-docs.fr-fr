---
title: Constantes énumérées dans des expressions de propriété | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], expressions
- dynamic properties
- updating package properties
- enumerated constants [Integration Services]
- property expressions [Integration Services]
ms.assetid: a4418315-38e2-4ad3-8784-576163b25d6f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b22e25ad9053ed4da0187035cff00ff7e3ca70af
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62898897"
---
# <a name="enumerated-constants-in-property-expressions"></a>Constantes énumérées dans des expressions de propriété
  Si des expressions de propriété incluent des valeurs d'une liste de membres d'énumérateur, l'expression doit utiliser la valeur numérique du membre énumérateur et non le nom convivial du membre. Par exemple, si une expression définit la propriété `LoggingMode`, vous devez utiliser la valeur numérique 2 à la place du nom convivial Désactivé.  
  
 Cette rubrique répertorie uniquement les valeurs numériques équivalant aux noms conviviaux d'énumérateurs dont les membres sont fréquemment utilisés dans des expressions de propriété. Le modèle objet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut de nombreux énumérateurs supplémentaires que vous utilisez quand vous programmez le modèle objet pour générer des packages par programmation ou des éléments de package de code personnalisé, tels que des tâches et des composants de flux de données.  
  
 En complément des propriétés personnalisées pour les packages et les objets package, la fenêtre Propriétés de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] inclut un jeu de propriétés accessibles aux packages, aux tâches, ainsi qu'aux conteneurs de boucles Foreach, de boucles For et de séquences. Les propriétés communes qui sont définies par des valeurs provenant d’énumérateurs -`ForceExecutionResult`, `LoggingMode`, `IsolationLevel`, et `Transaction Option`-sont répertoriées dans la section Propriétés communes.  
  
 Les sections suivantes fournissent des informations sur les constantes énumérées :  
  
 [Package](#Package)  
  
 [Énumérateurs de boucles Foreach](#Foreach)  
  
 [Tâches](#Tasks)  
  
 [Tâches du plan de maintenance](#MaintenancePlanTasks)  
  
 [Propriétés communes](#CommonProperties)  
  
##  <a name="Package"></a> Package  
 Les tableaux suivants répertorient les noms conviviaux et les équivalents en valeur numérique pour des propriétés de packages que vous définissez à l'aide de valeurs provenant d'un énumérateur.  
  
 `PackageType` Jeu de propriétés à l’aide de valeurs à partir de la `DTSPackageType` énumération.  
  
|Nom convivial dans DTSPackageType|Valeur numérique|  
|-------------------------------------|-------------------|  
|Par défaut|0|  
|DTSWizard|1|  
|DTSDesigner|2|  
|SQLReplication|3|  
|DTSDesigner100|5|  
|SQLDBMaint|6|  
  
 `CheckpointUsage` Jeu de propriétés à l’aide de valeurs à partir de la `DTSCheckpointUsage` énumération.  
  
|Nom convivial dans DTSCheckpointUsage|Valeur numérique|  
|-----------------------------------------|-------------------|  
|Never|0|  
|IfExists|1|  
|Always|2|  
  
 `PackagePriorityClass` Jeu de propriétés à l’aide de valeurs à partir de la `DTSPriorityClass` énumération.  
  
|Nom convivial dans DTSPriorityClass|Valeur numérique|  
|---------------------------------------|-------------------|  
|Par défaut|0|  
|AboveNormal|1|  
|Normale|2|  
|BelowNormal|3|  
|Idle|4|  
  
 `ProtectionLevel` Jeu de propriétés à l’aide de valeurs à partir de la `DTSProtectionLevel` énumération.  
  
|Nom convivial dans DTSProtectionLevel|Valeur numérique|  
|-----------------------------------------|-------------------|  
|DontSaveSensitive|0|  
|EncryptSensitiveWithUserKey|1|  
|EncryptSensitiveWithPassword|2|  
|EncryptAllWithPassword|3|  
|EncryptAllWithUserKey|4|  
|ServerStorage|5|  
  
##  <a name="PrecedenceConstraints"></a> Contraintes de précédence  
 `EvalOp` Jeu de propriétés à l’aide de valeurs à partir de la `DTSPrecedenceEvalOp` énumération.  
  
|Nom convivial dans DTSPrecedenceEvalOp|Valeur numérique|  
|------------------------------------------|-------------------|  
|Expression|1|  
|Contrainte|2|  
|ExpressionAndConstraint|3|  
|ExpressionOrConstraint|4|  
  
 `Value` Jeu de propriétés à l’aide de valeurs à partir de la `DTSExecResult` énumération.  
  
|Nom convivial|Valeur numérique|  
|-------------------|-------------------|  
|Opération réussie|0|  
|Failure|1|  
|Completion|2|  
|Opération annulée|3|  
  
##  <a name="Foreach"></a> Énumérateurs de boucles Foreach  
 La boucle Foreach inclut un jeu d'énumérateurs comportant des propriétés pouvant être définies par des expressions de la propriété.  
  
### <a name="foreach-ado-enumerator"></a>Énumérateur Foreach ADO  
 `Type` Jeu de propriétés à l’aide de valeurs à partir de la `ADOEnumerationType` énumération.  
  
|Nom convivial dans ADOEnumerationType|Valeur numérique|  
|-----------------------------------------|-------------------|  
|EnumerateTables|0|  
|EnumerateAllRows|1|  
|EnumerateRowsInFirstTable|2|  
  
### <a name="foreach-nodelist-enumerator"></a>Énumérateur Foreach Nodelist  
 `SourceDocumentType`, `InnerXPathStringSourceType`, et **OuterXPathStringSourceType** jeu de propriétés à l’aide de valeurs à partir de la `SourceType` énumération.  
  
|Nom convivial dans SourceType|Valeur numérique|  
|---------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
|DirectInput|2|  
  
 `EnumerationType` Jeu de propriétés à l’aide de valeurs à partir de la `EnumerationType` énumération.  
  
|Nom convivial dans EnumerationType|Valeur numérique|  
|--------------------------------------|-------------------|  
|Navigator|0|  
|Nœud|1|  
|NodeText|2|  
|ElementCollection|3|  
  
 `InnerElementType` Jeu de propriétés à l’aide de valeurs à partir de la `InnerElementType` énumération.  
  
|Nom convivial dans InnerElementType|Valeur numérique|  
|---------------------------------------|-------------------|  
|Navigator|0|  
|Nœud|1|  
|NodeText|2|  
  
##  <a name="Tasks"></a> Tâches  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut de nombreuses tâches avec des propriétés pouvant être définies par des expressions de la propriété.  
  
### <a name="analysis-services-execute-ddl-task"></a>Tâche DDL d'exécution de SQL Server Analysis Services  
 `SourceType` Jeu de propriétés à l’aide de valeurs à partir de la `DDLSourceType` énumération.  
  
|Nom convivial dans DDLSourceType|Valeur numérique|  
|------------------------------------|-------------------|  
|DirectInput|0|  
|FileConnection|1|  
|Variable|2|  
  
### <a name="bulk-insert-task"></a>tâche d'insertion en bloc  
 `DataFileType` Jeu de propriétés à l’aide de valeurs à partir de la `DTSBulkInsert_DataFileType` énumération.  
  
|Nom convivial dans DTSBulkInsert_DataFileType|Valeur numérique|  
|--------------------------------------------------|-------------------|  
|DTSBulkInsert_DataFileType_Char|0|  
|DTSBulkInsert_DataFileType_Native|1|  
|DTSBulkInsert_DataFileType_WideChar|2|  
|DTSBulkInsert_DataFileType_WideNative|3|  
  
### <a name="execute-sql-task"></a>Tâche d’exécution de requêtes SQL  
 `ResultSetType` Jeu de propriétés à l’aide de valeurs à partir de la `ResultSetType` énumération.  
  
|Nom convivial dans ResultSetType|Valeur numérique|  
|------------------------------------|-------------------|  
|ResultSetType_None|1|  
|ResultSetType_SingleRow|2|  
|ResultSetType_Rowset|3|  
|ResultSetType_XML|4|  
  
 `SqlStatementSourceType` Jeu de propriétés à l’aide de valeurs à partir de la `SqlStatementSourceType` énumération.  
  
|Nom convivial dans SqlStatementSourceType|Valeur numérique|  
|---------------------------------------------|-------------------|  
|DirectInput|1|  
|FileConnection|2|  
|Variable|3|  
  
### <a name="file-system-task"></a>Tâches du système de fichiers  
 `Operation` Jeu de propriétés à l’aide de valeurs à partir de la `DTSFileSystemOperation` énumération.  
  
|Nom convivial dans DTSFileSystemOperation|Valeur numérique|  
|---------------------------------------------|-------------------|  
|CopyFile|0|  
|MoveFile|1|  
|DeleteFile|2|  
|RenameFile|3|  
|SetAttributes|4|  
|CreateDirectory|5|  
|CopyDirectory|6|  
|MoveDirectory|7|  
|DeleteDirectory|8|  
|DeleteDirectoryContent|9|  
  
 `Attributes` Jeu de propriétés à l’aide de valeurs à partir de la `DTSFileSystemAttributes` énumération.  
  
|Nom convivial dans DTSFileSystemAttributes|Valeur numérique|  
|----------------------------------------------|-------------------|  
|Normale|0|  
|Archive|1|  
|Hidden|2|  
|En lecture seule|4|  
|Système|8|  
  
### <a name="ftp-task"></a>Tâche FTP  
 `Operation` Jeu de propriétés à l’aide de valeurs à partir de la `DTSFTPOp` énumération.  
  
|Nom convivial dans DTSFTPOp|Valeur numérique|  
|-------------------------------|-------------------|  
|Send|0|  
|Recevoir|1|  
|DeleteLocal|2|  
|DeleteRemote|3|  
|MakeDirLocal|4|  
|MakeDirRemote|5|  
|RemoveDirLocal|6|  
|RemoveDirRemote|7|  
  
### <a name="message-queue-task"></a>Message Queue Task  
 `MessageType` Jeu de propriétés à l’aide de valeurs à partir de la `MQMessageType` énumération.  
  
|Nom convivial dans MQMessageType|Valeur numérique|  
|------------------------------------|-------------------|  
|DTSMQMessageType_String|0|  
|DTSMQMessageType_DataFile|1|  
|DTSMQMessageType_Variables|2|  
|DTSMQMessagType_StringMessageToVariable|3|  
  
 `StringCompareType` Jeu de propriétés à l’aide de valeurs à partir de la `MQStringMessageCompare` énumération.  
  
|Nom convivial dans MQStringMessageCompare|Valeur numérique|  
|---------------------------------------------|-------------------|  
|DTSMQStringMessageCompare_None|0|  
|DTSMQStringMessageCompare_Exact|1|  
|DTSMQStringMessageCompare_IgnoreCase|2|  
|DTSMQStringMessageCompare_Contains|3|  
  
 `TaskType` Jeu de propriétés à l’aide de valeurs à partir de la `MQType` énumération.  
  
|Nom convivial dans MQType|Valeur numérique|  
|-----------------------------|-------------------|  
|DTSMQType_Sender|0|  
|DTSMQType_Receiver|1|  
  
### <a name="send-mail-task"></a>tache Envoyer un message  
 `MessageSourceType` Jeu de propriétés à l’aide de valeurs à partir de la `SendMailMessageSourceType` énumération.  
  
|Nom convivial dans SendMailMessageSourceType|Valeur numérique|  
|------------------------------------------------|-------------------|  
|DirectInput|0|  
|FileConnection|1|  
|Variable|2|  
  
 `Priority` Jeu de propriétés à l’aide de valeurs à partir de la `MailPriority` énumération.  
  
|Nom convivial dans MailPriority|Valeur numérique|  
|-----------------------------------|-------------------|  
|Élevée|1|  
|Normale|3|  
|Faible|5|  
  
### <a name="transfer-database-task"></a>Tâche de transfert de bases de données  
 `Action` Jeu de propriétés à l’aide de valeurs à partir de la `TransferAction` énumération.  
  
|Nom convivial dans TransferAction|Valeur numérique|  
|-------------------------------------|-------------------|  
|Copier|0|  
|Déplacer|1|  
  
 `Method` Jeu de propriétés à l’aide de valeurs à partir de la `TransferMethod` énumération.  
  
|Nom convivial dans TransferMethod|Valeur numérique|  
|-------------------------------------|-------------------|  
|DatabaseOffline|0|  
|DatabaseOnline|1|  
  
### <a name="transfer-error-messages-task"></a>Tâche de transfert de messages d'erreur  
 `IfObjectExists` Jeu de propriétés à l’aide de valeurs à partir de la `IfObjectExists` énumération.  
  
|Nom convivial dans IfObjectExists|Valeur numérique|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Remplacer|1|  
|Ignorer|2|  
  
### <a name="transfer-jobs-task"></a>Tâche de transfert de travaux  
 `IfObjectExists` Jeu de propriétés à l’aide de valeurs à partir de la `IfObjectExists` énumération.  
  
|Nom convivial dans IfObjectExists|Valeur numérique|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Remplacer|1|  
|Ignorer|2|  
  
### <a name="transfer-logins-task"></a>Tâche de transfert de connexions  
 `IfObjectExists` Jeu de propriétés à l’aide de valeurs à partir de la `IfObjectExists` énumération.  
  
|Nom convivial dans IfObjectExists|Valeur numérique|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Remplacer|1|  
|Ignorer|2|  
  
 `LoginsToTransfer` Jeu de propriétés à l’aide de valeurs à partir de la `LoginsToTransfer` énumération.  
  
|Nom convivial dans LoginsToTransfer|Valeur numérique|  
|---------------------------------------|-------------------|  
|AllLogins|0|  
|SelectedLogins|1|  
|AllLoginsFromSelectedDatabases|2|  
  
### <a name="transfer-master-stored-procedures-task"></a>Tâche de transfert de procédures stockées de master  
 `IfObjectExists` Jeu de propriétés à l’aide de valeurs à partir de la `IfObjectExists` énumération.  
  
|Nom convivial dans IfObjectExists|Valeur numérique|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Remplacer|1|  
|Ignorer|2|  
  
### <a name="transfer-sql-server-objects-task"></a>Tâche de transfert d'objets SQL Server  
 `ExistingData` Jeu de propriétés à l’aide de valeurs à partir de la `ExistingData` énumération.  
  
|Nom convivial dans ExistingData|Valeur numérique|  
|-----------------------------------|-------------------|  
|Remplacer|0|  
|Append|1|  
  
### <a name="web-service-task"></a>Tâche de service Web  
 `OutputType` Jeu de propriétés à l’aide de valeurs à partir de la `DTSOutputType` énumération.  
  
|Nom convivial dans DTSOutputType|Valeur numérique|  
|------------------------------------|-------------------|  
|Fichier|0|  
|Variable|1|  
  
### <a name="wmi-data-reader-task"></a>Tâche Lecteur de données WMI  
 `OverwriteDestination` Jeu de propriétés à l’aide de valeurs à partir de la `OverwriteDestination` énumération.  
  
|Nom convivial dans OverwriteDestination|Valeur numérique|  
|-------------------------------------------|-------------------|  
|OverwriteDestination|0|  
|AppendToDestination|1|  
|KeepOriginal|2|  
  
 `OutputType` Jeu de propriétés à l’aide de valeurs à partir de la `OutputType` énumération.  
  
|Nom convivial dans OutputType|Valeur numérique|  
|---------------------------------|-------------------|  
|DataTable|0|  
|PropertyValue|1|  
|PropertyNameAndValue|2|  
  
 `DestinationType` Jeu de propriétés à l’aide de valeurs à partir de la `DestinationType` énumération.  
  
|Nom convivial dans DestinationType|Valeur numérique|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
  
 `WqlQuerySourceType` Jeu de propriétés à l’aide de valeurs à partir de la `QuerySourceType` énumération.  
  
|Nom convivial dans QuerySourceType|Valeur numérique|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|DirectInput|1|  
|Variable|2|  
  
 Observateur d’événement WMI `ActionAtEvent` jeu de propriétés à l’aide de valeurs à partir de la `ActionAtEvent` énumération.  
  
|Nom convivial dans ActionAtEvent|Valeur numérique|  
|------------------------------------|-------------------|  
|LogTheEventAndFireDTSEvent|0|  
|LogTheEvent|1|  
  
 `ActionAtTimeout` Jeu de propriétés à l’aide de valeurs à partir de la `ActionAtTimeout` énumération.  
  
|Nom convivial dans ActionAtTimeout|Valeur numérique|  
|--------------------------------------|-------------------|  
|LogTimeoutAndFireDTSEvent|0|  
|LogTimeout|1|  
  
 `AfterEvent` Jeu de propriétés à l’aide de valeurs à partir de la `AfterEvent` énumération.  
  
|Nom convivial dans AfterEvent|Valeur numérique|  
|---------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `AfterTimeout` Jeu de propriétés à l’aide de valeurs à partir de la `AfterTimeout` énumération.  
  
|Nom convivial dans AfterTimeout|Valeur numérique|  
|-----------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `WqlQuerySourceType` Jeu de propriétés à l’aide de valeurs à partir de la `QuerySourceType` énumération.  
  
|Nom convivial dans QuerySourceType|Valeur numérique|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|DirectInput|1|  
|Variable|2|  
  
### <a name="xml-task"></a>Tâche XML  
 `OperationType` Jeu de propriétés à l’aide de valeurs à partir de la `DTSXMLOperation` énumération.  
  
|Nom convivial dans DTSXMLOperation|Valeur numérique|  
|--------------------------------------|-------------------|  
|Valider|0|  
|XSLT|1|  
|XPATH|2|  
|Fusion|3|  
|Diff|4|  
|Patch|5|  
  
 `SourceType`, `SecondOperandType`, et `XPathSourceType` jeu de propriétés à l’aide de valeurs à partir de la `DTSXMLSourceType` énumération.  
  
|Nom convivial dans DTSXMLSourceType|Valeur numérique|  
|---------------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
|DirectInput|2|  
  
 `DestinationType` et **DiffGramDestinationType** jeu de propriétés à l’aide de valeurs à partir de la `DTSXMLSaveResultTo` énumération.  
  
|Nom convivial dans DTSXMLSaveResultTo|Valeur numérique|  
|-----------------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
  
 `ValidationType` Jeu de propriétés à l’aide de valeurs à partir de la `DTSXMLValidationType` énumération.  
  
|Nom convivial dans DTSXMLValidationType|Valeur numérique|  
|-------------------------------------------|-------------------|  
|DTD|0|  
|XSD|1|  
  
 `XPathOperation` Jeu de propriétés à l’aide de valeurs à partir de la `DTSXMLXPathOperation` énumération.  
  
|Nom convivial dans DTSXMLXPathOperation|Valeur numérique|  
|-------------------------------------------|-------------------|  
|Evaluation|0|  
|Valeurs|1|  
|NodeList|2|  
  
 `DiffOptions` Jeu de propriétés à l’aide de valeurs à partir de la `DTSXMLDiffOptions` énumération. Les options dans cet énumérateur ne sont pas mutuellement exclusives. Pour utiliser plusieurs options, fournissez une liste des options à appliquer, séparées par des virgules.  
  
|Nom convivial dans DTSXMLDiffOptions|Valeur numérique|  
|----------------------------------------|-------------------|  
|None|0|  
|IgnoreChildOrder|1|  
|IgnoreComments|2|  
|IgnorePI|4|  
|IgnoreWhitespace|8|  
|IgnoreNamespaces|16|  
|IgnorePrefixes|32|  
|IgnoreXmlDecl|64|  
|IgnoreDtd|128|  
  
 `DiffAlgorithm` Jeu de propriétés à l’aide de valeurs à partir de la `DTSXMLDiffAlgorithm` énumération.  
  
|Nom convivial dans DTSXMLDiffAlgorithm|Valeur numérique|  
|------------------------------------------|-------------------|  
|Auto|0|  
|Rapide|1|  
|Précise|2|  
  
##  <a name="MaintenancePlanTasks"></a> Tâches du plan de maintenance  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut un ensemble de tâches qui effectuent des tâches SQL Server à utiliser dans des plans de maintenance et dans des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge la gestion de ces tâches par programmation et la documentation de référence de programmation n’inclut pas la documentation API de ces tâches et de leurs énumérateurs.  
  
### <a name="all-maintenance-tasks"></a>Toutes les tâches de maintenance  
 Toutes les tâches de maintenance utilisent les énumérations suivantes pour définir les propriétés spécifiées.  
  
 `DatabaseSelectionType` Jeu de propriétés à l’aide de valeurs à partir de la `DatabaseSelection` énumération.  
  
|Nom convivial dans DatabaseSelection|Valeur numérique|  
|----------------------------------------|-------------------|  
|None|0|  
|All|1|  
|Système|2|  
|Utilisateur|3|  
|Specific|4|  
  
 `TableSelectionType` Jeu de propriétés à l’aide de valeurs à partir de la `TableSelection` énumération.  
  
|Nom convivial dans TableSelection|Valeur numérique|  
|-------------------------------------|-------------------|  
|None|0|  
|All|1|  
|Specific|2|  
  
 `ObjectTypeSelection` Jeu de propriétés à l’aide de valeurs à partir de la `ObjectType` énumération.  
  
|Nom convivial dans ObjectType|Valeur numérique|  
|---------------------------------|-------------------|  
|Table de charge de travail|0|  
|Affichage|1|  
|TableView|2|  
  
### <a name="back-up-database-task"></a>Tâche Sauvegarder la base de données  
 `DestinationCreationType` Jeu de propriétés à l’aide de valeurs à partir de la `DestinationType` énumération.  
  
|Nom convivial dans DestinationType|Valeur numérique|  
|--------------------------------------|-------------------|  
|Auto|0|  
|Manuel|1|  
  
 `ExistingBackupsAction` Jeu de propriétés à l’aide de valeurs à partir de la `ActionForExistingBackups` énumération.  
  
|Nom convivial dans ActionForExistingBackups|Valeur numérique|  
|-----------------------------------------------|-------------------|  
|Ajouter|0|  
|Remplacer|1|  
  
 `BackupAction` Jeu de propriétés à l’aide de valeurs à partir de la `BackupTaskType` énumération. Cette propriété définit avec la propriété `BackupIsIncremental` le type de sauvegarde que la tâche effectue.  
  
|Nom convivial dans BackupTaskType|Valeur numérique|  
|-------------------------------------|-------------------|  
|Base de données|0|  
|Fichiers|1|  
|Journal|2|  
  
 `BackupDevice` Jeu de propriétés à l’aide de valeurs à partir de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) `DeviceType` énumération.  
  
|Nom convivial dans DeviceType|Valeur numérique|  
|---------------------------------|-------------------|  
|LogicalDevice|0|  
|Bande|1|  
|Fichier|2|  
|Pipe|3|  
|VirtualDevice|4|  
  
### <a name="maintenance-cleanup-task"></a>Tâche de nettoyage de maintenance  
 `FileTypeSelected` Jeu de propriétés à l’aide de valeurs à partir de la `FileType` énumération.  
  
|Nom convivial dans FileType|Valeur numérique|  
|-------------------------------|-------------------|  
|FileBackup|0|  
|FileReport|1|  
  
 `OlderThanTimeUnitType` Jeu de propriétés à l’aide de valeurs à partir de la `TimeUnitType` énumération.  
  
|Nom convivial dans TimeUnitType|Valeur numérique|  
|-----------------------------------|-------------------|  
|Jour|0|  
|Week|1|  
|Month|2|  
|Année|3|  
  
### <a name="update-statistics-task"></a>Tâche Mettre à jour les statistiques  
 `UpdateType` Jeu de propriétés à l’aide de valeurs à partir de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) `StatisticsTarget` énumération.  
  
|Nom convivial dans StatisticsTarget|Valeur numérique|  
|---------------------------------------|-------------------|  
|colonne|1|  
|Index|2|  
|All|3|  
  
##  <a name="CommonProperties"></a> Propriétés communes  
 Les packages, les tâches et les conteneurs de boucles Foreach, de boucles For et de séquences peuvent utiliser les énumérations suivantes pour définir les propriétés spécifiées.  
  
 `ForceExecutionResult` Jeu de propriétés à l’aide de valeurs à partir de la `DTSForcedExecResult` énumération.  
  
|Nom convivial dans DTSForcedExecResult|Valeur numérique|  
|------------------------------------------|-------------------|  
|None|-1|  
|Opération réussie|0|  
|Failure|1|  
|Completion|2|  
  
 `IsolationLevel` Jeu de propriétés par le .NET Framework `IsolationLevel` énumération. Pour plus d’informations, consultez la bibliothèque de classes .NET Framework dans [MSDN Library](https://go.microsoft.com/fwlink?LinkId=17313).  
  
 `LoggingMode` Jeu de propriétés à l’aide de valeurs à partir de la `DTSLoggingMode` énumération.  
  
|Nom convivial dans DTSLoggingMode|Valeur numérique|  
|-------------------------------------|-------------------|  
|UseParentSetting|0|  
|Enabled|1|  
|Désactivé|2|  
  
 `TransactionOption` Jeu de propriétés à l’aide de valeurs à partir de la `DTSTransactionOption` énumération.  
  
|Nom convivial dans DTSTransactionOption|Valeur numérique|  
|-------------------------------------------|-------------------|  
|NotSupported|0|  
|Pris en charge|1|  
|Requis|2|  
  
## <a name="related-tasks"></a>Tâches associées  
 [Ajouter ou modifier une expression de propriété](add-or-change-a-property-expression.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions de propriété dans des packages](use-property-expressions-in-packages.md)   
 [Packages Integration Services &#40;SSIS&#41;](../integration-services-ssis-packages.md)   
 [Conteneurs Integration Services](../control-flow/integration-services-containers.md)   
 [Tâches Integration Services](../control-flow/integration-services-tasks.md)   
 [Contraintes de précédence](../control-flow/precedence-constraints.md)  
  
  
