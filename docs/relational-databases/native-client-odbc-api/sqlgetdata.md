---
title: SQLGetData - France Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetData function
ms.assetid: 204848be-8787-45b4-816f-a60ac9d56fcf
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5ebda3de96cbd9a4a1ceadd62093420cc372a169
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302149"
---
# <a name="sqlgetdata"></a>SQLGetData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **SQLGetData** est utilisé pour récupérer les données de jeu de résultats sans les valeurs de colonne de liaison. **SQLGetData** peut être appelé successivement sur la même colonne pour récupérer de grandes quantités de données à partir d’une colonne avec un **texte,** **ntext**, ou type de données **d’image.**  
  
 Il n'y a aucune spécification exigeant qu'une application lie des variables pour extraire des données de jeu de résultats. Les données de n’importe quelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonne peuvent être récupérées auprès du conducteur native De l’ODBC en utilisant **SQLGetData**.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conducteur de Native Client ODBC n’est pas en charge de l’utilisation **de SQLGetData** pour récupérer des données dans l’ordre aléatoire de colonne. Toutes les colonnes non liées traitées avec **SQLGetData** doivent avoir desordinaux de colonne plus élevés que les colonnes liées dans l’ensemble de résultat. L'application doit traiter les données de la valeur d'ordinal de colonne indépendante la plus basse à la plus élevée. Toute tentative d'extraction de données d'une colonne d'ordinal inférieur provoque une erreur. Si l'application utilise des curseurs côté serveur pour signaler les lignes de jeu de résultats, l'application peut réextraire la ligne actuelle, puis extraire la valeur d'une colonne. Si une déclaration est exécutée sur le curseur par défaut lu uniquement et avant-seulement, vous devez ré-exécuter la déclaration pour sauvegarder **SQLGetData**.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conducteur de Native Client ODBC rapporte avec précision la longueur du **texte,** **du ntext**, et des données **d’image** récupérées à l’aide **de SQLGetData**. L’application peut faire bon usage du *StrLen_or_IndPtr* le retour du paramètre pour récupérer des données longues rapidement.  
  
> [!NOTE]  
>  Pour les types de grande valeur, *StrLen_or_IndPtr* retournera SQL_NO_TOTAL en cas de troncation de données.  
  
## <a name="sqlgetdata-support-for-enhanced-date-and-time-features"></a>Prise en charge de SQLGetData pour les fonctionnalités Date et Heure améliorées  
 Les valeurs de la colonne de résultat des types de date/heure sont converties comme décrit [dans Conversions de SQL à C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).  
  
 Pour plus d’informations, voir [Les améliorations de date et d’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgetdata-support-for-large-clr-udts"></a>Prise en charge SQLGetData pour les types CLR volumineux définis par l'utilisateur  
 **SQLGetData** prend en charge les grands types définis par les utilisateurs CLR (UDT). Pour plus d’informations, voir [Grands types définis par l’utilisateur CLR &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="example"></a>Exemple  
  
```  
SQLHDBC     hDbc = NULL;  
SQLHSTMT    hStmt = NULL;  
long        lEmpID;  
PBYTE       pPicture;  
SQLINTEGER  pIndicators[2];  
  
// Get an environment, connection, and so on.  
...  
  
// Get a statement handle and execute a command.  
SQLAllocHandle(SQL_HANDLE_STMT, hDbc, &hStmt);  
  
if (SQLExecDirect(hStmt,  
    (SQLCHAR*) "SELECT EmployeeID, Photo FROM Employees",  
    SQL_NTS) == SQL_ERROR)  
    {  
    // Handle error and return.  
    }  
  
// Retrieve data from row set.  
SQLBindCol(hStmt, 1, SQL_C_LONG, (SQLPOINTER) &lEmpID, sizeof(long),  
    &pIndicators[0]);  
  
while (SQLFetch(hStmt) == SQL_SUCCESS)  
    {  
    cout << "EmployeeID: " << lEmpID << "\n";  
  
    // Call SQLGetData to determine the amount of data that's waiting.  
    if (SQLGetData(hStmt, 2, SQL_C_BINARY, pPicture, 0, &pIndicators[1])  
        == SQL_SUCCESS_WITH_INFO)  
        {  
        cout << "Photo size: " pIndicators[1] << "\n\n";  
  
        // Get all the data at once.  
        pPicture = new BYTE[pIndicators[1]];  
        if (SQLGetData(hStmt, 2, SQL_C_DEFAULT, pPicture,  
            pIndicators[1], &pIndicators[1]) != SQL_SUCCESS)  
            {  
            // Handle error and continue.  
            }  
  
        delete [] pPicture;  
        }  
    else  
        {  
        // Handle error on attempt to get data length.  
        }  
    }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLGetData](https://go.microsoft.com/fwlink/?LinkId=59350)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
