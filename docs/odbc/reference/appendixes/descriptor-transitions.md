---
title: Transitions descripteur (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- state transitions [ODBC], descriptor
- transitioning states [ODBC], descriptor
- descriptor transitions [ODBC]
ms.assetid: 0cf24fe6-5e3c-45fa-81b8-4f52ddf8501d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec5c26bdde8a0d470f2d93e753504bf1c51edcc0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307040"
---
# <a name="descriptor-transitions"></a>Transitions de descripteur
Les descripteurs de l’ODBC ont les trois états suivants.  
  
|State|Description|  
|-----------|-----------------|  
|D0 D0|Descripteur non affecté|  
|D1i D1i|Descripteur implicitement attribué|  
|D1e|Descripteur explicitement attribué|  
  
 Les tableaux suivants montrent comment chaque fonction ODBC affecte l’état descripteur.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|D0 D0<br /><br /> Non alloué|D1i D1i<br /><br /> Implicite|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|D1i[1]|--|--|  
|D1e[2]|--|--|  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_STMT.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DESC.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc (SQLCopyDesc)  
  
|D0 D0<br /><br /> Non alloué|D1i D1i<br /><br /> Implicite|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0 D0<br /><br /> Non alloué|D1i D1i<br /><br /> Implicite|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|--[1]|D0 D0|--|  
|(IH) [2]|(HY017)|D0 D0|  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_STMT.  
  
 Cette ligne montre les transitions lorsque *HandleType* a été SQL_HANDLE_DESC.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField et SQLGetDescRec  
  
|D0 D0<br /><br /> Non alloué|D1i D1i<br /><br /> Implicite|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField et SQLSetDescRec  
  
|D0 D0<br /><br /> Non alloué|D1i D1i<br /><br /> Implicite|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|(IH) [1]|--|--|  
  
 Cette ligne montre les transitions lorsque *DescriptorHandle* était la poignée d’un ARD, APD, ou IPD, ou (pour **SQLSetDescField**) lorsque *DescriptorHandle* était la poignée d’un IRD et *FieldIdentifier* a été SQL_DESC_ARRAY_STATUS_PTR ou SQL_DESC_ROWS_PROCESSED_PTR.  
  
## <a name="all-other-odbc-functions"></a>Toutes les autres fonctions ODBC  
  
|D0 D0<br /><br /> Non alloué|D1i D1i<br /><br /> Implicite|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|--|--|--|
