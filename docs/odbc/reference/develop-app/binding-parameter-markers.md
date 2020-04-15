---
title: Marqueurs de paramètres contraignants (en anglais) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306390"
---
# <a name="binding-parameter-markers"></a>Liaison de marqueurs de paramètre
L’application lie les paramètres en appelant **SQLBindParameter**. **SQLBindParameter** lie un paramètre à la fois. Avec elle, l’application spécifie ce qui suit :  
  
-   Le numéro de paramètre. Les paramètres sont numérotés dans l’ordre de paramètres croissant dans l’énoncé SQL, à commencer par le numéro 1. Bien qu’il soit légal de spécifier un nombre de paramètres supérieur au nombre de paramètres dans l’énoncé SQL, la valeur du paramètre sera ignorée lorsque l’instruction sera exécutée.  
  
-   Le type de paramètre (entrée, entrée/sortie ou sortie). À l’exception des paramètres des appels de procédure, tous les paramètres sont des paramètres d’entrée. Pour plus d’informations, voir [Paramètres de procédure](../../../odbc/reference/develop-app/procedure-parameters.md), plus tard dans cette section.  
  
-   Le type de données C, l’adresse et la longueur des bytes de la variable liée au paramètre. Le conducteur doit être en mesure de convertir les données du type de données C au type de données SQL ou une erreur est retournée. Pour une liste de conversions prises en charge, voir [convertir les données de C à SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) dans l’annexe D : Data Types.  
  
-   Le type de données SQL, la précision et l’échelle du paramètre lui-même.  
  
-   L’adresse d’un tampon longueur/indicateur. Il fournit la longueur d’orteil des données binaires ou de caractère, spécifie que les données sont NULL, ou spécifie que les données seront envoyées avec **SQLPutData**. Pour plus d’informations, voir [Utilisation de la longueur/ valeurs d’indicateur](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Par exemple, le code suivant lie *SalesPerson* et *CustID* aux paramètres des colonnes SalesPerson et CustID. Parce que *SalesPerson* contient des données de caractère, qui est de longueur variable, le code spécifie la longueur des *byte* de SalesPerson (11) et lie *SalesPersonLenOrInd* pour contenir la longueur des byte des données dans *SalesPerson*. Ces informations ne sont pas nécessaires pour *CustID* car elles contiennent des données integer, qui sont de longueur fixe.  
  
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
  
 Lorsque **SQLBindParameter** est appelé, le conducteur stocke cette information dans la structure pour la déclaration. Lorsque l’instruction est exécutée, elle utilise les informations pour récupérer les données de paramètres et les envoyer à la source de données.  
  
> [!NOTE]  
>  Dans ODBC 1.0, les paramètres étaient liés à **SQLSetParam**. Le Driver Manager cartographie les appels entre **SQLSetParam** et **SQLBindParameter**, selon les versions d’ODBC utilisées par l’application et le conducteur.
