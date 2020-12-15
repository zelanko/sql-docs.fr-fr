---
title: SQL Server le modèle d’objet de chargement en masse XML (SQLXML)
description: En savoir plus sur les méthodes et les propriétés de l’objet SQLXMLBulkLoad utilisé pour le chargement en masse XML dans SQLXML 4,0.
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], object model
- ErrorLogFile property
- SGDropTables property
- SGUseID property
- KeepNulls property
- ConnectionCommand property
- SchemaGen property
- XMLFragment property
- SQLXMLBulkLoad object
- ForceTableLock property
- CheckConstraints property
- BulkLoad property
- TempFilePath property
- IgnoreDuplicateKeys property
- Transaction property
- KeepIdentity property
- ConnectionString property
- FireTriggers property
- Execute method
- XML Bulk Load [SQLXML], object model
ms.assetid: a9efbbde-ed2b-4929-acc1-261acaaed19d
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: bc5414ba64ec7a801cf279a4735a2f8e85cd3731
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97461730"
---
# <a name="sql-server-xml-bulk-load-object-model-sqlxml-40"></a>Modèle objet de chargement en masse XML de SQL Server (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] modèle objet de chargement en masse XML de Microsoft se compose de l’objet SQLXMLBulkLoad. Cet objet prend en charge les méthodes et les propriétés suivantes.  
  
## <a name="methods"></a>Méthodes  
 Execute  
 Procède au chargement en masse des données à l'aide du fichier de schéma et du fichier de données (ou flux) fournis en guise de paramètres.  
  
## <a name="properties"></a>Propriétés  
 BulkLoad  
 Spécifie si un chargement en masse doit avoir lieu. Cette propriété est utile si vous souhaitez générer uniquement les schémas (voir les propriétés SchemaGen, SGDropTables et SGUseID qui suivent) et ne pas effectuer de chargement en masse. Il s'agit d'une propriété booléenne. Lorsque la propriété est définie sur TRUE, le processus de chargement en masse XML s'exécute. Lorsqu'elle est définie sur FALSE, aucun processus de chargement en masse XML n'a lieu.  
  
 La valeur par défaut est TRUE.  
  
 CheckConstraints  
 Spécifie si les contraintes (telles que les contraintes découlant de la relation entre clé primaire et clé étrangère dans les colonnes) spécifiées sur la colonne doivent être vérifiées lorsque le chargement en masse XML insère des données dans les colonnes. Il s'agit d'une propriété booléenne.  
  
 Lorsque la propriété est définie sur TRUE, le chargement en masse XML recherche chaque valeur insérée dans les contraintes (ce qui signifie qu'une violation de contrainte entraîne une erreur).  
  
> [!NOTE]  
>  Pour conserver la valeur FALSe pour cette propriété, vous devez disposer des autorisations **ALTER TABLE** sur les tables cibles. Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md).  
  
 La valeur par défaut est FALSE. Lorsqu'il est défini sur FALSE, le chargement en masse XML ignore les contraintes au cours d'une opération d'insertion. Dans l'implémentation actuelle, vous devez définir les tables dans l'ordre des relations entre clés primaires et clés étrangères dans le schéma de mappage. Autrement dit, une table dotée d'une clé primaire doit être définie avant la table avec clé étrangère correspondante sans quoi le chargement en masse XML se soldera par un échec.  
  
 Notez que si vous procédez à une propagation d'identité, cette option ne s'applique pas et la vérification des contraintes restera activée. Ceci se produit lorsque `KeepIdentity=False` et qu'il existe une relation où le parent est un champ d'identité et la valeur est attribuée à l'enfant telle qu'elle est générée.  
  
 ConnectionCommand  
 Identifie un objet de connexion existant (par exemple, l’objet de commande ADO ou ICommand) que le chargement en masse XML doit utiliser. Vous pouvez utiliser la propriété ConnectionCommand au lieu de spécifier une chaîne de connexion avec la propriété ConnectionString. La propriété transaction doit avoir la valeur TRUE si vous utilisez ConnectionCommand.  
  
 Si vous utilisez à la fois les propriétés ConnectionString et ConnectionCommand, le chargement en masse XML utilise la dernière propriété spécifiée.  
  
 La valeur par défaut est NULL.  
  
 ConnectionString  
 Identifie la chaîne de connexion OLE DB qui fournit les informations nécessaires pour établir une connexion à une instance de la base de données. Si vous utilisez à la fois les propriétés ConnectionString et ConnectionCommand, le chargement en masse XML utilise la dernière propriété spécifiée.  
  
 La valeur par défaut est NULL.  
  
 ErrorLogFile  
 Spécifie le nom de fichier dans lequel le chargement en masse XML enregistre des erreurs et des messages. La valeur par défaut est une chaîne vide, auquel cas aucun enregistrement n'a lieu.  
  
 FireTriggers  
 Spécifie si les déclencheurs définis dans les tables cibles doivent être déclenchés pendant l'opération de chargement en masse. La valeur par défaut est FALSE.  
  
 Si la valeur est TRUE, les déclencheurs seront activés comme d'habitude lors des opérations d'insertion.  
  
