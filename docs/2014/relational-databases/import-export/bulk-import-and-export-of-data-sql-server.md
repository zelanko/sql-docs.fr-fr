---
title: Importation et exportation en bloc de données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- exporting data
- bulk importing [SQL Server], about bulk importing
- data [SQL Server], bulk export and import
- transferring data
- importing data, (See also bulk importing [SQL Server])
- copying data [SQL Server]
- bulk exporting [SQL Server]
- importing data, bulk import
- copying data [SQL Server], bulk export and import
- exporting data,(See also bulk exporting [SQL Server])
- bulk exporting [SQL Server], about bulk exporting
- bulk importing [SQL Server]
- importing data
ms.assetid: 19049021-c048-44a2-b38d-186d9f9e4a65
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a80eb337bfc03d826ab0933ac235f76dd16bfde9
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52525647"
---
# <a name="bulk-import-and-export-of-data-sql-server"></a>Importation et exportation en bloc de données (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge l’exportation en bloc de données (*données en bloc*) à partir d’une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et l’importation en bloc de données dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou une vue non partitionnée. L'importation et l'exportation en bloc sont essentielles pour transférer efficacement des données entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des sources de données hétérogènes. L'*exportation en bloc* consiste à copier des données d'une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers un fichier de données. Le terme*importation en bloc* fait référence au chargement de données d’un fichier de données vers une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Par exemple, vous pouvez exporter des données d'une application [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel vers un fichier de données, puis importer en bloc ces données dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Dans cette rubrique :**  
  
-   [Introduction à l’importation en bloc et les opérations d’exportation en bloc](#Intro)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="Intro"></a> Importation en bloc et présentation d’exportation en bloc  
 Cette section répertorie et compare brièvement les diverses méthodes disponibles pour l'importation et l'exportation de données en bloc. La section présente également des fichiers de format.  
  
 **Dans cette rubrique :**  
  
-   [Méthodes pour l’importation et exportation de données en bloc](#MethodsForBuliIE)  
  
-   [Fichiers de format](#FFs)  
  
###  <a name="MethodsForBuliIE"></a> Méthodes pour l’importation et exportation de données en bloc  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge l'exportation en bloc de données à partir d'une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et l'importation en bloc de données dans une table ou une vue non partitionnée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les méthodes de base disponibles sont les suivantes.  
  
|Méthode|Description|Importe les données|Exporte les données|  
|------------|-----------------|------------------|------------------|  
|[bcp (utilitaire)](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)|Utilitaire en ligne de commande (Bcp.exe) qui exporte et importe en bloc des données et génère des fichiers de format.|Oui|Oui|  
|[BULK INSERT, instruction](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|Instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] qui importe des données directement d'un fichier de données dans une table de base de données ou une vue non partitionnée.|Oui|Non|  
|instruction [INSERT ... instruction SELECT * FROM OPENROWSET(BULK...)](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)|Instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] qui utilise le fournisseur d’ensembles de lignes OPENROWSET pour importer en bloc des données dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en spécifiant la fonction OPENROWSET(BULK...) afin de sélectionner des données dans une instruction INSERT.|Oui|Non|  
  
> [!IMPORTANT]  
>  Les fichiers de valeurs séparées par des virgules (CSV, Comma-Separated Value) ne sont pas pris en charge par les opérations d'importation en bloc SQL Server. Toutefois, dans certains cas, un fichier CSV peut être utilisé comme fichier de données pour une importation en bloc de données dans SQL Server. Notez que la marque de fin de champ d'un fichier CSV n'est pas nécessairement une virgule. Pour plus d’informations, consultez [Préparer des données en vue d’une exportation ou d’une importation en bloc &#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md).  
  
###  <a name="FFs"></a> Fichiers de format  
 L’utilitaire **bcp**, BULK INSERT et INSERT ... SELECT \* FROM OPENROWSET(BULK...) gèrent tous l’utilisation d’un *fichier de format* spécialisé qui stocke les informations de format de chaque champ dans un fichier de données. Un fichier de format peut également contenir des informations sur la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] correspondante. Le fichier de format peut être utilisé pour fournir toutes les informations de format nécessaires pour exporter en bloc des données à partir d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]et pour importer en bloc des données vers une instance du même type.  
  
 Les fichiers de format procurent une souplesse qui permet d'une part l'interprétation des données tel qu'elles existent dans le fichier de données au moment de l'importation, et d'autre part le formatage des données dans le fichier de données au moment de l'exportation. Cette souplesse vous dispense d'écrire un code spécial en vue d'interpréter ou de reformater les données en fonction des exigences spécifiques de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l'application externe. Ainsi, si les données exportées en bloc doivent être chargées dans une application nécessitant des valeurs séparées par une virgule, vous pouvez utiliser un fichier de format pour insérer des virgules comme terminateurs de champ dans les données exportées.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge deux types de fichiers de format : Fichiers de format XML et les fichiers de format non-XML.  
  
 Le seul outil capable de générer un fichier de format est l'utilitaire **bcp** . Pour plus d’informations, consultez [Créer un fichier de format &#40;SQL Server&#41;](create-a-format-file-sql-server.md). Pour plus d’informations sur les fichiers de format, consultez [Fichiers de format pour l’importation ou l’exportation de données &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
> [!NOTE]  
>  Si, à l'occasion d'une opération d'exportation ou d'importation en bloc, aucun fichier de format n'est fourni, vous pouvez choisir de remplacer le formatage par défaut via la ligne de commande.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Importer et exporter des données en bloc à l’aide de l’utilitaire bcp &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)  
  
-   [Importer des données en bloc à l’aide de BULK INSERT ou OPENROWSET&#40;en bloc... &#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)  
  
-   [Conserver des valeurs d’identité lors de l’importation de données en bloc &#40;SQL Server&#41;](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Conserver les valeurs NULL ou utiliser la valeur par défaut lors de l’importation en bloc &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Préparer des données en vue d’une exportation ou d’une importation en bloc &#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 **Pour utiliser un fichier de format**  
  
-   [Créer un fichier de format &#40;SQL Server&#41;](create-a-format-file-sql-server.md)  
  
-   [Utiliser un fichier de format pour importer des données en bloc &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Utiliser un fichier de format pour mapper les colonnes d’une table sur les champs d’un fichier de données &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [Utiliser un fichier de format pour ignorer un champ de données &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Utiliser un fichier de format pour ignorer une colonne de table &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 **Pour utiliser des formats de données pour l'importation ou l'exportation en bloc**  
  
-   [Importer des données au format natif et caractère à partir de versions antérieures de SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Utiliser le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif pour importer ou exporter des données &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 **Pour spécifier des formats de données pour la compatibilité lors de l'utilisation de bcp**  
  
1.  [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)  
  
2.  [Spécifier une longueur de préfixe dans des fichiers de données à l’aide de bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [Spécifier le type de stockage de fichiers à l’aide de bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Conditions requises pour une journalisation minimale dans l'importation en bloc](prerequisites-for-minimal-logging-in-bulk-import.md)   
 [Fichiers de format pour l’importation ou l’exportation de données &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)   
 [Exemples d’importation et d’exportation en bloc de documents XML &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)   
 [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)   
 [Copier des bases de données sur d'autres serveurs](../databases/copy-databases-to-other-servers.md)   
 [Exécution du chargement en masse de données XML &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)   
 [Exécution d’opérations de copie en bloc](../native-client/features/performing-bulk-copy-operations.md)   
 [Utilitaire bcp](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Fichiers de format pour l’importation ou l’exportation de données &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
