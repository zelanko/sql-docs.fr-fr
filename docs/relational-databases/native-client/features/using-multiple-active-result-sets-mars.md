---
title: Utilisation de MARS (Multiple Active Result Sets) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, MARS
- SQLNCLI, MARS
- data access [SQL Server Native Client], MARS
- Multiple Active Result Sets
- SQL Server Native Client, MARS
- MARS [SQL Server]
- SQL Server Native Client ODBC driver, MARS
ms.assetid: ecfd9c6b-7d29-41d8-af2e-89d7fb9a1d83
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fdf953bd5cb1835b2d2f6cc0e868a3687e53e852
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303200"
---
# <a name="using-multiple-active-result-sets-mars"></a>Utilisation de MARS (Multiple Active Result Sets)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] a introduit la prise en charge de MARS (Multiple Active Result Sets) dans les applications accédant au [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], les applications de base de données ne pouvaient pas gérer plusieurs instructions actives sur une connexion. Lors de l'utilisation de jeux de résultats [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] par défaut, l'application devait traiter ou annuler tous les jeux de résultats d'un lot avant de pouvoir exécuter tout autre lot sur cette connexion. Un nouvel attribut de connexion a été introduit dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] de manière à ce que les applications puissent gérer plus d'une demande en attente par connexion et, plus spécifiquement, pour qu'elles puissent avoir plus d'un jeu de résultats par défaut actif par connexion.  
  
 MARS simplifie la conception d'applications grâce aux nouvelles fonctionnalités suivantes :  
  
-   Les applications peuvent avoir plusieurs jeux de résultats par défaut ouverts et entrelacer leur lecture.  
  
-   Les applications peuvent exécuter d'autres instructions (par exemple, INSERT, UPDATE, DELETE et des appels de procédure stockée) pendant que les jeux de résultats par défaut sont ouverts.  
  
 Voici quelques recommandations pour les applications utilisant MARS :  
  
-   Les jeux de résultats par défaut doivent être utilisés pour des jeux de résultats à courte durée de vie ou des jeux de résultats de petites taille générés par des instructions SQL uniques (SELECT, DML avec OUTPUT, RECEIVE, READ TEXT, etc.).  
  
-   Des curseurs côté serveur doivent être utilisés pour des jeux de résultats à plus longue durée de vie ou des jeux de résultats de grande taille générés par des instructions SQL uniques.  
  
-   Lisez systématiquement les résultats dans leur intégralité afin de savoir s'ils contiennent des demandes de procédure ou des traitements qui renvoient des résultats multiples.  
  
-   Si possible, utilisez des appels d'API pour modifier les propriétés de connexion et gérez les transactions plutôt que les instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
-   Dans MARS, l'emprunt d'identité à l'échelle de la session est interdit lorsque des traitements simultanés sont en cours d'exécution.  