> [!NOTE]  
>  Pour conserver la valeur FALSe pour cette propriété, vous devez disposer des autorisations **ALTER TABLE** sur les tables cibles. Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md).  
  
 Notez que si vous ne procédez à aucune propagation d'identité, cette option ne s'applique pas et les déclencheurs resteront activés. Ceci se produit lorsque `KeepIdentity=False` et qu'il existe une relation où le parent est un champ d'identité et la valeur est attribuée à l'enfant telle qu'elle est générée.  
  
 ForceTableLock  
 Spécifie si les tables dans lesquelles le chargement en masse XML copie des données doivent être verrouillées pour la durée du chargement en masse. Il s'agit d'une propriété booléenne. Lorsque la propriété est définie sur TRUE, le chargement en masse XML acquiert des verrous de table pendant toute la durée du chargement en masse. Si elle est définie sur FALSE, le chargement en masse XML acquiert un verrou de table chaque fois qu'il insère un enregistrement dans une table.  
  
 La valeur par défaut est FALSE.  
  
 IgnoreDuplicateKeys  
 Spécifie la démarche à suivre en cas de tentative d'insertion de valeurs dupliquées dans une colonne clé. Si cette propriété est définie sur TRUE et si une tentative d'insertion d'un enregistrement avec valeur dupliquée dans une colonne clé a lieu, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] n'insère pas cet enregistrement. En revanche, il insère l'enregistrement suivant ; l'opération de chargement en masse ne peut donc pas aboutir à un échec. Si cette propriété est définie sur FALSE, le chargement en masse échoue dès qu'une tentative d'insertion d'une valeur dupliquée dans une colonne clé a lieu.  
  
 Lorsque la propriété IgnoreDuplicateKeys est définie sur TRUE, une instruction COMMIT est émise pour chaque enregistrement inséré dans la table. ce qui ralentit les performances. La propriété peut avoir la valeur TRUE uniquement lorsque la propriété transaction a la valeur FALSe, car le comportement transactionnel est implémenté à l’aide de fichiers.  
  
 La valeur par défaut est FALSE.  
  
 KeepIdentity  
 Spécifie comment traiter les valeurs pour une colonne de type d'identité dans le fichier source. Il s'agit d'une propriété booléenne. Lorsque la propriété est définie sur TRUE, le chargement en masse XML affecte les valeurs spécifiées dans le fichier source à la colonne d'identité. Lorsque la propriété est définie sur FALSE, l'opération de chargement en masse ignore les valeurs de la colonne d'identité spécifiées dans la source. Dans ce cas, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] affecte une valeur à la colonne d'identité.  
  
 Si le chargement en masse implique une colonne désignant une clé étrangère qui fait référence à une colonne d'identité dans laquelle les valeurs générées par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sont stockées, le chargement en masse propage comme il se doit ces valeurs d'identité dans la colonne de clé étrangère.  
  
 La valeur de cette propriété s'applique à toutes les colonnes qui interviennent dans le chargement en masse. La valeur par défaut est TRUE.  
  
