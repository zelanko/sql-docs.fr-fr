---
title: Utilisation de SQLBindCol (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
- SQLBindCol function [ODBC], using
ms.assetid: 17277ab3-33ad-44d3-a81c-a26b5e338512
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: da49ad4db80b93d02534a0c4ecacdc2621c9cf8d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294629"
---
# <a name="using-sqlbindcol"></a>Utilisation de SQLBindCol
L’application lie les colonnes en appelant **SQLBindCol**. Cette fonction lie une colonne à la fois. Avec elle, l’application spécifie ce qui suit :  
  
-   Numéro de la colonne. Colonne 0 est la colonne de signet; cette colonne n’est pas incluse dans certains ensembles de résultats. Toutes les autres colonnes sont numérotées à partir du numéro 1. C’est une erreur de lier une colonne numérotée plus élevée qu’il n’y a de colonnes dans l’ensemble de résultats; cette erreur ne peut pas être détectée jusqu’à ce que l’ensemble de résultat a été créé, de sorte qu’il est retourné par **SQLFetch**, pas **SQLBindCol**.  
  
-   Le type de données C, l’adresse et la longueur des bytes de la variable liée à la colonne. Il s’agit d’une erreur de spécifier un type de données C auquel le type de données SQL de la colonne ne peut pas être converti; cette erreur pourrait ne pas être détectée jusqu’à ce que l’ensemble de résultat a été créé, de sorte qu’il est retourné par **SQLFetch**, pas **SQLBindCol**. Pour une liste de conversions prises en charge, voir [convertir les données de SQL à C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) dans l’annexe D : Data Types. Pour plus d’informations sur la longueur des byte, voir [Longueur tampon de données](../../../odbc/reference/develop-app/data-buffer-length.md).  
  
-   L’adresse d’un tampon longueur/indicateur. Le tampon longueur/indicateur est facultatif. Il est utilisé pour retourner la longueur d’or de données binaires ou de caractère ou de retourner SQL_NULL_DATA si les données sont NULL. Pour plus d’informations, voir [Utilisation de la longueur/ valeurs d’indicateur](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Lorsque **SQLBindCol** est appelé, le conducteur associe cette information à la déclaration. Lorsque chaque rangée de données est récupérée, elle utilise les informations pour placer les données pour chaque colonne dans les variables d’application liées.  
  
 Par exemple, le code suivant lie les variables aux colonnes SalesPerson et CustID. Les données pour les colonnes seront retournées dans *SalesPerson* et *CustID*. Étant donné que *SalesPerson* est un tampon de caractère, l’application spécifie sa longueur d’en-reste (11) afin que le conducteur puisse déterminer s’il faut tronquer les données. La longueur d’ord du titre retourné, ou si elle est NULL, sera retournée dans *SalesPersonLenOrInd*.  
  
 Parce que *CustID* est une variable d’intégrerie et a la longueur fixe, il n’est pas nécessaire de spécifier sa longueur d’ente; le conducteur suppose qu’il est **sizeof (** SQLUINTEGER **)**. La longueur des données d’identification des clients retournés, ou si elle est NULL, sera retournée dans *CustIDInd*. Notez que la demande ne s’intéresse qu’à savoir si le salaire est **)** NULL, parce que la longueur des byte est toujours taille de (SQLUINTEGER ) . **sizeof(**  
  
```  
SQLCHAR       SalesPerson[11];  
SQLUINTEGER   CustID;  
SQLINTEGER    SalesPersonLenOrInd, CustIDInd;  
SQLRETURN     rc;  
SQLHSTMT      hstmt;  
  
// Bind SalesPerson to the SalesPerson column and CustID to the   
// CustID column.  
SQLBindCol(hstmt, 1, SQL_C_CHAR, SalesPerson, sizeof(SalesPerson),  
            &SalesPersonLenOrInd);  
SQLBindCol(hstmt, 2, SQL_C_ULONG, &CustID, 0, &CustIDInd);  
  
// Execute a statement to get the sales person/customer of all orders.  
SQLExecDirect(hstmt, "SELECT SalesPerson, CustID FROM Orders ORDER BY SalesPerson",  
               SQL_NTS);  
  
// Fetch and print the data. Print "NULL" if the data is NULL. Code to   
// check if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   if (SalesPersonLenOrInd == SQL_NULL_DATA)   
            printf("NULL                     ");  
   else   
            printf("%10s   ", SalesPerson);  
   if (CustIDInd == SQL_NULL_DATA)   
         printf("NULL\n");  
   else   
            printf("%d\n", CustID);  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```  
  
 Le code suivant exécute une déclaration **SELECT** saisie par l’utilisateur et imprime chaque ligne de données dans l’ensemble de résultats. Étant donné que l’application ne peut pas prédire la forme de l’ensemble de résultat créé par l’instruction **SELECT,** elle ne peut pas lier les variables codées en dur au résultat défini comme dans l’exemple précédent. Au lieu de cela, l’application alloue un tampon qui contient les données et un tampon de longueur/indicateur pour chaque colonne de cette rangée. Pour chaque colonne, il calcule le décalage au début de la mémoire pour la colonne et ajuste ce décalage de sorte que les données et la longueur / tampons d’indicateur pour la colonne commencent sur les limites d’alignement. Il lie ensuite la mémoire à partir du décalage à la colonne. Du point de vue du conducteur, l’adresse de cette mémoire est indiscernable de l’adresse d’une variable liée dans l’exemple précédent. Pour plus d’informations sur l’alignement, voir [Alignement](../../../odbc/reference/develop-app/alignment.md).  
  
```  
// This application allocates a buffer at run time. For each column, this   
// buffer contains memory for the column's data and length/indicator.   
// For example:  
//      column 1         column 2      column 3      column 4  
// <------------><---------------><-----><------------>  
//      db1   li1   db2   li2   db3   li3   db4   li4  
//      |      |      |      |      |      |      |         |  
//      _____V_____V________V_______V___V___V______V_____V_  
// |__________|__|_____________|__|___|__|__________|__|  
//  
// dbn = data buffer for column n  
// lin = length/indicator buffer for column n  
  
// Define a macro to increase the size of a buffer so that it is a   
// multiple of the alignment size. Thus, if a buffer starts on an   
// alignment boundary, it will end just before the next alignment   
// boundary. In this example, an alignment size of 4 is used because   
// this is the size of the largest data type used in the application's   
// buffer--the size of an SDWORD and of the largest default C data type   
// are both 4. If a larger data type (such as _int64) was used, it would   
// be necessary to align for that size.  
#define ALIGNSIZE 4  
#define ALIGNBUF(Length) Length % ALIGNSIZE ? \  
                  Length + ALIGNSIZE - (Length % ALIGNSIZE) : Length  
  
SQLCHAR        SelectStmt[100];  
SQLSMALLINT    NumCols, *CTypeArray, i;  
SQLINTEGER *   ColLenArray, *OffsetArray, SQLType, *DataPtr;  
SQLRETURN      rc;   
SQLHSTMT       hstmt;  
  
// Get a SELECT statement from the user and execute it.  
GetSelectStmt(SelectStmt, 100);  
SQLExecDirect(hstmt, SelectStmt, SQL_NTS);  
  
// Determine the number of result set columns. Allocate arrays to hold   
// the C type, byte length, and buffer offset to the data.  
SQLNumResultCols(hstmt, &NumCols);  
CTypeArray = (SQLSMALLINT *) malloc(NumCols * sizeof(SQLSMALLINT));  
ColLenArray = (SQLINTEGER *) malloc(NumCols * sizeof(SQLINTEGER));  
OffsetArray = (SQLINTEGER *) malloc(NumCols * sizeof(SQLINTEGER));  
  
OffsetArray[0] = 0;  
for (i = 0; i < NumCols; i++) {  
   // Determine the column's SQL type. GetDefaultCType contains a switch   
   // statement that returns the default C type for each SQL type.  
   SQLColAttribute(hstmt, ((SQLUSMALLINT) i) + 1, SQL_DESC_TYPE, NULL, 0, NULL, (SQLPOINTER) &SQLType);  
   CTypeArray[i] = GetDefaultCType(SQLType);  
  
   // Determine the column's byte length. Calculate the offset in the   
   // buffer to the data as the offset to the previous column, plus the   
   // byte length of the previous column, plus the byte length of the   
   // previous column's length/indicator buffer. Note that the byte   
   // length of the column and the length/indicator buffer are increased   
   // so that, assuming they start on an alignment boundary, they will  
   // end on the byte before the next alignment boundary. Although this   
   // might leave some holes in the buffer, it is a relatively   
   // inexpensive way to guarantee alignment.  
   SQLColAttribute(hstmt, ((SQLUSMALLINT) i)+1, SQL_DESC_OCTET_LENGTH, NULL, 0, NULL, &ColLenArray[i]);  
   ColLenArray[i] = ALIGNBUF(ColLenArray[i]);  
   if (i)  
      OffsetArray[i] = OffsetArray[i-1]+ColLenArray[i-1]+ALIGNBUF(sizeof(SQLINTEGER));  
}  
  
// Allocate the data buffer. The size of the buffer is equal to the   
// offset to the data buffer for the final column, plus the byte length   
// of the data buffer and length/indicator buffer for the last column.  
void *DataPtr = malloc(OffsetArray[NumCols - 1] +  
               ColLenArray[NumCols - 1] + ALIGNBUF(sizeof(SQLINTEGER)));  
  
// For each column, bind the address in the buffer at the start of the   
// memory allocated for that column's data and the address at the start   
// of the memory allocated for that column's length/indicator buffer.  
for (i = 0; i < NumCols; i++)  
   SQLBindCol(hstmt,  
            ((SQLUSMALLINT) i) + 1,  
            CTypeArray[i],  
            (SQLPOINTER)((SQLCHAR *)DataPtr + OffsetArray[i]),  
            ColLenArray[i],  
            (SQLINTEGER *)((SQLCHAR *)DataPtr + OffsetArray[i] + ColLenArray[i]));  
  
// Retrieve and print each row. PrintData accepts a pointer to the data,   
// its C type, and its byte length/indicator. It contains a switch   
// statement that casts and prints the data according to its type. Code   
// to check if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   for (i = 0; i < NumCols; i++) {  
      PrintData((SQLCHAR *)DataPtr[OffsetArray[i]], CTypeArray[i],  
               (SQLINTEGER *)((SQLCHAR *)DataPtr[OffsetArray[i] + ColLenArray[i]]));  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```