> [!NOTE]
> Par défaut, la fonctionnalité MARS n’est pas activée par le pilote. Pour utiliser MARS lors [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de la connexion avec Native Client, vous devez activer SPÉCIFIQUEMENT MARS dans une chaîne de connexion. Toutefois, certaines applications peuvent activer MARS par défaut, si l’application détecte que le conducteur prend en charge MARS. Pour ces applications, vous pouvez désactiver MARS dans la chaîne de connexion au besoin. Pour plus d'informations, consultez les sections relatives au fournisseur OLE DB de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et au pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, plus loin dans cette rubrique.

 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ne limite pas le nombre d'instructions actives sur une connexion.  
  
 Les applications typiques qui n’ont pas besoin d’avoir plus d’un seul lot multi-relevés ou une procédure stockée exécutant en même temps bénéficieront de MARS sans avoir à comprendre comment MARS est implémenté. Toutefois, les applications ayant des exigences plus complexes doivent prendre ceci compte.  
  
 MARS permet l'exécution entrelacée de plusieurs demandes au sein d'une connexion unique. Autrement dit, il permet à un traitement de s'exécuter, et au sein de cette exécution, il permet à d'autres demandes de s'exécuter. Notez toutefois que MARS est défini en terme d'entrelacement et non en terme d'exécution parallèle.  
  
 L'infrastructure de MARS permet l'exécution entrelacée de plusieurs traitements, mais l'exécution ne peut être basculée qu'à des points bien définis. Par ailleurs, la plupart des instructions doivent s'exécuter atomiquement au sein d'un lot. Les déclarations qui renvoient les lignes au client, qui sont parfois appelées *points de rendement,* sont autorisées à interlendre l’exécution avant l’achèvement pendant que des rangées sont envoyées au client, par exemple :  
  
-   SELECT  
  
-   FETCH  
  
-   RECEIVE  
  
 Toute autre instruction exécutée dans le cadre d'une procédure stockée ou d'un traitement doit s'exécuter jusqu'à la fin pour que l'exécution puisse être basculée sur d'autres demandes MARS.  
  
 La manière exacte dont les lots entrelacent l'exécution dépend de plusieurs facteurs et il est difficile de prédire la séquence exacte dans laquelle les commandes de plusieurs traitements qui contiennent des points d'interruption seront exécutées. Soyez prudent afin d'éviter des effets secondaires non désirés liés à l'exécution entrelacée de traitements complexes de cet type.  
  
 Évitez des problèmes en utilisant des appels d'API plutôt que des instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] pour gérer l'état de la connexion (SET, USE) et les transactions (BEGIN TRAN, COMMIT, ROLLBACK) en n'incluant pas ces instructions dans des traitements à instructions multiples qui contiennent également des points d'interruption, et en sérialisant l'exécution de tels traitements par la consommation ou l'annulation de tous les résultats.  
  
> [!NOTE]  
>  Un traitement ou une procédure stockée qui démarre une transaction manuelle ou implicite lorsque MARS est activé doit terminer la transaction avant que le traitement ne quitte. S'il ne le fait pas, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] restaure toutes les modifications apportées par la transaction lorsque le traitement se termine. Une telle transaction est gérée par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en tant que transaction dont l'étendue est définie par traitement. Il s'agit d'un nouveau type de transaction introduit dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] pour permettre aux procédures stockées valides existantes d'être utilisées lorsque MARS est activé. Pour plus d’informations sur les transactions dont l’étendue est définie par lot, consultez [Instructions de transaction &#40;Transact-SQL&#41;](~/t-sql/statements/statements.md).  
  
 Par exemple d’utiliser MARS à partir d’ADO, voir [Utiliser ADO avec SQL Server Native Client](../../../relational-databases/native-client/applications/using-ado-with-sql-server-native-client.md).  
  
## <a name="in-memory-oltp"></a>OLTP en mémoire  
 L’OLTP en mémoire prend en charge MARS à l’aide de requêtes et de procédures stockées compilées en mode natif. MARS permet de demander des données à partir de plusieurs requêtes sans avoir à récupérer complètement chaque jeu de résultats avant d’envoyer une demande d’extraction de lignes depuis un nouveau jeu de résultats. Pour lire avec succès à partir de plusieurs ensembles de résultats ouverts, vous devez utiliser une connexion compatible MARS.  
  
 MARS est désactivé par défaut ; vous devez donc l’activer explicitement en ajoutant `MultipleActiveResultSets=True` à une chaîne de connexion. L’exemple suivant montre comment se connecter à une instance SQL Server et spécifier que MARS est activé :  
  
```  
Data Source=MSSQL; Initial Catalog=AdventureWorks; Integrated Security=SSPI; MultipleActiveResultSets=True  
```  
  
 MARS avec OLTP en mémoire est fondamentalement identique à MARS dans le reste du moteur SQL. La liste suivante répertorie les différences lors de l’utilisation de MARS dans les tables optimisées en mémoire et les procédures stockées compilées en mode natif.  
  
 **MARS et tables optimisées en mémoire**  
  
 Voici les différences entre les tables sur disque et les tables mémoire optimisées lors de l’utilisation d’une connexion avec MARS activé :  
  
-   Deux instructions peuvent modifier des données dans le même objet cible, mais si elles tentent de modifier le même enregistrement, un conflit d’écriture entraîne l’échec de la nouvelle opération. Toutefois, si les deux opérations modifient des enregistrements différents, les opérations réussissent.  
  
-   Chaque instruction s’exécute sous le niveau d’isolation SNAPSHOT ; ainsi, les nouvelles opérations ne peuvent pas voir les modifications apportées par les instructions existantes. Même si les instructions simultanées sont exécutées dans le cadre de la même transaction, le moteur SQL crée des transactions dont l’étendue est définie par lot et isolées les unes des autres pour chaque instruction. Toutefois, les transactions dont l’étendue est définie par lot sont toujours liées, et la restauration d’une transaction dont l’étendue est définie par lot affecte les autres dans le même lot.  
  