> [!NOTE]  
>  Pour conserver la valeur TRUE pour cette propriété, vous devez disposer des autorisations **ALTER TABLE** sur les tables cibles. Sinon, vous devez lui attribuer la valeur FALSE. Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md).  
  
 KeepNulls  
 Spécifie la valeur à utiliser pour une colonne pour laquelle un attribut ou un élément enfant correspondant est manquant dans le document XML. Il s'agit d'une propriété booléenne. Lorsque la propriété est définie sur TRUE, le chargement en masse XML affecte une valeur NULL à la colonne. Il n'affecte pas la valeur par défaut de la colonne (le cas échéant) telle que définie sur le serveur. La valeur de cette propriété s'applique à toutes les colonnes qui interviennent dans le chargement en masse.  
  
 La valeur par défaut est FALSE.  
  
 SchemaGen  
 Spécifie si les tables requises doivent être créées avant une opération de chargement en masse. Il s'agit d'une propriété booléenne. Si cette propriété est définie sur TRUE, les tables identifiées dans le schéma de mappage sont créées (la base de données doit exister). Si une ou plusieurs tables existent déjà dans la base de données, la propriété SGDropTables détermine si ces tables préexistantes doivent être supprimées et recréées.  
  
 La valeur par défaut de la propriété SchemaGen est FALSe. SchemaGen ne crée pas de contraintes de clé primaire sur les tables nouvellement créées. Toutefois, SchemaGen crée des contraintes de clé étrangère dans la base de données s’il peut trouver des annotations **SQL : relation** et **SQL : key-fields** correspondantes dans le schéma de mappage et si le champ clé se compose d’une seule colonne.  
  
 Notez que si vous définissez la propriété SchemaGen sur TRUE, le chargement en masse XML effectue les opérations suivantes :  
  
-   Il crée les tables nécessaires à partir des noms d'élément et d'attribut. C'est pourquoi il est primordial que vous n'utilisiez pas de mots réservés [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour les noms d'élément et d'attribut dans le schéma.  
  
-   Retourne des données de dépassement pour toute colonne désignée à l’aide de [SQL : overflow-field](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md) au format de [type de données XML](../../../t-sql/xml/xml-transact-sql.md) .  
  
 SGDropTables  
 Spécifie si les tables existantes doivent être supprimées et recréées. Vous utilisez cette propriété lorsque la propriété SchemaGen est définie sur TRUE. Si SGDropTables a la valeur FALSe, les tables existantes sont conservées. Les tables existantes sont supprimées et recréées lorsque cette propriété a la valeur TRUE.  
  
 La valeur par défaut est FALSE.  
  
 SGUseID  
 Spécifie si l’attribut dans le schéma de mappage identifié comme type d' **ID** peut être utilisé lors de la création d’une contrainte de clé primaire lors de la création de la table. Utilisez cette propriété lorsque la propriété SchemaGen est définie sur TRUE. Si SGUseID a la valeur TRUE, l’utilitaire SchemaGen utilise un attribut pour lequel **DT : type = « ID »** est spécifié en tant que colonne de clé primaire et ajoute la contrainte de clé primaire appropriée lors de la création de la table.  
  
 La valeur par défaut est FALSE.  
  
 TempFilePath  
 Spécifie le chemin d'accès où le chargement en masse XML crée les fichiers temporaires pour un chargement en masse transactionnel. (Cette propriété est utile uniquement lorsque la propriété transaction a la valeur TRUE.) Vous devez vous assurer que le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] compte utilisé pour le chargement en masse XML a accès à ce chemin d’accès. Si cette propriété n'est pas définie, le chargement en masse XML stocke les fichiers temporaires à l'emplacement spécifié dans la variable d'environnement TEMP.  
  
 Transaction  
 Spécifie si le chargement en masse doit avoir lieu sous la forme d'une transaction, auquel cas la restauration est garantie si le chargement en masse échoue. Il s'agit d'une propriété booléenne. Si la propriété est définie sur TRUE, le chargement en masse intervient dans un contexte transactionnel. La propriété TempFilePath est utile uniquement lorsque transaction a la valeur TRUE.  
  
> [!NOTE]  
>  Si vous chargez des données binaires (telles que les types de données XML bin. Hex, bin. Base64 dans les types de données binaires image [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ), la propriété transaction doit avoir la valeur false.  
  
 La valeur par défaut est FALSE.  
  
 XMLFragment  
 Spécifie si les données source sont un fragment XML. Un fragment XML est un document XML sans élément unique de niveau supérieur (racine). Il s'agit d'une propriété booléenne. Cette propriété doit être définie sur TRUE si le fichier source consiste en un fragment XML.  
  
 La valeur par défaut est FALSE.  
  
  
