---
title: Exécution d’opérations de copie en bloc | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [SQL Server Native Client]
- data access [SQL Server Native Client], bulk copy operations
- SQL Server Native Client, bulk copy operations
- SQLNCLI, bulk copy operations
ms.assetid: 50d8456b-e6a1-4b25-bc7e-56946ed654a7
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b4ba6b0f278c872dc8ae3dde6967f385c39880fa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68016642"
---
# <a name="performing-bulk-copy-operations"></a>Exécution d'opérations de copie en bloc
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  La fonction de copie en bloc de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge le transfert de quantités importantes de données vers ou depuis une table ou une vue [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les données peuvent également être transférées en spécifiant une instruction SELECT. Les données peuvent être déplacées entre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et un fichier de données du système d'exploitation, par exemple un fichier ASCII. Le fichier de données peut avoir différents formats ; le format est défini pour effectuer la copie en bloc dans un fichier de format. Facultativement, les données peuvent être chargées dans des variables de programme et transférées vers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide de fonctions et de méthodes de copie en bloc.  
  
 Pour un exemple d’application qui illustre cette fonctionnalité, consultez [en bloc copie de données en bloc avec IRowsetFastLoad &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md).  
  
 Une application utilise en général la copie en bloc de l'une des manières suivantes :  
  
-   Effectuer une copie en bloc à partir d'une table, d'une vue ou du jeu de résultats d'une instruction Transact-SQL dans un fichier de données où les données sont stockées dans le même format que la table ou la vue.  
  
     On parle de « fichier de données en mode natif ».  
  
-   Effectuer une copie en bloc à partir d'une table, d'une vue ou du jeu de résultats d'une instruction Transact-SQL dans un fichier de données où les données sont stockées dans un format différent de celui de la table ou de la vue.  
  
     Dans ce cas, un fichier de format séparé est créé qui définit les caractéristiques (type de données, position, longueur, terminateur, etc.) de chaque colonne à mesure que les colonnes sont stockées dans le fichier de données. Si toutes les colonnes sont converties en format caractère, le fichier résultant est appelé un « fichier de données en mode caractère ».  
  
-   Effectuer une copie en bloc à partir d'un fichier de données dans une table ou une vue.  
  
     Si nécessaire, un fichier de format est utilisé pour déterminer la structure du fichier de données.  
  
-   Charger des données dans des variables de programme, puis importer les données dans une table ou une vue à l'aide des fonctions de copie en bloc pour effectuer la copie en bloc dans une ligne à la fois.  
  
 Il n'est pas nécessaire que les fichiers de données utilisés par les fonctions de copie en bloc soient créés par un autre programme de copie en bloc. Tout autre système peut générer un fichier de données et un fichier de format conformément aux définitions de la copie en bloc ; ces fichiers peuvent ensuite être utilisés avec un programme de copie en bloc [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour importer des données dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Par exemple, vous pouvez exporter des données à partir d'une feuille de calcul dans un fichier délimité par des tabulations, générer un fichier de format décrivant le fichier délimité par des tabulations, puis utilisez un programme de copie en bloc pour importer rapidement les données dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les fichiers de données générés par la copie en bloc peuvent également être importés dans d'autres applications. Par exemple, vous pouvez utiliser des fonctions de copie en bloc pour exporter les données d'une table ou d'une vue dans un fichier délimité par des tabulations que vous pouvez ensuite charger dans une feuille de calcul.  
  
 Les programmeurs qui codent des applications pour utiliser les fonctions de copie en bloc doivent respecter les règles générales pour obtenir de bonnes performances en matière de copie en bloc. Pour plus d’informations sur la prise en charge des opérations de copie en bloc dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consultez [importation et exportation de données &#40;SQL Server&#41;](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Un type CLR défini par l'utilisateur (UDT) doit être lié en tant que données binaires. Même si un fichier de format spécifie SQLCHAR en tant que type de données pour une colonne UDT cible, l'utilitaire BCP traite les données en tant que données binaires.  
  
 N'utilisez pas SET FMTONLY OFF avec des opérations de copie en bloc. SET FMTONLY OFF peut entraîner l'échec de votre opération de copie en bloc ou générer des résultats inattendus.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Fournisseur OLE DB SQL Server Native Client  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client implémente deux méthodes pour effectuer des opérations de copie en bloc avec un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] base de données. La première méthode implique l’utilisation de l’interface [IRowsetFastLoad](../../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) pour les opérations de copie en bloc basées sur la mémoire, tandis que la seconde implique l’utilisation de l’interface [IBCPSession](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md) pour les opérations de copie en bloc basées sur le fichier.  
  
### <a name="using-memory-based-bulk-copy-operations"></a>Utilisation d'opérations de copie en bloc basées sur la mémoire  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur implémente la **IRowsetFastLoad** interface à exposer la prise en charge de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les opérations de copie en bloc basées sur la mémoire. L’interface **IRowsetFastLoad** implémente les méthodes [IRowsetFastLoad::Commit](../../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-commit-ole-db.md) et [IRowsetFastLoad::InsertRow](../../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-insertrow-ole-db.md).  
  
#### <a name="enabling-a-session-for-irowsetfastload"></a>Activation d'une session pour IRowsetFastLoad  
 Le consommateur notifie le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client de son besoin en matière de copie en bloc en attribuant la valeur VARIANT_TRUE à la propriété SSPROP_ENABLEFASTLOAD de la source de données spécifique au fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Lorsque la propriété est définie sur la source de données, le consommateur crée une session du fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. La nouvelle session permet au consommateur d’accéder à l’interface **IRowsetFastLoad**.  
  
> [!NOTE]  
>  Si l’interface **IDataInitialize** est utilisée pour initialiser la source de données, vous devez définir la propriété SSPROP_IRowsetFastLoad dans le paramètre *rgPropertySets* de la méthode **IOpenRowset::OpenRowset** ; sinon, l’appel à la méthode **OpenRowset** retourne E_NOINTERFACE.  
  
 L'activation d'une session pour la copie en bloc limite la prise en charge du fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client aux interfaces sur la session. Une session compatible avec la copie en bloc expose uniquement les interfaces suivantes :  
  
-   **IDBSchemaRowset**  
  
-   **IGetDataSource**  
  
-   **IOpenRowset**  
  
-   **ISupportErrorInfo**  
  
-   **ITransactionJoin**  
  
 Pour désactiver la création d'ensembles de lignes compatibles avec la copie en bloc et forcer la session du fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à rétablir le traitement standard, attribuez la valeur VARIANT_FALSE à SSPROP_ENABLEFASTLOAD.  
  
#### <a name="irowsetfastload-rowsets"></a>Ensembles de lignes IRowsetFastLoad  
 Les ensembles de lignes de copie en bloc du fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client sont en écriture seule, mais ils exposent des interfaces qui permettent au consommateur de déterminer la structure d'une table [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les interfaces suivantes sont exposées sur un ensemble de lignes du fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client compatible avec la copie en bloc :  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
-   **IColumnsRowset**  
  
-   **IConvertType**  
  
-   **IRowsetFastLoad**  
  
-   **IRowsetInfo**  
  
-   **ISupportErrorInfo**  
  
 Les propriétés spécifiques au fournisseur SSPROP_FASTLOADOPTIONS, SSPROP_FASTLOADKEEPNULLS et SSPROP_FASTLOADKEEPIDENTITY contrôle les comportements d'un ensemble de lignes de copie en bloc du fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Les propriétés sont spécifiées dans le *rgProperties* membre d’un _rgPropertySets_**IOpenRowset**membre de paramètre.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_FASTLOADKEEPIDENTITY|Colonne : Non<br /><br /> R/W : en lecture/écriture<br /><br /> Tapez : VT_BOOL<br /><br /> Par défaut : VARIANT_FALSE<br /><br /> Description : Conserve les valeurs d’identité fournies par le consommateur.<br /><br /> VARIANT_FALSE : Valeurs pour une colonne d’identité dans le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table sont générées par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Toute valeur liée pour la colonne est ignorée par le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif.<br /><br /> VARIANT_TRUE : Le consommateur lie un accesseur qui fournit une valeur pour un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] colonne d’identité. La propriété d’identité n’étant pas disponible sur les colonnes qui acceptent Null, le consommateur fournit une valeur unique sur chaque appel de **IRowsetFastLoad::Insert**.|  
|SSPROP_FASTLOADKEEPNULLS|Colonne : Non<br /><br /> R/W : en lecture/écriture<br /><br /> Tapez : VT_BOOL<br /><br /> Par défaut : VARIANT_FALSE<br /><br /> Description : Maintient la valeur NULL pour les colonnes avec une contrainte par défaut. Affecte uniquement les colonnes [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui acceptent NULL et auxquelles une contrainte DEFAULT est appliquée.<br /><br /> VARIANT_FALSE : [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] insère la valeur par défaut pour la colonne lorsque le consommateur du fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client insère une ligne contenant NULL pour la colonne.<br /><br /> VARIANT_TRUE : [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] insère NULL pour la valeur de colonne lorsque le consommateur du fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client insère une ligne contenant NULL pour la colonne.|  
|SSPROP_FASTLOADOPTIONS|Colonne : Non<br /><br /> R/W : en lecture/écriture<br /><br /> Tapez : VT_BSTR<br /><br /> Valeur par défaut : aucune<br /><br /> Description : Cette propriété est identique à la **-h** »*indicateur*[,... *n*] « option de le **bcp** utilitaire. La ou les chaînes suivantes peuvent être utilisées en tant qu'options pour la copie en bloc de données dans une table.<br /><br /> **ORDER**(*column*[**ASC** &#124; **DESC**][,...*n*]): Ordre de tri des données dans le fichier de données. Les performances de la copie en bloc peuvent être améliorées si le fichier de données à charger est trié conformément à l'index cluster de la table.<br /><br /> **ROWS_PER_BATCH** = *bb*: Nombre de lignes de données par lot ( *bb*). Le serveur optimise le chargement en masse en fonction de la valeur de *bb*. Par défaut, **ROWS_PER_BATCH** est inconnu.<br /><br /> **KILOBYTES_PER_BATCH** = *cc*: Nombre de kilo-octets (Ko) de données par lot (cc). Par défaut, **KILOBYTES_PER_BATCH** est inconnu.<br /><br /> **TABLOCK**: Un verrou de niveau table est acquis pour la durée de l’opération de copie en bloc. Cette option augmente sensiblement les performances car le maintien d'un verrou uniquement pour la durée de la seule opération de copie en bloc réduit la contention de verrou sur la table. Une table peut être chargée simultanément par plusieurs clients si elle ne comporte pas d’index et si **TABLOCK** est spécifié. Par défaut, le comportement de verrouillage est déterminé par l’option de table **table lock on bulk load**.<br /><br /> **CHECK_CONSTRAINTS**: Toutes les contraintes sur *table_name* sont vérifiées pendant l’opération de copie en bloc. Par défaut, les contraintes sont ignorées.<br /><br /> **FIRE_TRIGGER** : [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise le contrôle de version de ligne pour les déclencheurs et stocke les versions des lignes dans le magasin de versions de la base de données **tempdb**. Par conséquent, les optimisations de journalisation en bloc sont disponibles même lorsque les déclencheurs sont activés. Avant de procéder à l’importation en bloc d’un lot comptant un nombre important de lignes avec les déclencheurs activés, vous devrez peut-être augmenter la taille de **tempdb**.|  
  
### <a name="using-file-based-bulk-copy-operations"></a>Utilisation d'opérations de copie en bloc basées sur le fichier  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur implémente la **IBCPSession** interface à exposer la prise en charge de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les opérations de copie en bloc basées sur le fichier. L’interface **IBCPSession** implémente les méthodes [IBCPSession::BCPColFmt](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md), [IBCPSession::BCPColumns](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md), [IBCPSession::BCPControl](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md), [IBCPSession::BCPDone](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md), [IBCPSession::BCPExec](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md), [IBCPSession::BCPInit](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md), [IBCPSession::BCPReadFmt](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md) et [IBCPSession::BCPWriteFmt](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>Pilote ODBC SQL Server Native Client  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client maintient la même prise en charge pour les opérations de copie en bloc qui faisaient partie des versions précédentes du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour plus d’informations sur les opérations de copie en bloc à l’aide de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client, consultez [effectuant des opérations de copie en bloc &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [Propriétés de la source de données &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)   
 [Importation et exportation en bloc de données &#40;SQL Server&#41;](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [IRowsetFastLoad &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)   
 [IBCPSession &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Optimisation des performances de l’importation en bloc](https://msdn.microsoft.com/library/ms190421\(SQL.105\).aspx)  
  
  
