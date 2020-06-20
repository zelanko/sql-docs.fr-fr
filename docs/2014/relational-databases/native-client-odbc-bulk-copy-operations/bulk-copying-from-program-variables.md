---
title: Copie en bloc à partir de variables de programme | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], program variables
- bcp_bind function
- mapping data types [ODBC]
- SQL Server Native Client ODBC driver, bulk copy
- data types [ODBC], bulk copying
- ODBC, bulk copy operations
- program variables [ODBC]
ms.assetid: e4284a1b-7534-4b34-8488-b8d05ed67b8c
author: rothja
ms.author: jroth
ms.openlocfilehash: 7a76f86f1be8012e0df2ed80960095eb83d6882e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021448"
---
# <a name="bulk-copying-from-program-variables"></a>Copie en bloc à partir de variables de programme
  Vous pouvez effectuer une copie en bloc directement à partir de variables de programme. Après avoir alloué des variables pour stocker les données d’une ligne et appelant [bcp_init](../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) pour démarrer la copie en bloc, appelez [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) pour chaque colonne afin de spécifier l’emplacement et le format de la variable de programme à associer à la colonne. Remplissez chaque variable avec des données, puis appelez [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) pour envoyer une ligne de données au serveur. Répétez le processus de remplissage des variables et en appelant **bcp_sendrow** jusqu’à ce que toutes les lignes aient été envoyées au serveur, puis appelez [bcp_done](../native-client-odbc-extensions-bulk-copy-functions/bcp-done.md) pour spécifier que l’opération est terminée.  
  
 Le paramètre **bcp_bind**_pData_ contient l’adresse de la variable liée à la colonne. Les données de chaque colonne peuvent être stockées de l'une des deux manières suivantes :  
  
-   Allocation d'une variable destinée à contenir les données.  
  
-   Allocation d'une variable indicateur suivie immédiatement de la variable de données.  
  
 La variable indicateur indique la longueur des données des colonnes de longueur variable et indique des valeurs NULL si la colonne autorise ces valeurs. Si seule une variable de données est utilisée, l’adresse de cette variable est stockée dans le paramètre **bcp_bind**_pData_ . Si une variable indicateur est utilisée, l’adresse de la variable indicateur est stockée dans le paramètre **bcp_bind**_pData_ . Les fonctions de copie en bloc calculent l’emplacement de la variable de données en ajoutant les paramètres **bcp_bind**_cbIndicator_ et *pData* .  
  
 **bcp_bind** prend en charge trois méthodes de gestion des données de longueur variable :  
  
-   Utilisez *cbData* avec uniquement une variable de données. Placez la longueur des données dans *cbData*. Chaque fois que la longueur des données à copier en bloc change, appelez [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)pour réinitialiser *cbData*. Si l’une des deux autres méthodes est utilisée, spécifiez SQL_VARLEN_DATA pour *cbData*. Si toutes les valeurs de données fournies pour une colonne sont NULL, spécifiez SQL_NULL_DATA pour *cbData*.  
  
-   Utilisation de variables indicateur. Dès qu'une nouvelle valeur de données est déplacée dans la variable de données, stockez la longueur de la valeur dans la variable indicateur. Si l’une des deux autres méthodes est utilisée, spécifiez 0 pour *cbIndicator*.  
  
-   Utilisation de pointeurs de terminateur. Chargez le paramètre **bcp_bind**_pterm_ avec l’adresse du modèle binaire qui termine les données. Si l’une des deux autres méthodes est utilisée, spécifiez NULL pour *pterm*.  
  
 Ces trois méthodes peuvent être utilisées sur le même appel de **bcp_bind** , auquel cas la spécification qui produit la plus petite quantité de données copiée est utilisée.  
  
 Le paramètre de_type_ **bcp_bind**utilise des identificateurs de type de données DB-Library, et non des identificateurs de type de données ODBC. Les identificateurs de type de données DB-Library sont définis dans sqlncli. h pour une utilisation avec la fonction ODBC **bcp_bind** .  
  
 Les fonctions de copie en bloc ne prennent pas en charge tous les types de données ODBC C. Par exemple, les fonctions de copie en bloc ne prennent pas en charge la structure ODBC SQL_C_TYPE_TIMESTAMP. Utilisez donc [SQLBindCol](../native-client-odbc-api/sqlbindcol.md) ou [SQLGetData](../native-client-odbc-api/sqlgetdata.md) pour convertir les données ODBC SQL_TYPE_TIMESTAMP en une variable SQL_C_CHAR. Si vous utilisez ensuite **bcp_bind** avec un paramètre de *type* SQLCHARACTER pour lier la variable à une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonne **DateTime** , les fonctions de copie en bloc convertissent la clause d’échappement timestamp dans la variable caractère au format DateTime approprié.  
  
 Le tableau suivant répertorie les types de données recommandés à utiliser lors du mappage d'un type de données SQL ODBC à un type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Type de données ODBC SQL|Type de données ODBC C|paramètre de *type* bcp_bind|Type de données SQL Server|  
