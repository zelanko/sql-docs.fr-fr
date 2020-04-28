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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 53531ff4a3b2e1441fabf22ec7a3ce12b15540eb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301411"
---
# <a name="transferring-data-in-its-binary-form"></a>Transfert de données dans leur forme binaire
Une application peut transférer en toute sécurité des données (dans le format interne utilisé par un SGBD spécifié) entre deux sources de données qui utilisent le même SGBD et la même plateforme matérielle. Pour un élément de données donné, les types de données SQL doivent être identiques dans les sources de données source et cible. Le type de données C est SQL_C_BINARY.  
  
 Lorsque l’application appelle **SQLFetch**, **SQLFetchScroll**ou **SQLGetData** pour extraire les données de la source de données source, le pilote récupère les données de la source de données et les transfère, sans conversion, vers un emplacement de stockage de type SQL_C_BINARY. Lorsque l’application appelle **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPutData ou SQLSetPos** pour envoyer les données à la source de données cible, le pilote récupère les données à partir de l’emplacement de stockage et les transfère, sans conversion, à la source de données cible.  
  
> [!NOTE]  
>  Les applications qui transfèrent des données (à l’exception des données binaires) de cette manière ne sont pas interopérables entre les SGBD.  
  
 **SQLCopyDesc** peut être utilisé pour copier des liaisons de lignes du SGBD source vers des liaisons de paramètres dans le SGBD cible.
