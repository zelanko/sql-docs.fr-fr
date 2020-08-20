---
description: Mappage de types de données (ODBC)
title: Mappage de types de données (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [ODBC]
- result sets [ODBC], data types
- ODBC data types, mapping
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], mapping
- sql_variant data type
- SQL Server Native Client ODBC driver, data types
ms.assetid: 4ba0924d-9fca-4c48-aced-0a8d817b3dde
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a2cd0786cac3976bcb280422f177d19d8f86a3c7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465301"
---
# <a name="mapping-data-types-odbc"></a>Mappage de types de données (ODBC)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client mappe les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données SQL aux types de données SQL ODBC. Les sections suivantes traitent des types de données SQL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des types de données SQL ODBC auxquels ils sont mappés. Elles décrivent également les types de données SQL ODBC et leurs types de données C ODBC correspondants, ainsi que les conversions prises en charge et par défaut.  
  
> [!NOTE]  
>  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données **timestamp** est mappé sur le type de données SQL_BINARY ou SQL_VARBINARY ODBC, car les valeurs des colonnes **timestamp** ne sont pas des valeurs **DateTime** , mais des valeurs **Binary (8)** ou **varbinary (8)** qui indiquent la séquence de l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] activité sur la ligne. Si le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client rencontre une valeur SQL_C_WCHAR (Unicode) qui correspond à un nombre impair d'octets, l'octet impaire de fin est tronqué.  
  
## <a name="dealing-with-sql_variant-data-type-in-odbc"></a>Traitement du type de données sql_variant dans ODBC  
 La colonne de type de données **sql_variant** peut contenir l’un des types de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , à l’exception des objets de grande taille (LOB), tels que **Text**, **ntext**et **image**. Par exemple, la colonne peut contenir des valeurs **smallint** pour certaines lignes, des valeurs **float** pour d’autres lignes et des valeurs **CHAR/NCHAR** dans le reste.  
  
 Le type de données **sql_variant** est semblable au type de données **variant** dans Microsoft Visual Basic®.  
  
### <a name="retrieving-data-from-the-server"></a>Récupération de données à partir du serveur  
 ODBC n’a pas de concept de types variants, ce qui limite l’utilisation du type de données **sql_variant** avec un pilote ODBC dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , si la liaison est spécifiée, le type de données **sql_variant** doit être lié à l’un des types de données ODBC documentés. **SQL_CA_SS_VARIANT_TYPE**, un nouvel attribut propre au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client, retourne le type de données d’une instance de la colonne **sql_variant** à l’utilisateur.  
  
 Si aucune liaison n’est spécifiée, la fonction [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) peut être utilisée pour déterminer le type de données d’une instance dans la colonne **sql_variant** .  
  
 Pour récupérer **sql_variant** données, procédez comme suit.  
  
1.  Appelez **SQLFetch** pour positionner sur la ligne récupérée.  
  
2.  Appelez **SQLGetData**, en spécifiant SQL_C_BINARY pour le type et 0 pour la longueur des données. Cela force le pilote à lire l’en-tête **sql_variant** . L’en-tête fournit le type de données de cette instance dans la colonne **sql_variant** . **SQLGetData** retourne la taille (en octets) de la valeur.  
  
3.  Appelez [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) en spécifiant **SQL_CA_SS_VARIANT_TYPE** comme valeur d’attribut. Cette fonction retourne le type de données C de l’instance dans la colonne **sql_variant** au client.  
  
 Voici un segment de code qui illustre les étapes précédentes.  
  
```  
while ((retcode = SQLFetch (hstmt))==SQL_SUCCESS)  
{  
    if (retcode != SQL_SUCCESS && retcode != SQL_SUCCESS_WITH_INFO)  
    {  
        SQLError (NULL, NULL, hstmt, NULL,   
                    &lNativeError,szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    retcode = SQLGetData (hstmt, 1, SQL_C_BINARY,   
                                pBuff,0,&Indicator);//Figure out the length  
    if (retcode != SQL_SUCCESS_WITH_INFO && retcode != SQL_SUCCESS)  
    {  
        SQLError (NULL, NULL, hstmt, NULL, &lNativeError,   
                    szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    printf_s ("Byte length : %d ",Indicator); //Print out the byte length  
  
    int iValue = 0;  
    retcode = SQLColAttribute (hstmt, 1, SQL_CA_SS_VARIANT_TYPE, NULL,   
                                        NULL,NULL,&iValue);  //Figure out the type  
    printf_s ("Sub type = %d ",iValue);//Print the type, the return is C_type of the column]  
  
// Set up a new binding or do the SQLGetData on that column with   
// the appropriate type  
}  
```  
  
 Si l’utilisateur crée la liaison à l’aide de [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md), le pilote lit les métadonnées et les données. Le pilote convertit ensuite les données en un type ODBC approprié tel que spécifié dans la liaison.  
  
### <a name="sending-data-to-the-server"></a>Envoi de données au serveur  
 **SQL_SS_VARIANT**, un nouveau type de données spécifique au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client, est utilisé pour les données envoyées à une colonne **sql_variant** . Lors de l’envoi de données au serveur à l’aide de paramètres (par exemple, INSERT dans des valeurs TableName ( ?, ?)), [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) est utilisé pour spécifier les informations sur les paramètres, y compris le type C et le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type correspondant. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC native client convertit le type de données C en un des sous-types **sql_variant** appropriés.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des résultats &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