-   Les opérations DDL ne sont pas autorisées dans les transactions utilisateur et échouent immédiatement.  
  
 **MARS et procédures stockées compilées en mode natif**  
  
 Les procédures stockées compilées en mode natif peuvent s’exécuter dans des connexions MARS et accorder l’exécution à une autre instruction uniquement lorsqu’un point d’arrêt temporaire est rencontré. Un point d’arrêt temporaire requiert une instruction SELECT, qui est la seule instruction au sein d’une procédure stockée compilée en mode natif à pouvoir accorder l’exécution à une autre instruction. Si une instruction SELECT n’est pas présente dans la procédure, elle ne s’arrêtera pas et s’exécutera jusqu’à la fin avant que d’autres instructions commencent.  
  
 **MARS et transactions OLTP en mémoire**  
  
 Les modifications apportées par les instructions et les blocs atomiques entrelacés sont isolées les unes des autres. Par exemple, si une instruction ou un bloc atomique effectue des modifications, puis accorde l’exécution à une autre instruction, la nouvelle instruction ne verra pas les modifications apportées par la première. En outre, quand la première instruction reprend l’exécution, elle ne voit pas les modifications apportées par les autres instructions. Les instructions ne voient que les modifications qui sont terminées et validées avant le début de l’instruction.  
  
 Une nouvelle transaction utilisateur peut être lancée dans la transaction utilisateur actuelle à l’aide de l’instruction BEGIN TRANSACTION - elle n’est prise en charge qu’en mode interop afin que le BEGIN TRANSACTION ne puisse être appelé qu’à partir d’une déclaration T-SQL, et non à partir d’une procédure stockée nativement compilée. Vous pouvez créer un point d’enregistrement dans une transaction à l’aide de SAVE TRANSACTION ou d’un appel aPI à la transaction. Enregistrer (save_point_name) pour revenir au point d’arrêt. Cette fonctionnalité est également activée uniquement à partir d’instructions T-SQL, et non à partir de procédures stockées compilées en mode natif.  
  
 **MARS et index columnstore**  
  
 SQL Server (à partir de la version 2016) prend en charge MARS avec les index columnstore. SQL Server 2014 utilise MARS pour les connexions en lecture seule à des tables avec un index columnstore.    Toutefois, SQL Server 2014 ne prend pas en charge MARS pour les opérations de langage de manipulation de données (DML) simultanées sur une table avec un index columnstore. Quand ce cas se produit, SQL Server met fin aux connexions et annule les transactions.   SQL Server 2012 a des index columnstore en lecture seule et MARS ne s’y applique pas.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Fournisseur OLE DB SQL Server Native Client  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur de DB OLE native Client prend en charge MARS par l’ajout de la propriété de initialisation de source de données SSPROP_INIT_MARSCONNECTION, qui est mise en œuvre dans l’ensemble de propriétés DBPROPSET_SQLSERVERDBINIT. De plus, un nouveau mot clé de chaîne de connexion, **MarsConn**, a été ajouté. Il accepte les valeurs **true** et **false** ; **false** est la valeur par défaut.  
  
 Le propriété de source de données DBPROP_MULTIPLECONNECTIONS a la valeur par défaut VARIANT_TRUE. Cela signifie que le fournisseur générera dynamiquement plusieurs connexions pour prendre en charge plusieurs objets command et rowset simultanés. Lorsque MARS est [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] activé, Native Client peut prendre en charge plusieurs objets de commande et de rangée sur une seule connexion, de sorte que MULTIPLE_CONNECTIONS est réglé pour VARIANT_FALSE par défaut.  
  
 Pour plus d'informations sur les améliorations apportées au jeu de propriétés DBPROPSET_SQLSERVERDBINIT, consultez [Propriétés d'initialisation et d'autorisation](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
