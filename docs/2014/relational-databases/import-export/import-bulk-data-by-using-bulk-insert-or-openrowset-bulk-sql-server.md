---
title: Importer des données en bloc à l’aide de BULK INSERT ou OPENROWSET(BULK...) (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- BULK INSERT statement, importing data from a remote data file
- bulk importing [SQL Server], methods
- bulk exporting [SQL Server], methods
- OPENROWSET function, BULK INSERT
- bulk importing [SQL Server], security
- bulk rowset providers [SQL Server]
- bulk exporting [SQL Server], BULK INSERT statement
- remote data access [SQL Server], bulk importing
- bulk importing [SQL Server], BULK INSERT statement
- Transact-SQL bulk export/import operations
ms.assetid: 18a64236-0285-46ea-8929-6ee9bcc020b9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e8b09ee01da2dde8e8bf50fbda21c1c8bca1689d
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66011934"
---
# <a name="import-bulk-data-by-using-bulk-insert-or-openrowsetbulk-sql-server"></a>Importer des données en bloc à l’aide de BULK INSERT ou OPENROWSET(BULK...) (SQL Server)
  Cette rubrique fournit une vue d'ensemble de l'utilisation de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] BULK INSERT et de l'instruction INSERT...SELECT * FROM OPENROWSET(BULK...) destinées à l'importation en bloc de données à partir d'un fichier de données dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cette rubrique décrit aussi des règles de sécurité relatives à l’utilisation de BULK INSERT et OPENROWSET(BULK...), et l’utilisation de ces méthodes pour l’importation en bloc à partir d’une source de données distante.  
  
> [!NOTE]  
>  Quand vous utilisez BULK INSERT ou OPENROWSET(BULK...), il est important de comprendre la manière dont la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gère l’emprunt d’identité. Pour plus d'informations, consultez « Considérations sur la sécurité» plus loin dans cette rubrique.  
  
## <a name="bulk-insert-statement"></a>Instruction BULK INSERT  
 BULK INSERT charge les données d'un fichier de données dans une table. Cette fonctionnalité est similaire à celle fournie par l’option **in** de la commande **bcp** , mais le fichier de données est lu par le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour obtenir une description de la syntaxe BULK INSERT, consultez [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
### <a name="examples"></a>Exemples  
 Pour des exemples BULK INSERT, consultez :  
  
