---
title: Transfert de données sous sa forme binaire (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301411"
---
# <a name="transferring-data-in-its-binary-form"></a>Transfert de données dans leur forme binaire
Une application peut transférer en toute sécurité des données (sous la forme interne utilisée par un DBMS spécifié) entre deux sources de données qui utilisent la même plate-forme DBMS et matérielle. Pour un élément donné de données, les types de données SQL doivent être les mêmes dans les sources de données source et cible. Le type de données C est SQL_C_BINARY.  
  
 Lorsque l’application appelle **SQLFetch**, **SQLFetchScroll**, ou **SQLGetData** pour récupérer les données de la source de données, le conducteur récupère les données de la source de données et les transfère, sans conversion, à un emplacement de stockage de type SQL_C_BINARY. Lorsque l’application appelle **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPutData, ou SQLSetPos** pour envoyer les données à la source de données cible, le conducteur récupère les données de l’emplacement de stockage et les transfère, sans conversion, à la source de données cible.  
  
> [!NOTE]  
>  Les applications qui transfèrent toutes les données (sauf les données binaires) de cette manière ne sont pas interopérables chez les DBMS.  
  
 **SQLCopyDesc** peut être utilisé pour copier les fixations de ligne de la source DBMS aux fixations de paramètres dans le DBMS cible.
