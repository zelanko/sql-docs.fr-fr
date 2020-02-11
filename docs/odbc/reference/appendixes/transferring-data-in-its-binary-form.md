---
title: Transfert de données sous sa forme binaire | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], transferring in binary form
- transferring data in binary form [ODBC]
- binary data transfers [ODBC]
ms.assetid: 4b12a9de-51d0-416a-87f4-9bf84959cad9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a2897f882dc9dcd78ee8b919de01126d6be510c2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070026"
---
# <a name="transferring-data-in-its-binary-form"></a>Transfert de données dans leur forme binaire
Une application peut transférer en toute sécurité des données (dans le format interne utilisé par un SGBD spécifié) entre deux sources de données qui utilisent le même SGBD et la même plateforme matérielle. Pour un élément de données donné, les types de données SQL doivent être identiques dans les sources de données source et cible. Le type de données C est SQL_C_BINARY.  
  
 Lorsque l’application appelle **SQLFetch**, **SQLFetchScroll**ou **SQLGetData** pour extraire les données de la source de données source, le pilote récupère les données de la source de données et les transfère, sans conversion, vers un emplacement de stockage de type SQL_C_BINARY. Lorsque l’application appelle **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPutData ou SQLSetPos** pour envoyer les données à la source de données cible, le pilote récupère les données à partir de l’emplacement de stockage et les transfère, sans conversion, à la source de données cible.  
  
> [!NOTE]  
>  Les applications qui transfèrent des données (à l’exception des données binaires) de cette manière ne sont pas interopérables entre les SGBD.  
  
 **SQLCopyDesc** peut être utilisé pour copier des liaisons de lignes du SGBD source vers des liaisons de paramètres dans le SGBD cible.
