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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62898897"
---
# <a name="enumerated-constants-in-property-expressions"></a>Constantes énumérées dans des expressions de propriété
  Si des expressions de propriété incluent des valeurs d'une liste de membres d'énumérateur, l'expression doit utiliser la valeur numérique du membre énumérateur et non le nom convivial du membre. Par exemple, si une expression définit la propriété `LoggingMode`, vous devez utiliser la valeur numérique 2 à la place du nom convivial Désactivé.  
  
 Cette rubrique répertorie uniquement les valeurs numériques équivalant aux noms conviviaux d'énumérateurs dont les membres sont fréquemment utilisés dans des expressions de propriété. Le modèle objet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut de nombreux énumérateurs supplémentaires que vous utilisez quand vous programmez le modèle objet pour générer des packages par programmation ou des éléments de package de code personnalisé, tels que des tâches et des composants de flux de données.  
  
 En complément des propriétés personnalisées pour les packages et les objets package, la fenêtre Propriétés de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] inclut un jeu de propriétés accessibles aux packages, aux tâches, ainsi qu'aux conteneurs de boucles Foreach, de boucles For et de séquences. Les propriétés communes qui sont définies par des valeurs provenant d’énumérateurs `LoggingMode`- `IsolationLevel``ForceExecutionResult`,, `Transaction Option`et-sont répertoriées dans la section Propriétés communes.  
  
 Les sections suivantes fournissent des informations sur les constantes énumérées :  
  
 [Package](#Package)  
  
 [Énumérateurs de boucles Foreach](#Foreach)  
  
 [Tâches :](#Tasks)  
  
 [Tâches du plan de maintenance](#MaintenancePlanTasks)  
  
 [Propriétés communes](#CommonProperties)  
  
##  <a name="Package"></a> Package  
 Les tableaux suivants répertorient les noms conviviaux et les équivalents en valeur numérique pour des propriétés de packages que vous définissez à l'aide de valeurs provenant d'un énumérateur.  
  
 `PackageType`Définie par la propriété à l’aide des `DTSPackageType` valeurs de l’énumération.  
  
|Nom convivial dans DTSPackageType|Valeur numérique|  
|-------------------------------------|-------------------|  
|Default|0|  
|DTSWizard|1|  
|DTSDesigner|2|  
|SQLReplication|3|  
|DTSDesigner100|5|  
|SQLDBMaint|6|  
  
 `CheckpointUsage`Définie par la propriété à l’aide des `DTSCheckpointUsage` valeurs de l’énumération.  
  
|Nom convivial dans DTSCheckpointUsage|Valeur numérique|  
|-----------------------------------------|-------------------|  
|Jamais|0|  
|IfExists|1|  
|Toujours|2|  
  
 `PackagePriorityClass`Définie par la propriété à l’aide des `DTSPriorityClass` valeurs de l’énumération.  
  
|Nom convivial dans DTSPriorityClass|Valeur numérique|  
|---------------------------------------|-------------------|  
|Default|0|  
|AboveNormal|1|  
|Normal|2|  
|BelowNormal|3|  
|Idle|4|  
  
 `ProtectionLevel`Définie par la propriété à l’aide des `DTSProtectionLevel` valeurs de l’énumération.  
  
|Nom convivial dans DTSProtectionLevel|Valeur numérique|  
|-----------------------------------------|-------------------|  
|DontSaveSensitive|0|  
|EncryptSensitiveWithUserKey|1|  
|EncryptSensitiveWithPassword|2|  
|EncryptAllWithPassword|3|  
|EncryptAllWithUserKey|4|  
|ServerStorage|5|  
  
##  <a name="PrecedenceConstraints"></a> Contraintes de précédence  
 `EvalOp`Définie par la propriété à l’aide des `DTSPrecedenceEvalOp` valeurs de l’énumération.  
  
|Nom convivial dans DTSPrecedenceEvalOp|Valeur numérique|  
|------------------------------------------|-------------------|  
|Expression|1|  
|Contrainte|2|  
|ExpressionAndConstraint|3|  
|ExpressionOrConstraint|4|  
  
 `Value`Définie par la propriété à l’aide des `DTSExecResult` valeurs de l’énumération.  
  
|Nom convivial|Valeur numérique|  
|-------------------|-------------------|  
|Succès|0|  
|Échec|1|  
|Completion|2|  
|Opération annulée|3|  
  
##  <a name="Foreach"></a> Énumérateurs de boucles Foreach  
 La boucle Foreach inclut un jeu d'énumérateurs comportant des propriétés pouvant être définies par des expressions de la propriété.  
  
### <a name="foreach-ado-enumerator"></a>Énumérateur Foreach ADO  
 `Type`Définie par la propriété à l’aide des `ADOEnumerationType` valeurs de l’énumération.  
  
|Nom convivial dans ADOEnumerationType|Valeur numérique|  
|-----------------------------------------|-------------------|  
|EnumerateTables|0|  
|EnumerateAllRows|1|  
|EnumerateRowsInFirstTable|2|  
  
### <a name="foreach-nodelist-enumerator"></a>Énumérateur Foreach Nodelist  
 `SourceDocumentType`propriétés `InnerXPathStringSourceType`, et **OuterXPathStringSourceType** -définies à l’aide des valeurs de `SourceType` l’énumération.  
  
|Nom convivial dans SourceType|Valeur numérique|  
|---------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
|DirectInput|2|  
  
 `EnumerationType`Définie par la propriété à l’aide des `EnumerationType` valeurs de l’énumération.  
  
|Nom convivial dans EnumerationType|Valeur numérique|  
|--------------------------------------|-------------------|  
|Navigateur|0|  
|Nœud|1|  
|NodeText|2|  
|ElementCollection|3|  
  
 `InnerElementType`Définie par la propriété à l’aide des `InnerElementType` valeurs de l’énumération.  
  
|Nom convivial dans InnerElementType|Valeur numérique|  
|---------------------------------------|-------------------|  
|Navigateur|0|  
|Nœud|1|  
|NodeText|2|  
  
##  <a name="Tasks"></a> Tâches  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut de nombreuses tâches avec des propriétés pouvant être définies par des expressions de la propriété.  
  
### <a name="analysis-services-execute-ddl-task"></a>Tâche DDL d'exécution de SQL Server Analysis Services  
 `SourceType`Définie par la propriété à l’aide des `DDLSourceType` valeurs de l’énumération.  
  
|Nom convivial dans DDLSourceType|Valeur numérique|  
|------------------------------------|-------------------|  
|DirectInput|0|  
|FileConnection|1|  
|Variable|2|  
  
### <a name="bulk-insert-task"></a>tâche d'insertion en bloc  
 `DataFileType`Définie par la propriété à l’aide des `DTSBulkInsert_DataFileType` valeurs de l’énumération.  
  
|Nom convivial dans DTSBulkInsert_DataFileType|Valeur numérique|  
|--------------------------------------------------|-------------------|  
|DTSBulkInsert_DataFileType_Char|0|  
|DTSBulkInsert_DataFileType_Native|1|  
|DTSBulkInsert_DataFileType_WideChar|2|  
|DTSBulkInsert_DataFileType_WideNative|3|  
  
### <a name="execute-sql-task"></a>Tâche d’exécution de requêtes SQL  
 `ResultSetType`Définie par la propriété à l’aide des `ResultSetType` valeurs de l’énumération.  
  
|Nom convivial dans ResultSetType|Valeur numérique|  
|------------------------------------|-------------------|  
|ResultSetType_None|1|  
|ResultSetType_SingleRow|2|  
|ResultSetType_Rowset|3|  
|ResultSetType_XML|4|  
  
 `SqlStatementSourceType`Définie par la propriété à l’aide des `SqlStatementSourceType` valeurs de l’énumération.  
  
|Nom convivial dans SqlStatementSourceType|Valeur numérique|  
|---------------------------------------------|-------------------|  
|DirectInput|1|  
|FileConnection|2|  
|Variable|3|  
  
### <a name="file-system-task"></a>Tâches du système de fichiers  
 `Operation`Définie par la propriété à l’aide des `DTSFileSystemOperation` valeurs de l’énumération.  
  
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
  
 `Attributes`Définie par la propriété à l’aide des `DTSFileSystemAttributes` valeurs de l’énumération.  
  
|Nom convivial dans DTSFileSystemAttributes|Valeur numérique|  
|----------------------------------------------|-------------------|  
|Normal|0|  
|Archivage|1|  
|Hidden|2|  
|Lecture seule|4|  
|Système|8|  
  
### <a name="ftp-task"></a>Tâche FTP  
 `Operation`Définie par la propriété à l’aide des `DTSFTPOp` valeurs de l’énumération.  
  
|Nom convivial dans DTSFTPOp|Valeur numérique|  
|-------------------------------|-------------------|  
|Envoyer|0|  
|Recevoir|1|  
|DeleteLocal|2|  
|DeleteRemote|3|  
|MakeDirLocal|4|  
|MakeDirRemote|5|  
|RemoveDirLocal|6|  
|RemoveDirRemote|7|  
  
### <a name="message-queue-task"></a>Message Queue Task  
 `MessageType`Définie par la propriété à l’aide des `MQMessageType` valeurs de l’énumération.  
  
|Nom convivial dans MQMessageType|Valeur numérique|  
|------------------------------------|-------------------|  
|DTSMQMessageType_String|0|  
|DTSMQMessageType_DataFile|1|  
|DTSMQMessageType_Variables|2|  
|DTSMQMessagType_StringMessageToVariable|3|  
  
 `StringCompareType`Définie par la propriété à l’aide des `MQStringMessageCompare` valeurs de l’énumération.  
  
|Nom convivial dans MQStringMessageCompare|Valeur numérique|  
|---------------------------------------------|-------------------|  
|DTSMQStringMessageCompare_None|0|  
|DTSMQStringMessageCompare_Exact|1|  
|DTSMQStringMessageCompare_IgnoreCase|2|  
|DTSMQStringMessageCompare_Contains|3|  
  
 `TaskType`Définie par la propriété à l’aide des `MQType` valeurs de l’énumération.  
  
|Nom convivial dans MQType|Valeur numérique|  
|-----------------------------|-------------------|  
|DTSMQType_Sender|0|  
|DTSMQType_Receiver|1|  
  
### <a name="send-mail-task"></a>tache Envoyer un message  
 `MessageSourceType`Définie par la propriété à l’aide des `SendMailMessageSourceType` valeurs de l’énumération.  
  
|Nom convivial dans SendMailMessageSourceType|Valeur numérique|  
|------------------------------------------------|-------------------|  
|DirectInput|0|  
|FileConnection|1|  
|Variable|2|  
  
 `Priority`Définie par la propriété à l’aide des `MailPriority` valeurs de l’énumération.  
  
|Nom convivial dans MailPriority|Valeur numérique|  
|-----------------------------------|-------------------|  
|Élevé|1|  
|Normal|3|  
|Faible|5|  
  
### <a name="transfer-database-task"></a>Tâche de transfert de bases de données  
 `Action`Définie par la propriété à l’aide des `TransferAction` valeurs de l’énumération.  
  
|Nom convivial dans TransferAction|Valeur numérique|  
|-------------------------------------|-------------------|  
|Copier|0|  
|Déplacer|1|  
  
 `Method`Définie par la propriété à l’aide des `TransferMethod` valeurs de l’énumération.  
  
|Nom convivial dans TransferMethod|Valeur numérique|  
|-------------------------------------|-------------------|  
|DatabaseOffline|0|  
|DatabaseOnline|1|  
  
### <a name="transfer-error-messages-task"></a>Tâche de transfert de messages d'erreur  
 `IfObjectExists`Définie par la propriété à l’aide des `IfObjectExists` valeurs de l’énumération.  
  
|Nom convivial dans IfObjectExists|Valeur numérique|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Remplacer|1|  
|Ignorer|2|  
  
### <a name="transfer-jobs-task"></a>Tâche de transfert de travaux  
 `IfObjectExists`Définie par la propriété à l’aide des `IfObjectExists` valeurs de l’énumération.  
  
|Nom convivial dans IfObjectExists|Valeur numérique|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Remplacer|1|  
|Ignorer|2|  
  
### <a name="transfer-logins-task"></a>Tâche de transfert de connexions  
 `IfObjectExists`Définie par la propriété à l’aide des `IfObjectExists` valeurs de l’énumération.  
  
|Nom convivial dans IfObjectExists|Valeur numérique|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Remplacer|1|  
|Ignorer|2|  
  
 `LoginsToTransfer`Définie par la propriété à l’aide des `LoginsToTransfer` valeurs de l’énumération.  
  
|Nom convivial dans LoginsToTransfer|Valeur numérique|  
|---------------------------------------|-------------------|  
|AllLogins|0|  
|SelectedLogins|1|  
|AllLoginsFromSelectedDatabases|2|  
  
### <a name="transfer-master-stored-procedures-task"></a>Tâche de transfert de procédures stockées de master  
 `IfObjectExists`Définie par la propriété à l’aide des `IfObjectExists` valeurs de l’énumération.  
  
|Nom convivial dans IfObjectExists|Valeur numérique|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Remplacer|1|  
|Ignorer|2|  
  
### <a name="transfer-sql-server-objects-task"></a>Tâche de transfert d'objets SQL Server  
 `ExistingData`Définie par la propriété à l’aide des `ExistingData` valeurs de l’énumération.  
  
|Nom convivial dans ExistingData|Valeur numérique|  
|-----------------------------------|-------------------|  
|Replace|0|  
|Ajouter|1|  
  
### <a name="web-service-task"></a>Tâche de service Web  
 `OutputType`Définie par la propriété à l’aide des `DTSOutputType` valeurs de l’énumération.  
  
|Nom convivial dans DTSOutputType|Valeur numérique|  
|------------------------------------|-------------------|  
|Fichier|0|  
|Variable|1|  
  
### <a name="wmi-data-reader-task"></a>Tâche Lecteur de données WMI  
 `OverwriteDestination`Définie par la propriété à l’aide des `OverwriteDestination` valeurs de l’énumération.  
  
|Nom convivial dans OverwriteDestination|Valeur numérique|  
|-------------------------------------------|-------------------|  
|OverwriteDestination|0|  
|AppendToDestination|1|  
|KeepOriginal|2|  
  
 `OutputType`Définie par la propriété à l’aide des `OutputType` valeurs de l’énumération.  
  
|Nom convivial dans OutputType|Valeur numérique|  
|---------------------------------|-------------------|  
|DataTable|0|  
|PropertyValue|1|  
|PropertyNameAndValue|2|  
  
 `DestinationType`Définie par la propriété à l’aide des `DestinationType` valeurs de l’énumération.  
  
|Nom convivial dans DestinationType|Valeur numérique|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
  
 `WqlQuerySourceType`Définie par la propriété à l’aide des `QuerySourceType` valeurs de l’énumération.  
  
|Nom convivial dans QuerySourceType|Valeur numérique|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|DirectInput|1|  
|Variable|2|  
  
 Propriété observateur `ActionAtEvent` d’événement WMI-défini à l’aide des `ActionAtEvent` valeurs de l’énumération.  
  
|Nom convivial dans ActionAtEvent|Valeur numérique|  
|------------------------------------|-------------------|  
|LogTheEventAndFireDTSEvent|0|  
|LogTheEvent|1|  
  
 `ActionAtTimeout`Définie par la propriété à l’aide des `ActionAtTimeout` valeurs de l’énumération.  
  
|Nom convivial dans ActionAtTimeout|Valeur numérique|  
|--------------------------------------|-------------------|  
|LogTimeoutAndFireDTSEvent|0|  
|LogTimeout|1|  
  
 `AfterEvent`Définie par la propriété à l’aide des `AfterEvent` valeurs de l’énumération.  
  
|Nom convivial dans AfterEvent|Valeur numérique|  
|---------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `AfterTimeout`Définie par la propriété à l’aide des `AfterTimeout` valeurs de l’énumération.  
  
|Nom convivial dans AfterTimeout|Valeur numérique|  
|-----------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `WqlQuerySourceType`Définie par la propriété à l’aide des `QuerySourceType` valeurs de l’énumération.  
  
|Nom convivial dans QuerySourceType|Valeur numérique|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|DirectInput|1|  
|Variable|2|  
  
### <a name="xml-task"></a>Tâche XML  
 `OperationType`Définie par la propriété à l’aide des `DTSXMLOperation` valeurs de l’énumération.  
  
|Nom convivial dans DTSXMLOperation|Valeur numérique|  
|--------------------------------------|-------------------|  
|Valider|0|  
|XSLT|1|  
|XPATH|2|  
|Fusionner|3|  
|Diff|4|  
|Correctif|5|  
  
 `SourceType`propriétés `SecondOperandType`, et `XPathSourceType` définies à l’aide des valeurs de l' `DTSXMLSourceType` Énumération.  
  
|Nom convivial dans DTSXMLSourceType|Valeur numérique|  
|---------------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
|DirectInput|2|  
  
 `DestinationType`et les propriétés **DiffGramDestinationType** -définies à l’aide des `DTSXMLSaveResultTo` valeurs de l’énumération.  
  
|Nom convivial dans DTSXMLSaveResultTo|Valeur numérique|  
|-----------------------------------------|-------------------|  
|FileConnection|0|  
|Variable|1|  
  
 `ValidationType`Définie par la propriété à l’aide des `DTSXMLValidationType` valeurs de l’énumération.  
  
|Nom convivial dans DTSXMLValidationType|Valeur numérique|  
|-------------------------------------------|-------------------|  
|DTD|0|  
|XSD|1|  
  
 `XPathOperation`Définie par la propriété à l’aide des `DTSXMLXPathOperation` valeurs de l’énumération.  
  
|Nom convivial dans DTSXMLXPathOperation|Valeur numérique|  
|-------------------------------------------|-------------------|  
|Évaluation|0|  
|Valeurs|1|  
|NodeList|2|  
  
 `DiffOptions`Définie par la propriété à l’aide des `DTSXMLDiffOptions` valeurs de l’énumération. Les options dans cet énumérateur ne sont pas mutuellement exclusives. Pour utiliser plusieurs options, fournissez une liste des options à appliquer, séparées par des virgules.  
  
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
  
 `DiffAlgorithm`Définie par la propriété à l’aide des `DTSXMLDiffAlgorithm` valeurs de l’énumération.  
  
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
  
 `DatabaseSelectionType`Définie par la propriété à l’aide des `DatabaseSelection` valeurs de l’énumération.  
  
|Nom convivial dans DatabaseSelection|Valeur numérique|  
|----------------------------------------|-------------------|  
|None|0|  
|Tous|1|  
|Système|2|  
|Utilisateur|3|  
|Spécifique|4|  
  
 `TableSelectionType`Définie par la propriété à l’aide des `TableSelection` valeurs de l’énumération.  
  
|Nom convivial dans TableSelection|Valeur numérique|  
|-------------------------------------|-------------------|  
|None|0|  
|Tous|1|  
|Spécifique|2|  
  
 `ObjectTypeSelection`Définie par la propriété à l’aide des `ObjectType` valeurs de l’énumération.  
  
|Nom convivial dans ObjectType|Valeur numérique|  
|---------------------------------|-------------------|  
|Table de charge de travail|0|  
|Affichage|1|  
|TableView|2|  
  
### <a name="back-up-database-task"></a>Tâche Sauvegarder la base de données  
 `DestinationCreationType`Définie par la propriété à l’aide des `DestinationType` valeurs de l’énumération.  
  
|Nom convivial dans DestinationType|Valeur numérique|  
|--------------------------------------|-------------------|  
|Auto|0|  
|Manuel|1|  
  
 `ExistingBackupsAction`Définie par la propriété à l’aide des `ActionForExistingBackups` valeurs de l’énumération.  
  
|Nom convivial dans ActionForExistingBackups|Valeur numérique|  
|-----------------------------------------------|-------------------|  
|Ajouter|0|  
|Remplacer|1|  
  
 `BackupAction`Définie par la propriété à l’aide des `BackupTaskType` valeurs de l’énumération. Cette propriété définit avec la propriété `BackupIsIncremental` le type de sauvegarde que la tâche effectue.  
  
|Nom convivial dans BackupTaskType|Valeur numérique|  
|-------------------------------------|-------------------|  
|Base de données|0|  
|Fichiers|1|  
|Journal|2|  
  
 `BackupDevice`Défini par la propriété à l’aide de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valeurs provenant de l’énumération Smo (Management Objects) `DeviceType` .  
  
|Nom convivial dans DeviceType|Valeur numérique|  
|---------------------------------|-------------------|  
|LogicalDevice|0|  
|Bande|1|  
|Fichier|2|  
|Pipe|3|  
|VirtualDevice|4|  
  
### <a name="maintenance-cleanup-task"></a>Tâche de nettoyage de maintenance  
 `FileTypeSelected`Définie par la propriété à l’aide des `FileType` valeurs de l’énumération.  
  
|Nom convivial dans FileType|Valeur numérique|  
|-------------------------------|-------------------|  
|FileBackup|0|  
|FileReport|1|  
  
 `OlderThanTimeUnitType`Définie par la propriété à l’aide des `TimeUnitType` valeurs de l’énumération.  
  
|Nom convivial dans TimeUnitType|Valeur numérique|  
|-----------------------------------|-------------------|  
|jour|0|  
|Week|1|  
|Month|2|  
|Year|3|  
  
### <a name="update-statistics-task"></a>Tâche Mettre à jour les statistiques  
 `UpdateType`Défini par la propriété à l’aide de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valeurs provenant de l’énumération Smo (Management Objects) `StatisticsTarget` .  
  
|Nom convivial dans StatisticsTarget|Valeur numérique|  
|---------------------------------------|-------------------|  
|Colonne|1|  
|Index|2|  
|Tous|3|  
  
##  <a name="CommonProperties"></a> Propriétés communes  
 Les packages, les tâches et les conteneurs de boucles Foreach, de boucles For et de séquences peuvent utiliser les énumérations suivantes pour définir les propriétés spécifiées.  
  
 `ForceExecutionResult`Définie par la propriété à l’aide des `DTSForcedExecResult` valeurs de l’énumération.  
  
|Nom convivial dans DTSForcedExecResult|Valeur numérique|  
|------------------------------------------|-------------------|  
|None|-1|  
|Succès|0|  
|Échec|1|  
|Completion|2|  
  
 `IsolationLevel`propriété définie par l’énumération `IsolationLevel` .NET Framework. Pour plus d’informations, consultez la bibliothèque de classes .NET Framework dans [MSDN Library](https://go.microsoft.com/fwlink?LinkId=17313).  
  
 `LoggingMode`Définie par la propriété à l’aide des `DTSLoggingMode` valeurs de l’énumération.  
  
|Nom convivial dans DTSLoggingMode|Valeur numérique|  
|-------------------------------------|-------------------|  
|UseParentSetting|0|  
|activé|1|  
|Désactivé|2|  
  
 `TransactionOption`Définie par la propriété à l’aide des `DTSTransactionOption` valeurs de l’énumération.  
  
|Nom convivial dans DTSTransactionOption|Valeur numérique|  
|-------------------------------------------|-------------------|  
|NotSupported|0|  
|Prise en charge|1|  
|Obligatoire|2|  
  
## <a name="related-tasks"></a>Tâches associées  
 [Ajouter ou modifier une expression de propriété](add-or-change-a-property-expression.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions de propriété dans des packages](use-property-expressions-in-packages.md)   
 [Packages Integration Services &#40;SSIS&#41;](../integration-services-ssis-packages.md)   
 [Conteneurs Integration Services](../control-flow/integration-services-containers.md)   
 [Tâches Integration Services](../control-flow/integration-services-tasks.md)   
 [Contraintes de précédence](../control-flow/precedence-constraints.md)  
  
  
