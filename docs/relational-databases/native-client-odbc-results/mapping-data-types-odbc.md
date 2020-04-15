---
title: Types de données cartographiques (ODBC) Microsoft Docs
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
ms.openlocfilehash: 92426c854758d07a9d62ec57510d202b870dd9f2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304624"
---
# <a name="mapping-data-types-odbc"></a>Mappage de types de données (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conducteur de Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client ODBC cartographie les types de données SQL aux types de données SQL D’ODBC. Les sections suivantes traitent des types de données SQL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des types de données SQL ODBC auxquels ils sont mappés. Elles décrivent également les types de données SQL ODBC et leurs types de données C ODBC correspondants, ainsi que les conversions prises en charge et par défaut.  
  
> [!NOTE]  
>  Les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]cartes de type de données **timetamp** à la SQL_BINARY ou SQL_VARBINARY type de données ODBC parce que les valeurs dans les colonnes **timetamp** ne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont pas des valeurs **de date,** mais **binaires(8)** ou **varbinaires(8)** valeurs qui indiquent la séquence d’activité sur la ligne. Si le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client rencontre une valeur SQL_C_WCHAR (Unicode) qui correspond à un nombre impair d'octets, l'octet impaire de fin est tronqué.  
  
## <a name="dealing-with-sql_variant-data-type-in-odbc"></a>Traitement du type de données sql_variant dans ODBC  
 La colonne **de** type de données sql_variant peut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenir n’importe lequel des types de données dans des objets à l’exception des grands objets (LOB), tels que **le texte,** le **ntext,** et **l’image**. Par exemple, la colonne peut contenir des valeurs **de petite teinte** pour certaines lignes, des valeurs de **flottement** pour d’autres rangées et des valeurs **d’omble/nchar** dans le reste.  
  
 Le type de données **sql_variant** est similaire au type de données **Variant** dans Microsoft Visual Basic®.  
  
### <a name="retrieving-data-from-the-server"></a>Récupération de données à partir du serveur  
 ODBC n’a pas de concept de types **sql_variant** de variantes, limitant l’utilisation du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de données sql_variant avec un pilote ODBC dans . Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], si la liaison est spécifiée, le type de données **sql_variant** doit être lié à l’un des types documentés de données ODBC. **SQL_CA_SS_VARIANT_TYPE**, un nouvel attribut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifique au pilote native ODBC, renvoie le type de données d’une instance dans la colonne **sql_variant** à l’utilisateur.  
  
 Si aucune liaison n’est spécifiée, la fonction [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) peut être utilisée pour déterminer le type de données d’une instance dans la colonne **sql_variant.**  
  
 Pour récupérer **sql_variant** données, suivez ces étapes.  
  
1.  Appelez **SQLFetch** pour positionner la rangée récupérée.  
  
2.  Appelez **SQLGetData**, en précisant SQL_C_BINARY pour le type et 0 pour la longueur des données. Cela oblige le conducteur à lire **l’en-tête sql_variant.** L’en-tête fournit le type de données de cette instance dans la colonne **sql_variant.** **SQLGetData** retourne la taille (dans les octets) de la valeur.  
  
3.  Appelez [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) en spécifiant **SQL_CA_SS_VARIANT_TYPE** comme valeur d’attribut. Cette fonction retournera le type de données C de l’instance dans la colonne **sql_variant** au client.  
  
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
  
 Si l’utilisateur crée la liaison à l’aide [de SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md), le conducteur lit les métadonnées et les données. Le pilote convertit ensuite les données en un type ODBC approprié tel que spécifié dans la liaison.  
  
### <a name="sending-data-to-the-server"></a>Envoi de données au serveur  
 **SQL_SS_VARIANT**, un nouveau type de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données spécifique au pilote native ODBC, est utilisé pour les données envoyées à une colonne **de sql_variant.** Lors de l’envoi de données au serveur à l’aide de paramètres (par exemple, INSERT INTO TableName VALUES (?,?)), [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) est utilisé pour spécifier les informations de paramètres, y compris le type C et le type correspondant. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conducteur de Native Client ODBC convertira le type de données C en l’un des sous-types **sql_variant** appropriés.  
  
## <a name="see-also"></a>Voir aussi  
 [Résultats de traitement &#40;&#41;ODBC](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