### <a name="sql-server-native-client-ole-db-provider-example"></a>Exemple de fournisseur OLE DB de SQL Server Native Client  
 Dans cet exemple, un objet source [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de données est créé à l’aide du fournisseur Native OLE DB, et MARS est activé à l’aide de l’ensemble de propriété DBPROPSET_SQLSERVERDBINIT avant la création de l’objet de session.  
  
```cpp
#include <sqlncli.h>  
  
IDBInitialize *pIDBInitialize = NULL;  
IDBCreateSession *pIDBCreateSession = NULL;  
IDBProperties *pIDBProperties = NULL;  
  
// Create the data source object.  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL,  
   CLSCTX_INPROC_SERVER,  
   IID_IDBInitialize,   
    (void**)&pIDBInitialize);  
  
hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void**)&pIDBProperties);  
  
// Set the MARS property.  
DBPROP rgPropMARS;  
  
// The following is necessary since MARS is off by default.  
rgPropMARS.dwPropertyID = SSPROP_INIT_MARSCONNECTION;  
rgPropMARS.dwOptions = DBPROPOPTIONS_REQUIRED;  
rgPropMARS.dwStatus = DBPROPSTATUS_OK;  
rgPropMARS.colid = DB_NULLID;  
V_VT(&(rgPropMARS.vValue)) = VT_BOOL;  
V_BOOL(&(rgPropMARS.vValue)) = VARIANT_TRUE;  
  
// Create the structure containing the properties.  
DBPROPSET PropSet;  
PropSet.rgProperties = &rgPropMARS;  
PropSet.cProperties = 1;  
PropSet.guidPropertySet = DBPROPSET_SQLSERVERDBINIT;  
  
// Get an IDBProperties pointer and set the initialization properties.  
pIDBProperties->SetProperties(1, &PropSet);  
pIDBProperties->Release();  
  
// Initialize the data source object.  
hr = pIDBInitialize->Initialize();  
  
//Create a session object from a data source object.  
IOpenRowset * pIOpenRowset = NULL;  
hr = IDBInitialize->QueryInterface(IID_IDBCreateSession, (void**)&pIDBCreateSession));  
hr = pIDBCreateSession->CreateSession(  
   NULL,             // pUnkOuter  
   IID_IOpenRowset,  // riid  
  &pIOpenRowset ));  // ppSession  
  
// Create a rowset with a firehose mode cursor.  
IRowset *pIRowset = NULL;  
DBPROP rgRowsetProperties[2];  
  
// To get a firehose mode cursor request a   
// forward only read only rowset.  
rgRowsetProperties[0].dwPropertyID = DBPROP_IRowsetLocate;  
rgRowsetProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[0].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[0].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[0].vValue));  
rgRowsetProperties[0].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[0].vValue.boolVal = VARIANT_FALSE;  
  
rgRowsetProperties[1].dwPropertyID = DBPROP_IRowsetChange;  
rgRowsetProperties[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[1].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[1].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[1].vValue));  
rgRowsetProperties[1].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[1].vValue.boolVal = VARIANT_FALSE;  
  
DBPROPSET rgRowsetPropSet[1];  
rgRowsetPropSet[0].rgProperties = rgRowsetProperties  
rgRowsetPropSet[0].cProperties = 2  
rgRowsetPropSet[0].guidPropertySet = DBPROPSET_ROWSET;  
  
hr = pIOpenRowset->OpenRowset (NULL,  
   &TableID,  
   NULL,  
   IID_IRowset,  
   1,  
   rgRowsetPropSet  
   (IUnknown**)&pIRowset);  
```  
  
## <a name="sql-server-native-client-odbc-driver"></a>Pilote ODBC SQL Server Native Client  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] conducteur native Client ODBC prend en charge MARS par le biais d’ajouts aux fonctions [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) et [SQLGetConnectAttr.](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) SQL_COPT_SS_MARS_ENABLED a été ajouté pour accepter SQL_MARS_ENABLED_YES ou SQL_MARS_ENABLED_NO ; SQL_MARS_ENABLED_NO étant la valeur par défaut. En outre, un nouveau mot clé de chaîne de connexion, **Mars_Connection**, comme ajouté. Il accepte les valeurs « yes » ou « non » ; «no » étant la valeur par défaut.  
  
### <a name="sql-server-native-client-odbc-driver-example"></a>Exemple de pilote ODBC SQL Server Native Client  
 Dans cet exemple, la fonction **SQLSetConnectAttr** est utilisée pour activer MARS avant d’appeler la fonction **SQLDriverConnect** pour connecter la base de données. Une fois la connexion effectuée, deux fonctions **SQLExecDirect** sont appelées pour créer deux ensembles de résultats distincts sur la même connexion.  
  
```cpp
#include <sqlncli.h>  
  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_MARS_ENABLED, SQL_MARS_ENABLED_YES, SQL_IS_UINTEGER);  
SQLDriverConnect(hdbc, hwnd,   
   "DRIVER=SQL Server Native Client 10.0;  
   SERVER=(local);trusted_connection=yes;", SQL_NTS, szOutConn,   
   MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt1);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt2);  
  
// The 2nd execute would have failed with connection busy error if  
// MARS were not enabled.  
SQLExecDirect(hstmt1, L"SELECT * FROM Authors", SQL_NTS);  
SQLExecDirect(hstmt2, L"SELECT * FROM Titles", SQL_NTS);  
  
// Result set processing can interleave.  
SQLFetch(hstmt1);  
SQLFetch(hstmt2);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Caractéristiques des clients autochtones de SQL Server](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [Utilisation de jeux de résultats SQL Server par défaut](../../../relational-databases/native-client-odbc-cursors/implementation/using-sql-server-default-result-sets.md)  
  
  
