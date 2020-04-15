---
title: Fonction SQLSetConnectAttrForDbcInfo (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9f43a0fc6cd02fe566579a543667f9a4c4c1a108
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301886"
---
# <a name="sqlsetconnectattrfordbcinfo-function"></a>SQLSetConnectAttrForDbcInfo, fonction
**Conformité**  
 Version introduite: ODBC 3.81 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLSetConnectAttrForDbcInfo** est le même que **SQLSetConnectAttr**, mais il définit l’attribut sur le jeton d’informations de connexion au lieu de sur la poignée de connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
  
SQLRETURN  SQLSetConnectAttrForDbcInfo(  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                SQLINTEGER            Attribute,  
                SQLPOINTER            ValuePtr,  
                SQLINTEGER            StringLength );  
```  
  
## <a name="arguments"></a>Arguments  
 *hDbcInfoToken (en anglais seulement)*  
 [Entrée] Poignée symbolique.  
  
 *Attribut*  
 [Entrée] Attribuer à définir. La liste des attributs valides est spécifique au conducteur et identique à celui de [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 *ValuePtr*  
 [Entrée] Pointeur à la valeur à associer à *Attribut*. Selon la valeur de *l’attribut*, *ValuePtr* sera une valeur insignable non signée 32 bits ou pointera vers une chaîne de caractères non terminée. Notez que si *l’argument d’attribut* est une valeur spécifique au conducteur, la valeur dans *ValuePtr* peut être un intégrateur signé.  
  
 *StringLength (en)*  
 [Entrée] Si *Attribut* est un attribut défini par ODBC et *que ValuePtr* pointe vers une chaîne de caractères ou un tampon binaire, cet argument doit être la longueur de *'ValuePtr*' Pour les données de chaîne de caractère, cet argument doit contenir le nombre d’octets dans la chaîne.  
  
 Si *Attribut* est un attribut défini par ODBC et *que ValuePtr* est un intégrateur, *StringLength* est ignoré.  
  
 Si *Attribut* est un attribut défini par le conducteur, l’application indique la nature de l’attribut au gestionnaire de conducteur en définissant l’argument *StringLength.* *StringLength* peut avoir les valeurs suivantes :  
  
-   Si *ValuePtr* est un pointeur d’une chaîne de caractères, *stringLength* est la longueur de la chaîne ou SQL_NTS.  
  
-   Si *ValuePtr* est un pointeur à un tampon binaire, alors l’application place le résultat de la SQL_LEN_BINARY_ATTR (*longueur)* macro dans *StringLength*. Cela place une valeur négative dans *StringLength*.  
  
-   Si *ValuePtr* est un pointeur à une valeur autre qu’une chaîne de caractère ou une chaîne binaire, alors *StringLength* devrait avoir la valeur SQL_IS_POINTER.  
  
-   Si *ValuePtr* contient une valeur fixe, *stringLength* est soit SQL_IS_INTEGER ou SQL_IS_UINTEGER, le cas échéant.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Idem que [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), sauf que le Driver Manager utilisera un **HandleType** de SQL_HANDLE_DBC_INFO_TOKEN et une **poignée** de *hDbcInfoToken*.  
  
## <a name="remarks"></a>Notes  
 **SQLSetConnectAttrForDbcInfo** est le même que **SQLSetConnectAttr**, mais il définit l’attribut sur le jeton d’information de connexion, au lieu de sur la poignée de connexion. Par exemple, si **SQLSetConnectAttr** ne reconnaît pas un attribut, **SQLSetConnectAttrForDbcInfo** devrait également retourner SQL_ERROR pour cet attribut.  
  
 Chaque fois que le conducteur retourne SQL_ERROR ou SQL_INVALID_HANDLE, le conducteur doit ignorer cet attribut pour calculer l’id de la piscine. De plus, le gestionnaire de chauffeur obtiendra les renseignements diagnostiques de *hDbcInfoToken*et retournera SQL_SUCCESS_WITH_INFO à l’application dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) et [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md). Par conséquent, une application peut récupérer des détails sur les raisons pour lesquelles certains attributs ne peuvent pas être définis.  
  
 Les applications ne doivent pas appeler cette fonction directement. Un conducteur ODBC qui prend en charge la mise en commun des connexions consciente du conducteur doit mettre en œuvre cette fonction.  
  
 Inclure sqlspi.h pour le développement du pilote ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Mise en commun des connexions conscientes du conducteur](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Développement de la reconnaissance des pools de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