-   [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
-   [Exemples d’importation et d’exportation en bloc de documents XML &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Conserver des valeurs d’identité lors de l’importation de données en bloc &#40;SQL Server&#41;](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Conserver les valeurs NULL ou utiliser la valeur par défaut lors de l’importation en bloc &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)  
  
-   [Utiliser un fichier de format pour importer des données en bloc &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Utiliser le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif pour importer ou exporter des données &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser un fichier de format pour ignorer une colonne de table &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Utiliser un fichier de format pour mapper les colonnes d’une table sur les champs d’un fichier de données &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="openrowsetbulk-function"></a>OPENROWSET(BULK...) Fonction  
 Le fournisseur d'ensembles de lignes en bloc OPENROWSET est accessible en appelant la fonction OPENROWSET et en spécifiant l'option BULK. La fonction OPENROWSET(BULK...) vous permet d’accéder aux données distantes en vous connectant à une source de données distante (un fichier de données) par l’intermédiaire d’un fournisseur OLE DB.  
  
 Pour importer en bloc des données, appelez OPENROWSET(BULK...) à partir d’une clause SELECT...FROM dans une instruction INSERT. La syntaxe de base pour l'importation en bloc de données est la suivante :  
  
 INSERT ... SELECT * FROM OPENROWSET(BULK...)  
  
 Lorsqu'elle apparaît dans une instruction INSERT, OPENROWSET(BULK...) prend en charge les indicateurs de table. En plus des indicateurs de table standard, comme TABLOCK, la clause BULK peut accepter les indicateurs de table spécialisés suivants : IGNORE_CONSTRAINTS (ignore uniquement les contraintes CHECK), IGNORE_TRIGGERS, KEEPDEFAULTS et KEEPIDENTITY. Pour plus d’informations, consultez [Indicateurs de table &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).  
  
 Pour plus d’informations sur les autres utilisations de l’option BULK, consultez [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
### <a name="examples"></a>Exemples  
 Pour des exemples d'instructions INSERT...SELECT * FROM OPENROWSET(BULK...), consultez les rubriques suivantes :  
  
-   [Exemples d’importation et d’exportation en bloc de documents XML &#40;SQL Server&#41;](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Conserver des valeurs d’identité lors de l’importation de données en bloc &#40;SQL Server&#41;](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Conserver les valeurs NULL ou utiliser la valeur par défaut lors de l’importation en bloc &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Utiliser un fichier de format pour importer des données en bloc &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Utiliser le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser un fichier de format pour ignorer une colonne de table &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Utiliser un fichier de format pour ignorer un champ de données &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Utiliser un fichier de format pour mapper les colonnes d’une table sur les champs d’un fichier de données &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="security-considerations"></a>Considérations relatives à la sécurité  
 Si un utilisateur a recours à une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le profil de sécurité du compte du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est alors utilisé. Une connexion via l'authentification SQL Server ne peut pas être authentifiée en dehors du moteur de base de données. Par conséquence, lorsqu'une commande BULK INSERT est initiée par une connexion via l'authentification SQL Server, la connexion aux données s'effectue à l'aide du contexte de sécurité du compte du processus SQL Server (compte utilisé par le service de moteur de base de données SQL Server). Pour pouvoir lire les données sources, vous devez octroyer au compte utilisé par le moteur de base de données SQL Server l'accès aux données sources. Par opposition, si un utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'est connecté via l'authentification Windows, il peut lire uniquement les fichiers accessibles par le compte d'utilisateur, indépendamment du profil de sécurité du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Prenons l'exemple d'un utilisateur qui s'est connecté à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de l'authentification Windows. Pour que cet utilisateur puisse utiliser BULK INSERT ou OPENROWSET en vue d'importer les données d'un fichier dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le compte d'utilisateur nécessite des droits d'accès en lecture au fichier de données. En bénéficiant de droits accès au fichier de données, l'utilisateur peut importer les données du fichier dans une table même si le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas l'autorisation d'accéder au fichier. L'utilisateur n'est pas obligé d'accorder au processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une autorisation d'accès au fichier.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows peuvent être configurés afin de permettre à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de se connecter à une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en transmettant les informations d'un utilisateur Windows authentifié. Ce procédé est appelé *emprunt d'identité* ou *délégation*. Il importe de comprendre comment la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gère les aspects de sécurité en matière d'emprunt d'identité lorsque vous utilisez l'instruction BULK INSERT ou OPENROWSET. L'emprunt d'identité permet au fichier de données de résider sur un ordinateur différent du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l'utilisateur. Par exemple, si un utilisateur sur **Ordinateur_A** a accès à un fichier de données sur **Ordinateur_B**, et que la délégation des informations d’identification a été correctement définie, l’utilisateur peut se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécutant sur **Ordinateur_C**, accéder au fichier de données sur **Ordinateur_B**, et importer les données en bloc de ce fichier dans une table résidant sur **Ordinateur_C**.  
  
## <a name="bulk-importing-from-a-remote-data-file"></a>Importation en bloc à partir d'un fichier de données distant  
 Pour utiliser BULK INSERT ou INSERT...SELECT \* FROM OPENROWSET(BULK...) pour effectuer l’importation en bloc de données à partir d’un autre ordinateur, le fichier de données doit être partagé entre les deux ordinateurs. Pour spécifier un fichier de données partagé, utilisez son nom UNC (Universal Naming Convention), dont le format général est **\\\\**_nom_serveur_**\\**_nom_partage_**\\**_chemin_**\\**_nom_fichier_. En outre, le compte utilisé pour accéder au fichier de données doit avoir reçu les autorisations requises pour lire le fichier sur le disque distant.  
  
 Par exemple, l'instruction `BULK INSERT` ci-dessous importe en bloc des données dans la table `SalesOrderDetail` de la base de données `AdventureWorks` à partir d'un fichier de données nommé `newdata.txt`. Ce fichier de données réside dans un dossier partagé nommé `\dailyorders`, dans un répertoire partagé du réseau nommé `salesforce`, sur un système nommé `computer2`.  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM '\\computer2\salesforce\dailyorders\neworders.txt';  
GO  
```  
  
> [!NOTE]  
>  Cette restriction ne s’applique pas à l’utilitaire **bcp**, car le fichier est lu par le client indépendamment de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)   
 [Clause SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql)   
 [Importation et exportation en bloc de données &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)   
 [FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql)   
 [Utilitaire bcp](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
  
