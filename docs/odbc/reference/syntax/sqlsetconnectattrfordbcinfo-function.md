---
title: SQLSetConnectAttrForDbcInfo Function | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectAttrForDbcInfo function [ODBC]
ms.assetid: a28fadb9-b998-472a-b252-709507e92005
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 15366693f212690176620bd1b395dae856ff1302
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537299"
---
# <a name="sqlsetconnectattrfordbcinfo-function"></a>SQLSetConnectAttrForDbcInfo, fonction
**Conformité**  
 Version introduite : Conformité aux normes 3,81 ODBC : ODBC  
  
 **Résumé**  
 **SQLSetConnectAttrForDbcInfo** est identique à **SQLSetConnectAttr**, mais il définit l’attribut sur le jeton d’informations de connexion à la place de sur le handle de connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
  
SQLRETURN  SQLSetConnectAttrForDbcInfo(  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                SQLINTEGER            Attribute,  
                SQLPOINTER            ValuePtr,  
                SQLINTEGER            StringLength );  
```  
  
## <a name="arguments"></a>Arguments  
 *hDbcInfoToken*  
 [Entrée] Handle de jeton.  
  
 *Attribute*  
 [Entrée] Attribut à définir. La liste des attributs valides est spécifiques aux pilotes et les mêmes que pour [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 *ValuePtr*  
 [Entrée] Pointeur vers la valeur à associer à *attribut*. Selon la valeur de *attribut*, *ValuePtr* aura une valeur d’entier non signé 32 bits ou pointe vers une chaîne de caractères se terminant par null. Notez que si le *attribut* argument est une valeur spécifique au pilote, la valeur dans *ValuePtr* peut être un entier signé.  
  
 *StringLength*  
 [Entrée] Si *attribut* est un attribut défini par ODBC et *ValuePtr* pointe vers une chaîne de caractères ou une mémoire tampon binaire, cet argument doit être la longueur de **ValuePtr*. Pour les données de chaîne de caractères, cet argument doit contenir le nombre d’octets dans la chaîne.  
  
 Si *attribut* est un attribut défini par ODBC et *ValuePtr* est un entier, *StringLength* est ignoré.  
  
 Si *attribut* est un attribut définies par le pilote, l’application indique la nature de l’attribut pour le Gestionnaire de pilotes en définissant le *StringLength* argument. *StringLength* peut avoir les valeurs suivantes :  
  
-   Si *ValuePtr* est un pointeur vers une chaîne de caractères, puis *StringLength* est la longueur de la chaîne ou le SQL_NTS.  
  
-   Si *ValuePtr* est un pointeur vers une mémoire tampon binaire, puis l’application place le résultat de la SQL_LEN_BINARY_ATTR (*longueur*) macro dans *StringLength*. Cela place une valeur négative dans *StringLength*.  
  
-   Si *ValuePtr* est un pointeur vers une valeur autre qu’une chaîne de caractères ou une chaîne binaire, puis *StringLength* doit avoir la valeur SQL_IS_POINTER.  
  
-   Si *ValuePtr* contient une valeur de longueur fixe, puis *StringLength* est SQL_IS_INTEGER ou SQL_IS_UINTEGER, comme il convient.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Identique à [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), sauf que le Gestionnaire de pilotes utilisera un **HandleType** de SQL_HANDLE_DBC_INFO_TOKEN et un **gérer** de *hDbcInfoToken* .  
  
## <a name="remarks"></a>Notes  
 **SQLSetConnectAttrForDbcInfo** est identique à **SQLSetConnectAttr**, mais il définit l’attribut sur le jeton d’informations de connexion, au lieu de sur le handle de connexion. Par exemple, si **SQLSetConnectAttr** ne reconnaît pas un attribut, **SQLSetConnectAttrForDbcInfo** doit également retourner SQL_ERROR pour cet attribut.  
  
 Chaque fois que le pilote retourne SQL_ERROR ou SQL_INVALID_HANDLE, le pilote doit ignorer cet attribut pour calculer l’ID de pool. En outre, le Gestionnaire de pilotes obtiendront les informations de diagnostic à partir de *hDbcInfoToken*et retourne SQL_SUCCESS_WITH_INFO, à l’application dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) et [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md). Par conséquent, une application peut récupérer plus d’informations sur la raison pour laquelle certains attributs ne peut pas être définis.  
  
 Applications ne doivent pas appeler cette fonction directement. Un pilote ODBC qui prend en charge le regroupement de connexions prenant en charge les pilotes doive implémenter cette fonction.  
  
 Inclure sqlspi.h pour le développement de pilote ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Le regroupement de connexions prenant en charge de pilote](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Développement de la reconnaissance des pools de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
