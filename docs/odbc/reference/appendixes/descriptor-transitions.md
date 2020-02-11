---
title: Transitions de descripteurs | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68129997"
---
# <a name="descriptor-transitions"></a>Transitions de descripteur
Les descripteurs ODBC ont les trois États suivants.  
  
|State|Description|  
|-----------|-----------------|  
|D0|Descripteur non alloué|  
|D1i|Descripteur alloué implicitement|  
|D1e|Descripteur alloué explicitement|  
  
 Les tableaux suivants montrent comment chaque fonction ODBC affecte l’état du descripteur.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|D0<br /><br /> Non alloué|D1i<br /><br /> Implicite.|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|D1i [1]|--|--|  
|D1E [2]|--|--|  
  
 [1] cette ligne montre les transitions lorsque *comme HandleType* a été SQL_HANDLE_STMT.  
  
 [2] cette ligne affiche les transitions lorsque *comme HandleType* a été SQL_HANDLE_DESC.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|D0<br /><br /> Non alloué|D1i<br /><br /> Implicite.|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|IH|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0<br /><br /> Non alloué|D1i<br /><br /> Implicite.|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|--[1]|D0|--|  
|IH 2|(HY017)|D0|  
  
 [1] cette ligne montre les transitions lorsque *comme HandleType* a été SQL_HANDLE_STMT.  
  
 [2] cette ligne affiche les transitions lorsque *comme HandleType* a été SQL_HANDLE_DESC.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField et SQLGetDescRec  
  
|D0<br /><br /> Non alloué|D1i<br /><br /> Implicite.|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|IH|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField et SQLSetDescRec  
  
|D0<br /><br /> Non alloué|D1i<br /><br /> Implicite.|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|IH 1,0|--|--|  
  
 [1] cette ligne montre les transitions lorsque *DescriptorHandle* était le descripteur d’un ARD, APD ou IPD, ou (pour **SQLSetDescField**) quand *DescriptorHandle* était le descripteur d’un IRD et *FieldIdentifier* était SQL_DESC_ARRAY_STATUS_PTR ou SQL_DESC_ROWS_PROCESSED_PTR.  
  
## <a name="all-other-odbc-functions"></a>Toutes les autres fonctions ODBC  
  
|D0<br /><br /> Non alloué|D1i<br /><br /> Implicite.|D1e<br /><br /> Explicite|  
|------------------------|----------------------|----------------------|  
|--|--|--|
