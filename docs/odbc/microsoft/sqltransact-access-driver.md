---
description: SQLTransact (pilote Access)
title: SQLTransact (pilote Access) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLTransact
- SQLTransact function [ODBC], Access Driver
ms.assetid: 892b79c7-9e20-4d1f-bc60-d4b25694ca25
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7e9b00f8f5a12af2d3823171d22ad53106569352
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339672"
---
# <a name="sqltransact-access-driver"></a>SQLTransact (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote d’accès. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Lorsque le pilote Microsoft Access est utilisé, SQL_COMMIT et SQL_ROLLBACK sont pris en charge pour l’argument *ftype* dans un appel à **SQLTransact**.  
  
 Si une défaillance se produit pendant le processus de validation, la base de données affectée peut être réparée à l’aide de l’option réparer la base de données dans le programme d’installation du pilote Microsoft Access ou à l’aide du mot clé REPAIR_DB dans la fonction **SQLConfigDataSource** .