|-----------------------|----------------------|--------------------------------|--------------------------|  
|SQL_CHAR|SQL_C_CHAR|SQLCHARACTER|**symbole**<br /><br /> **char**|  
|SQL_VARCHAR|SQL_C_CHAR|SQLCHARACTER|**varchar**<br /><br /> **character varying**<br /><br /> **char varying**<br /><br /> **sysname**|  
|SQL_LONGVARCHAR|SQL_C_CHAR|SQLCHARACTER|**text**|  
|SQL_WCHAR|SQL_C_WCHAR|SQLNCHAR|**nchar**|  
|SQL_WVARCHAR|SQL_C_WCHAR|SQLNVARCHAR|**nvarchar**|  
|SQL_WLONGVARCHAR|SQL_C_WCHAR|SQLNTEXT|**ntext**|  
|SQL_DECIMAL|SQL_C_CHAR|SQLCHARACTER|**decimal**<br /><br /> **decembre**<br /><br /> **money**<br /><br /> **smallmoney**|  
|SQL_NUMERIC|SQL_C_NUMERIC|SQLNUMERICN|**numeric**|  
|SQL_BIT|SQL_C_BIT|SQLBIT|**bit**|  
|SQL_TINYINT (signé)|SQL_C_SSHORT|SQLINT2|**smallint**|  
|SQL_TINYINT (non signé)|SQL_C_UTINYINT|SQLINT1|**tinyint**|  
|SQL_SMALL_INT (signé)|SQL_C_SSHORT|SQLINT2|**smallint**|  
|SQL_SMALL_INT (non signé)|SQL_C_SLONG|SQLINT4|**int**<br /><br /> **entier**|  
|SQL_INTEGER (signé)|SQL_C_SLONG|SQLINT4|**int**<br /><br /> **entier**|  
|SQL_INTEGER (non signé)|SQL_C_CHAR|SQLCHARACTER|**decimal**<br /><br /> **decembre**|  
|SQL_BIGINT (signé et non signé)|SQL_C_CHAR|SQLCHARACTER|**bigint**|  
|SQL_REAL|SQL_C_FLOAT|SQLFLT4|**real**|  
|SQL_FLOAT|SQL_C_DOUBLE|SQLFLT8|**float**|  
|SQL_DOUBLE|SQL_C_DOUBLE|SQLFLT8|**float**|  
|SQL_BINARY|SQL_C_BINARY|SQLBINARY|**binary**<br /><br /> **timestamp**|  
|SQL_VARBINARY|SQL_C_BINARY|SQLBINARY|**varbinary**<br /><br /> **binary varying**|  
|SQL_LONGVARBINARY|SQL_C_BINARY|SQLBINARY|**image**|  
|SQL_TYPE_DATE|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_TYPE_TIME|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_TYPE_TIMESTAMP|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_GUID|SQL_C_GUID|SQLUNIQUEID|**uniqueidentifier**|  
|SQL_INTERVAL_|SQL_C_CHAR|SQLCHARACTER|**char**|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]n’a pas de types de données **tinyint**, unsigned **smallint**ou unsigned **int** signés. Pour empêcher la perte de valeurs de données lors de la migration de ces types de données, créez la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec le plus grand type de données integer suivant. Pour empêcher les utilisateurs d'ajouter ultérieurement des valeurs en dehors de la plage autorisée par le type de données d'origine, appliquez une règle à la colonne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de manière à limiter les valeurs autorisées à la plage prise en charge par le type de données dans la source d'origine :  
  
```  
CREATE TABLE Sample_Ints(STinyIntCol   SMALLINT,  
USmallIntCol INT)  
GO  
CREATE RULE STinyInt_Rule  
AS   
@range >= -128 AND @range <= 127  
GO  
CREATE RULE USmallInt_Rule  
AS   
@range >= 0 AND @range <= 65535  
GO  
sp_bindrule STinyInt_Rule, 'Sample_Ints.STinyIntCol'  
GO  
sp_bindrule USmallInt_Rule, 'Sample_Ints.USmallIntCol'  
GO  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge directement les types de données interval. Toutefois, une application peut stocker des séquences d'échappement d'intervalle sous la forme de chaînes de caractères dans une colonne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de type character. L'application peut les lire pour une utilisation ultérieure, mais elles ne peuvent pas être utilisées dans des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 Les fonctions de copie en bloc peuvent être utilisées pour charger rapidement dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des données qui ont été lues à partir d'une source de données ODBC. Utilisez [SQLBindCol](../native-client-odbc-api/sqlbindcol.md) pour lier les colonnes d’un jeu de résultats à des variables de programme, puis utilisez **bcp_bind** pour lier les mêmes variables de programme à une opération de copie en bloc. L’appel de [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md) ou **SQLFetch** récupère ensuite une ligne de données de la source de données ODBC dans les variables de programme, et l’appel de [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) copie en bloc les données à partir des variables de programme vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Une application peut utiliser la fonction [bcp_colptr](../native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md) à chaque fois qu’elle a besoin de modifier l’adresse de la variable de données spécifiée à l’origine dans le paramètre **bcp_bind** _pData_ . Une application peut utiliser la fonction [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) à chaque fois qu’elle a besoin de modifier la longueur des données spécifiée à l’origine dans le paramètre **bcp_bind**_cbData_ .  
  
 Vous ne pouvez pas lire des données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans des variables de programme à l'aide de la copie en bloc. Il n'existe en effet pas de fonction similaire à « bcp_readrow ». Vous pouvez seulement envoyer des données de l'application au serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’opérations de copie en bloc &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)  
  
  
