---
description: SQLGetConnectOption, fonction
title: Sqlgetconnectoption, fonction) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConnectOption
helpviewer_keywords:
- SQLGetConnectOption function [ODBC]
ms.assetid: 59cde899-7957-4b5e-8677-f34d3b859bfd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df3fd7dc9a024348c4371fabdbcabfab63a6f071
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421283"
---
# <a name="sqlgetconnectoption-function"></a>SQLGetConnectOption, fonction
**Conformité**  
 Version introduite : conformité des normes ODBC 1,0 : déconseillé  
  
 **Résumé**  
 Dans ODBC *3. x*, la fonction ODBC *2. x* **Sqlgetconnectoption,** a été remplacée par **SQLGetConnectAttr**. Pour plus d’informations, consultez [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md).  
  
> [!NOTE]
>  Pour plus d’informations sur le mappage de cette fonction par le gestionnaire de pilotes lorsqu’une application ODBC *2. x* utilise un pilote ODBC *3. x* , consultez [mappage des fonctions déconseillées](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) dans l’annexe G : instructions relatives aux pilotes pour la compatibilité descendante.  
> 
> [!NOTE]
>  L’attribut SQL_ASYNC_DBC_FUNCTION_ENABLE introduit dans ODBC 3,8 n’est pas pris en charge par **sqlgetconnectoption,**. Les applications qui utilisent l’opération asynchrone sur un handle de connexion doivent utiliser **SQLGetConnectAttr**.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
