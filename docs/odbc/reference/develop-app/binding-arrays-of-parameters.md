---
description: Liaison de tableaux de paramètres
title: Liaison de tableaux de paramètres | Microsoft Docs
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
ms.openlocfilehash: 529ea49d2697ffcf7b89217746420ab5cb298890
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429481"
---
# <a name="binding-arrays-of-parameters"></a>Liaison de tableaux de paramètres
Les applications qui utilisent des tableaux de paramètres lient les tableaux aux paramètres dans l’instruction SQL. Il existe deux styles de liaison :  
  
-   Liez un tableau à chaque paramètre. Chaque structure de données (tableau) contient toutes les données d’un seul paramètre. C’est ce que l’on appelle une liaison selon les *colonnes* , car elle lie une colonne de valeurs pour un paramètre unique.  
  
-   Définissez une structure qui contiendra les données de paramètre pour un ensemble complet de paramètres et liez un tableau de ces structures. Chaque structure de données contient les données d’une instruction SQL unique. C’est ce que l’on appelle une *liaison selon les lignes* , car elle lie une ligne de paramètres.  
  
 Comme lorsque l’application lie des variables uniques à des paramètres, elle appelle **SQLBindParameter** pour lier des tableaux aux paramètres. La seule différence est que les adresses transmises sont des adresses de tableau, et non des adresses à une seule variable. L’application définit l’attribut d’instruction SQL_ATTR_PARAM_BIND_TYPE pour spécifier s’il utilise la liaison basée sur les colonnes (valeur par défaut) ou la liaison selon les lignes. L’utilisation de la liaison selon les colonnes ou les lignes dépend principalement des préférences de l’application. Selon la façon dont le processeur accède à la mémoire, la liaison selon les lignes peut être plus rapide. Toutefois, la différence est susceptible d’être négligeable, à l’exception du très grand nombre de lignes de paramètres.  
  
## <a name="column-wise-binding"></a>Liaison selon les colonnes  
 Lors de l’utilisation d’une liaison selon les colonnes, une application lie un ou deux tableaux à chaque paramètre pour lequel des données doivent être fournies. Le premier tableau contient les valeurs de données, tandis que le second tableau contient des mémoires tampons de longueur/indicateur. Chaque tableau contient autant d’éléments qu’il y a de valeurs pour le paramètre.  
  
 La liaison selon les colonnes est la valeur par défaut. L’application peut également passer d’une liaison par ligne à une liaison selon les colonnes en définissant l’attribut d’instruction SQL_ATTR_PARAM_BIND_TYPE. L’illustration suivante montre le fonctionnement de la liaison selon les colonnes.  
  
 ![Illustre le fonctionnement de la liaison de colonne&#45;Wise](../../../odbc/reference/develop-app/media/pr31.gif "pr31")  
  
 Par exemple, le code suivant lie les tableaux à 10 éléments aux paramètres des colonnes PartId, description et Price, puis exécute une instruction pour insérer 10 lignes. Il utilise la liaison selon les colonnes.  
  
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
 Lors de l’utilisation d’une liaison selon les lignes, une application définit une structure pour chaque ensemble de paramètres. La structure contient un ou deux éléments pour chaque paramètre. Le premier élément contient la valeur de paramètre et le deuxième élément contient la mémoire tampon de longueur/d’indicateur. L’application alloue ensuite un tableau de ces structures, qui contient autant d’éléments qu’il y a de valeurs pour chaque paramètre.  
  
 L’application déclare la taille de la structure au pilote à l’aide de l’attribut d’instruction SQL_ATTR_PARAM_BIND_TYPE. L’application lie les adresses des paramètres dans la première structure du tableau. Ainsi, le pilote peut calculer l’adresse des données pour une ligne et une colonne particulières en tant que  
  
```  
Address = Bound Address + ((Row Number - 1) * Structure Size) + Offset  
```  
  
 où les lignes sont numérotées de 1 à la taille du jeu de paramètres. Le décalage, s’il est défini, est la valeur vers laquelle pointe l’attribut d’instruction SQL_ATTR_PARAM_BIND_OFFSET_PTR. L’illustration suivante montre le fonctionnement de la liaison selon les lignes. Les paramètres peuvent être placés dans la structure dans n’importe quel ordre, mais ils sont affichés dans l’ordre séquentiel pour plus de clarté.  
  
 ![Illustre le fonctionnement de la liaison de ligne&#45;Wise](../../../odbc/reference/develop-app/media/pr32.gif "pr32")  
  
 Le code suivant crée une structure avec des éléments pour les valeurs à stocker dans les colonnes PartId, description et Price. Il alloue ensuite un tableau de 10 éléments de ces structures et le lie aux paramètres des colonnes PartId, description et Price, à l’aide d’une liaison selon les lignes. Il exécute ensuite une instruction pour insérer 10 lignes.  
  
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
