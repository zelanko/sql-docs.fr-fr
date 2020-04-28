---
title: bcp_control | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_control
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_control function
ms.assetid: 32187282-1385-4c52-9134-09f061eb44f5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b3d09d1f577c9af59ea085eefbf51e9a70558a36
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "73782877"
---
# <a name="bcp_control"></a>bcp_control
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Modifie les paramètres par défaut pour différents paramètres de contrôle pour une copie en bloc entre un fichier et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_control (  
        HDBC hdbc,  
        INT eOption,  
        void* iValue);  
```  
  
## <a name="arguments"></a>Arguments  
 *hdbc*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
 *eOption*  
 Prend l'une des valeurs suivantes :  
  
 BCPABORT  
 Arrête une opération de copie en bloc déjà en cours. Appelez **bcp_control** avec un *eOption* de BCPABORT à partir d’un autre thread pour arrêter l’exécution d’une opération de copie en bloc. Le paramètre *iValue* est ignoré.  
  
 BCPBATCH  
 Nombre de lignes par lot. La valeur par défaut est 0, ce qui indique soit que toutes les lignes sont dans une table, lorsque les données sont extraites, soit que toutes les lignes sont dans le fichier des données utilisateur, lorsque les données sont copiées vers un serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Une valeur inférieure à 1 rétablit la valeur par défaut de BCPBATCH.  
  
 BCPDELAYREADFMT  
 Une valeur booléenne, si la valeur est true, provoque la lecture de [bcp_readfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) lors de l’exécution. Si la valeur est false (valeur par défaut), bcp_readfmt lit immédiatement le fichier de format. Une erreur de séquence se produit si BCPDELAYREADFMT a la valeur true et que vous appelez bcp_columns ou bcp_setcolfmt.  
  
 Une erreur de séquence se produira également si `bcp_control(hdbc,` vous`, (void *)FALSE)` appelez BCPDELAYREADFMT `bcp_control(hdbc,` après`, (void *)TRUE)` avoir appelé BCPDELAYREADFMT et bcp_writefmt.  
  
 Pour plus d’informations, consultez [Découverte des métadonnées](../../relational-databases/native-client/features/metadata-discovery.md).  
  
 BCPFILECP  
 *iValue* contient le numéro de la page de codes pour le fichier de données. Vous pouvez spécifier le numéro de la page de codes, par exemple 1252 ou 850, ou l'une de ces valeurs :  
  
 BCPFILE_ACP : les données dans le fichier figurent dans la page de codes Microsoft Windows® du client.  
  
 BCPFILE_OEMCP : les données dans le fichier figurent dans la page de codes OEM du client (valeur par défaut).  
  
 BCPFILE_RAW : les données dans le fichier figurent dans la page de codes du serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 BCPFILEFMT  
 Numéro de version du format de fichier de données. Il peut s’agir de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]80 (), [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]90 (), [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 100 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)](ou), [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]110 () ou 120 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)](). 120 est la valeur par défaut. Cela s'avère utile pour exporter et importer des données dans des formats pris en charge par une version antérieure du serveur. Par exemple, pour importer des données obtenues à partir d’une colonne de texte [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] d’un serveur dans une colonne **varchar (max)** dans un [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] serveur ou ultérieur, vous devez spécifier 80. De même, si vous spécifiez 80 lors de l’exportation de données à partir d’une colonne **varchar (max)** , celles-ci sont enregistrées de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] la même façon que les colonnes de texte sont enregistrées au format [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] et peuvent être importées dans une colonne de texte d’un serveur.  
  
 BCPFIRST  
 Première ligne du fichier de données ou de la table à copier. La valeur par défaut est 1 ; une valeur inférieure à 1 rétablit la valeur par défaut de cette option.  
  
 BCPFIRSTEX  
 Pour les opérations bcp out, spécifie la première ligne de la table de base de données à copier dans le fichier de données.  
  
 Pour les opérations bcp in, spécifie la première ligne du fichier de données à copier dans la table de base de données.  
  
 Le paramètre *iValue* doit être l’adresse d’un entier 64 bits signé contenant la valeur. La valeur maximale qui peut être passée à BCPFIRSTEX est est 2 ^ 63-1.  
  
 BCPFMTXML  
 Spécifie que le fichier de format généré doit être au format XML. Il est désactivé par défaut.  
  
 Les fichiers au format XML offrent plus de souplesse, mais aussi quelques contraintes supplémentaires. Par exemple, vous ne pouvez pas spécifier simultanément le préfixe et la terminaison pour un champ, ce qui était possible dans les fichiers de format plus anciens.  
  
> [!NOTE]  
>  Les fichiers de format XML ne sont pris en charge que si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé conjointement avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 BCPHINTS  
 *iValue* contient un pointeur de chaîne de caractères SQLTCHAR. La chaîne adressée spécifie des indicateurs de traitement de copie en bloc [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou une instruction Transact-SQL qui retourne un jeu de résultats. Si une instruction Transact-SQL est spécifiée qui retourne plusieurs jeux de résultats, tous les jeux de résultats après le premier sont ignorés. Pour plus d’informations sur les indicateurs de traitement de copie en bloc, consultez [BCP Utility](../../tools/bcp-utility.md).  
  
 BCPKEEPIDENTITY  
 Quand *iValue* a la valeur true, spécifie que les fonctions de copie en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bloc insèrent des valeurs de données fournies pour les colonnes définies avec une contrainte d’identité. Le fichier d'entrée doit fournir des valeurs pour les colonnes d'identité. Si cela n'est pas défini, de nouvelles valeurs d'identités sont générées pour les lignes insérées. Toutes les données présentes dans le fichier pour les colonnes d'identité sont ignorées.  
  
 BCPKEEPNULLS  
 Spécifie si les valeurs de données vides dans le fichier sont converties en valeurs NULL dans la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Quand *iValue* a la valeur true, les valeurs vides sont converties [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en valeurs NULL dans la table. L'option par défaut consiste à convertir les valeurs vides en une valeur par défaut pour la colonne dans la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si une valeur par défaut existe.  
  
 BCPLAST  
 Dernière ligne à copier. L'option par défaut consiste à copier toutes les lignes ; une valeur inférieure à 1 rétablit la valeur par défaut de cette option.  
  
 BCPLASTEX  
 Pour les opérations bcp out, spécifie la dernière ligne de la table de base de données à copier dans le fichier de données.  
  
 Pour les opérations bcp in, spécifie la dernière ligne du fichier de données à copier dans la table de base de données.  
  
 Le paramètre *iValue* doit être l’adresse d’un entier 64 bits signé contenant la valeur. La valeur maximale qui peut être passée à BCPLASTEX est 2^63-1.  
  
 BCPMAXERRS  
 Nombre d’erreurs autorisées avant l’échec de l’opération de copie en bloc. La valeur par défaut est 10 ; une valeur inférieure à 1 rétablit la valeur par défaut de cette option. La copie en bloc impose 65 535 erreurs au maximum. Toute tentative d'attribution d'une valeur supérieure à 65 535 à cette option entraîne l'attribution de la valeur 65 535 à l'option.  
  
 BCPODBC  
 Si la valeur est TRUE, spécifie que les valeurs **DateTime** et **smalldatetime** enregistrées au format caractère utilisent le préfixe et le suffixe de séquence d’échappement d’horodateur ODBC. L’option BCPODBC s’applique uniquement aux DB_OUT.  
  
 Quand la valeur est FALSe, une valeur **DateTime** représentant le 1er janvier 1997 est convertie en chaîne de caractères : 1997-01-01 00:00:00.000. Si la valeur est TRUE, la même valeur **DateTime** est représentée comme suit : {ts' 1997-01-01 00:00:00.000 '}.  
  
 BCPROWCOUNT  
 Retourne le nombre de lignes affectées par l'opération BCP en cours (ou la dernière).  
  
 BCPTEXTFILE  
 Lorsque la valeur est TRUE, spécifie que le fichier de données est un fichier texte et non un fichier binaire. Si le fichier est un fichier texte, BCP détermine s'il est ou non un fichier Unicode en vérifiant le marqueur d'octet Unicode dans les deux premiers octets du fichier de données.  
  
 BCPUNICODEFILE  
 Lorsque la valeur est TRUE, spécifie que le fichier d'entrée est un fichier Unicode.  
  
 *iValue*  
 Valeur du *eOption*spécifié. *iValue* est une valeur entière (LongLong) transtypée en un pointeur void pour permettre une expansion future vers des valeurs 64 bits.  
  
## <a name="returns"></a>Retours  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 Cette fonction définit différents paramètres de contrôle pour les opérations de copie en bloc, y compris le nombre d'erreurs autorisées avant l'annulation de la copie en bloc, les numéros des première et dernière lignes à copier à partir d'un fichier de données, et la taille du lot.  
  
 Cette fonction est également utilisée pour spécifier l'instruction SELECT lors de la copie en bloc à partir du jeu de résultats [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'une instruction SELECT. Affectez à *eOption* la valeur valeur BCPHINTS et à *iValue* la valeur d’un pointeur vers une chaîne SQLTCHAR contenant l’instruction SELECT.  
  
 Ces paramètres de contrôle ne sont explicites qu'en cas de copie entre un fichier utilisateur et une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les paramètres de contrôle n’ont aucun effet sur les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lignes copiées dans avec [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
## <a name="example"></a>Exemple  
  
```  
// Variables like henv not specified.  
SQLHDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("address"), _T("address.add"), _T("addr.err"),  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the number of rows per batch.   
if (bcp_control(hdbc, BCPBATCH, (void*) 1000) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set file column count.   
if (bcp_columns(hdbc, 1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the file format.   
if (bcp_colfmt(hdbc, 1, 0, 0, SQL_VARLEN_DATA, '\n', 1, 1)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
printf_s("%ld rows processed by bulk copy.", nRowsProcessed);  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Bulk Copy Functions](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
