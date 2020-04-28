---
title: Marqueurs de paramètres de liaison | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- parameter markers [ODBC]
- binding parameter markers [ODBC]
ms.assetid: fe88c1c2-4ee4-45e0-8500-b8c25c047815
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be99bc884a8baa66f3d632ee4731985f0cc85732
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306390"
---
# <a name="binding-parameter-markers"></a>Liaison de marqueurs de paramètre
L’application lie les paramètres en appelant **SQLBindParameter**. **SQLBindParameter** lie un paramètre à la fois. Avec celle-ci, l’application spécifie les éléments suivants :  
  
-   Numéro du paramètre. Les paramètres sont numérotés dans l’ordre des paramètres d’incrémentation dans l’instruction SQL, en commençant par le chiffre 1. S’il est autorisé de spécifier un nombre de paramètres supérieur au nombre de paramètres dans l’instruction SQL, la valeur du paramètre est ignorée lors de l’exécution de l’instruction.  
  
-   Type de paramètre (entrée, entrée/sortie ou sortie). À l’exception des paramètres dans les appels de procédure, tous les paramètres sont des paramètres d’entrée. Pour plus d’informations, consultez [paramètres de procédure](../../../odbc/reference/develop-app/procedure-parameters.md), plus loin dans cette section.  
  
-   Le type de données C, l’adresse et la longueur en octets de la variable liée au paramètre. Le pilote doit être en mesure de convertir les données du type de données C en type de données SQL, faute de quoi une erreur est retournée. Pour obtenir la liste des conversions prises en charge, consultez [conversion de données de C en types de données SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) dans l’annexe D : types de données.  
  
-   Le type de données SQL, la précision et l’échelle du paramètre lui-même.  
  
-   Adresse d’une mémoire tampon de longueur/d’indicateur. Il fournit la longueur en octets des données binaires ou de type caractère, spécifie que les données sont NULL, ou spécifie que les données seront envoyées avec **SQLPutData**. Pour plus d’informations, consultez [utilisation des valeurs de longueur/indicateur](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Par exemple, le code suivant lie *SalesPerson* et *CustID* aux paramètres des colonnes SalesPerson et CustID. Étant donné que *SalesPerson* contient des données de type caractère, dont la longueur est variable, le code spécifie la longueur en octets du *vendeur* (11) et lie *SalesPersonLenOrInd* pour contenir la longueur en octets des données dans le *vendeur*. Ces informations ne sont pas nécessaires pour *CustID* , car elles contiennent des données de type entier, qui sont de longueur fixe.  
  
```  
SQLCHAR       SalesPerson[11];  
SQLINTEGER    SalesPersonLenOrInd, CustIDInd;  
SQLUINTEGER   CustID;  
  
// Bind SalesPerson to the parameter for the SalesPerson column and  
// CustID to the parameter for the CustID column.  
SQLBindParameter(hstmt1, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 10, 0,  
                  SalesPerson, sizeof(SalesPerson), &SalesPersonLenOrInd);  
SQLBindParameter(hstmt1, 2, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 10, 0,  
                  &CustID, 0, &CustIDInd);  
  
// Set values of salesperson and customer ID and length/indicators.  
strcpy_s((char*)SalesPerson, _countof(SalesPerson), "Garcia");  
SalesPersonLenOrInd = SQL_NTS;  
CustID = 1331;  
CustIDInd = 0;  
  
// Execute a statement to get data for all orders made to the specified  
// customer by the specified salesperson.  
SQLExecDirect(hstmt1,"SELECT * FROM Orders WHERE SalesPerson=? AND CustID=?",SQL_NTS);  
```  
  
 Lorsque **SQLBindParameter** est appelé, le pilote stocke ces informations dans la structure de l’instruction. Lorsque l’instruction est exécutée, elle utilise les informations pour récupérer les données de paramètre et les envoyer à la source de données.  
  
> [!NOTE]  
>  Dans ODBC 1,0, les paramètres étaient liés à **SQLSetParam,**. Le gestionnaire de pilotes mappe les appels entre **SQLSetParam,** et **SQLBindParameter**, en fonction des versions de ODBC utilisées par l’application et le pilote.
