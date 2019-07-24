---
title: Transitions de descripteur | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 44e9d92c7371451d6bfdd2e1513c3f8fdac8447b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68129997"
---
# <a name="descriptor-transitions"></a>Transitions de descripteur
Descripteurs ODBC ont trois états suivants.  
  
|État|Description|  
|-----------|-----------------|  
|D0|Descripteur non alloué|  
|D1i|Descripteurs alloués implicitement|  
|D1e|Descripteurs alloués explicitement|  
  
 Les tableaux suivants indiquent comment chaque fonction ODBC affecte l’état du descripteur.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|D0<br /><br /> Non alloué|D1i<br /><br /> Implicite|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|D1i[1]|--|--|  
|D1e[2]|--|--|  
  
 [1] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_STMT.  
  
 [2] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_DESC.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|D0<br /><br /> Non alloué|D1i<br /><br /> Implicite|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0<br /><br /> Non alloué|D1i<br /><br /> Implicite|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|--[1]|D0|--|  
|(IH) [2]|(HY017)|D0|  
  
 [1] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_STMT.  
  
 [2] cette ligne affiche les transitions quand *HandleType* a été SQL_HANDLE_DESC.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField et SQLGetDescRec  
  
|D0<br /><br /> Non alloué|D1i<br /><br /> Implicite|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField et SQLSetDescRec  
  
|D0<br /><br /> Non alloué|D1i<br /><br /> Implicite|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|(IH)[1]|--|--|  
  
 [1] cette ligne affiche les transitions quand *DescriptorHandle* a été le handle d’ARD, APD ou IPD, ou (pour **SQLSetDescField**) lorsque *DescriptorHandle* a été le handle d’un IRD et *FieldIdentifier* a été SQL_DESC_ARRAY_STATUS_PTR ou SQL_DESC_ROWS_PROCESSED_PTR.  
  
## <a name="all-other-odbc-functions"></a>Toutes les autres fonctions ODBC  
  
|D0<br /><br /> Non alloué|D1i<br /><br /> Implicite|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|--|--|--|
