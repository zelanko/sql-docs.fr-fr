---
title: Fixation des tableaux de paramètres (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- binding parameter arrays [ODBC]
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 037afe23-052d-4f3a-8aa7-45302b199ad0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 73cfcde89e89edb87a4955cf0854c66a01d81e6f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283419"
---
# <a name="binding-arrays-of-parameters"></a>Liaison de tableaux de paramètres
Les applications qui utilisent des tableaux de paramètres lient les tableaux aux paramètres de l’énoncé SQL. Il existe deux styles de liaison :  
  
-   Lier un tableau à chaque paramètre. Chaque structure de données (tableau) contient toutes les données pour un seul paramètre. C’est ce qu’on appelle *la liaison colonne-sage* parce qu’il lie une colonne de valeurs pour un seul paramètre.  
  
-   Définissez une structure pour conserver les données de paramètres pour un ensemble entier de paramètres et lier un tableau de ces structures. Chaque structure de données contient les données d’une seule déclaration SQL. C’est ce qu’on appelle *la liaison de ligne-sage* parce qu’il lie une rangée de paramètres.  
  
 Comme lorsque l’application lie des variables uniques à des paramètres, elle appelle **SQLBindParameter** pour lier les tableaux aux paramètres. La seule différence est que les adresses transmises sont des adresses de tableau, pas des adresses à une variable unique. L’application définit l’attribut SQL_ATTR_PARAM_BIND_TYPE énoncé pour spécifier s’il utilise la liaison de colonne (par défaut) ou de la liaison de ligne. L’utilisation de la liaison de colonne ou de ligne est en grande partie une question de préférence d’application. Selon la façon dont le processeur accède à la mémoire, la liaison en ligne peut être plus rapide. Cependant, la différence est susceptible d’être négligeable, sauf pour un très grand nombre de rangées de paramètres.  
  
## <a name="column-wise-binding"></a>Liaison selon les colonnes  
 Lors de l’utilisation de la liaison de colonne-sage, une application lie un ou deux tableaux à chaque paramètre pour lequel les données doivent être fournies. Le premier tableau contient les valeurs de données, et le deuxième tableau contient des tampons de longueur/indicateur. Chaque tableau contient autant d’éléments qu’il y a de valeurs pour le paramètre.  
  
 La liaison de colonne-sage est la valeur par défaut. L’application peut également passer de la liaison de ligne-sage à la liaison colonne-sage en définissant l’attribut de l’SQL_ATTR_PARAM_BIND_TYPE déclaration. L’illustration suivante montre comment fonctionne la reliure de colonnes.  
  
 ![Montre comment fonctionne la colonne&#45;sage liaison](../../../odbc/reference/develop-app/media/pr31.gif "pr31")  
  
 Par exemple, le code suivant lie les tableaux de 10 éléments aux paramètres des colonnes PartID, Description et Prix, et exécute une déclaration pour insérer 10 lignes. Il utilise la liaison de colonne-sage.  
  
```  
#define DESC_LEN 51  
#define ARRAY_SIZE 10  
  
SQLCHAR *      Statement = "INSERT INTO Parts (PartID, Description,  Price) "  
                                                "VALUES (?, ?, ?)";  
SQLUINTEGER    PartIDArray[ARRAY_SIZE];  
SQLCHAR        DescArray[ARRAY_SIZE][DESC_LEN];  
SQLREAL        PriceArray[ARRAY_SIZE];  
SQLINTEGER     PartIDIndArray[ARRAY_SIZE], DescLenOrIndArray[ARRAY_SIZE],  
               PriceIndArray[ARRAY_SIZE];  
SQLUSMALLINT   i, ParamStatusArray[ARRAY_SIZE];  
SQLULEN ParamsProcessed;  
  
memset(DescLenOrIndArray, 0, sizeof(DescLenOrIndArray));  
memset(PartIDIndArray, 0, sizeof(PartIDIndArray));  
memset(PriceIndArray, 0, sizeof(PriceIndArray));  
  
// Set the SQL_ATTR_PARAM_BIND_TYPE statement attribute to use  
// column-wise binding.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_BIND_TYPE, SQL_PARAM_BIND_BY_COLUMN, 0);  
  
// Specify the number of elements in each parameter array.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMSET_SIZE, ARRAY_SIZE, 0);  
  
// Specify an array in which to return the status of each set of  
// parameters.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_STATUS_PTR, ParamStatusArray, 0);  
  
// Specify an SQLUINTEGER value in which to return the number of sets of  
// parameters processed.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMS_PROCESSED_PTR, &ParamsProcessed, 0);  
  
// Bind the parameters in column-wise fashion.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  PartIDArray, 0, PartIDIndArray);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  DescArray, DESC_LEN, DescLenOrIndArray);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  PriceArray, 0, PriceIndArray);  
  
// Set part ID, description, and price.  
for (i = 0; i < ARRAY_SIZE; i++) {  
   GetNewValues(&PartIDArray[i], DescArray[i], &PriceArray[i]);  
   PartIDIndArray[i] = 0;  
   DescLenOrIndArray[i] = SQL_NTS;  
   PriceIndArray[i] = 0;  
}  
  
// Execute the statement.  
SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Check to see which sets of parameters were processed successfully.  
for (i = 0; i < ParamsProcessed; i++) {  
   printf("Parameter Set  Status\n");  
   printf("-------------  -------------\n");  
   switch (ParamStatusArray[i]) {  
      case SQL_PARAM_SUCCESS:  
      case SQL_PARAM_SUCCESS_WITH_INFO:  
         printf("%13d  Success\n", i);  
         break;  
  
      case SQL_PARAM_ERROR:  
         printf("%13d  Error\n", i);  
         break;  
  
      case SQL_PARAM_UNUSED:  
         printf("%13d  Not processed\n", i);  
         break;  
  
      case SQL_PARAM_DIAG_UNAVAILABLE:  
         printf("%13d  Unknown\n", i);  
         break;  
  
   }  
}  
```  
  
## <a name="row-wise-binding"></a>Liaison selon les lignes  
 Lors de l’utilisation de la liaison en ligne, une application définit une structure pour chaque ensemble de paramètres. La structure contient un ou deux éléments pour chaque paramètre. Le premier élément détient la valeur du paramètre, et le deuxième élément détient le tampon longueur/indicateur. L’application alloue ensuite un éventail de ces structures, qui contient autant d’éléments qu’il y a de valeurs pour chaque paramètre.  
  
 La demande déclare la taille de la structure au conducteur avec l’attribut SQL_ATTR_PARAM_BIND_TYPE déclaration. L’application lie les adresses des paramètres de la première structure du tableau. Ainsi, le conducteur peut calculer l’adresse des données pour une ligne et une colonne  
  
```  
Address = Bound Address + ((Row Number - 1) * Structure Size) + Offset  
```  
  
 où les lignes sont numérotées de 1 à la taille de l’ensemble de paramètres. La compensation, si elle est définie, est la valeur soulignée par l’attribut SQL_ATTR_PARAM_BIND_OFFSET_PTR énoncé. L’illustration suivante montre comment fonctionne la reliure en ligne. Les paramètres peuvent être placés dans la structure dans n’importe quel ordre, mais sont indiqués dans l’ordre séquentiel pour la clarté.  
  
 ![Montre comment fonctionne la ligne&#45;sage liaison](../../../odbc/reference/develop-app/media/pr32.gif "pr32")  
  
 Le code suivant crée une structure avec des éléments pour les valeurs à stocker dans les colonnes PartID, Description et Prix. Il alloue ensuite un tableau de 10 éléments de ces structures et le lie aux paramètres pour les colonnes PartID, Description et Prix, en utilisant la liaison en ligne. Il exécute ensuite une déclaration pour insérer 10 lignes.  
  
```  
#define DESC_LEN 51  
#define ARRAY_SIZE 10  
  
typedef tagPartStruct {  
   SQLREAL       Price;  
   SQLUINTEGER   PartID;  
   SQLCHAR       Desc[DESC_LEN];  
   SQLINTEGER    PriceInd;  
   SQLINTEGER    PartIDInd;  
   SQLINTEGER    DescLenOrInd;  
} PartStruct;  
  
PartStruct PartArray[ARRAY_SIZE];  
SQLCHAR *      Statement = "INSERT INTO Parts (PartID, Description,  
                Price) "  
               "VALUES (?, ?, ?)";  
SQLUSMALLINT   i, ParamStatusArray[ARRAY_SIZE];  
SQLULEN ParamsProcessed;  
  
// Set the SQL_ATTR_PARAM_BIND_TYPE statement attribute to use  
// column-wise binding.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_BIND_TYPE, sizeof(PartStruct), 0);  
  
// Specify the number of elements in each parameter array.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMSET_SIZE, ARRAY_SIZE, 0);  
  
// Specify an array in which to return the status of each set of  
// parameters.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_STATUS_PTR, ParamStatusArray, 0);  
  
// Specify an SQLUINTEGER value in which to return the number of sets of  
// parameters processed.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMS_PROCESSED_PTR, &ParamsProcessed, 0);  
  
// Bind the parameters in row-wise fashion.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &PartArray[0].PartID, 0, &PartArray[0].PartIDInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  PartArray[0].Desc, DESC_LEN, &PartArray[0].DescLenOrInd);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &PartArray[0].Price, 0, &PartArray[0].PriceInd);  
  
// Set part ID, description, and price.  
for (i = 0; i < ARRAY_SIZE; i++) {  
   GetNewValues(&PartArray[i].PartID, PartArray[i].Desc, &PartArray[i].Price);  
   PartArray[0].PartIDInd = 0;  
   PartArray[0].DescLenOrInd = SQL_NTS;  
   PartArray[0].PriceInd = 0;  
}  
  
// Execute the statement.  
SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Check to see which sets of parameters were processed successfully.  
for (i = 0; i < ParamsProcessed; i++) {  
   printf("Parameter Set  Status\n");  
   printf("-------------  -------------\n");  
   switch (ParamStatusArray[i]) {  
      case SQL_PARAM_SUCCESS:  
      case SQL_PARAM_SUCCESS_WITH_INFO:  
         printf("%13d  Success\n", i);  
         break;  
  
      case SQL_PARAM_ERROR:  
         printf("%13d  Error\n", i);  
         break;  
  
      case SQL_PARAM_UNUSED:  
         printf("%13d  Not processed\n", i);  
         break;  
  
      case SQL_PARAM_DIAG_UNAVAILABLE:  
         printf("%13d  Unknown\n", i);  
         break;  
  
   }  
```
