---
title: SQLTransact, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLTransact
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTransact
helpviewer_keywords:
- SQLTransact function [ODBC]
ms.assetid: 496249e0-8eff-4c60-8358-5543bc3ead9c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6c96c903b68dee2d1d215804d318d47b4c39a7a5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039497"
---
# <a name="sqltransact-function"></a>SQLTransact, fonction
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : Déconseillé  
  
 **Résumé**  
 Dans ODBC *3.x*, ODBC *2.x* fonction **SQLTransact** a été remplacé par **SQLEndTran**. Pour plus d’informations, consultez [SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  Ne prend pas en charge l’attribut SQL_ASYNC_DBC_FUNCTION_ENABLE, qui a été introduit dans ODBC 3.8, **SQLTransact**. Applications à l’aide d’une opération asynchrone sur un handle de connexion doivent utiliser **SQLEndTran**.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
