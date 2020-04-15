---
title: SQLTransact (Chauffeur d’accès) Microsoft Docs
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
ms.openlocfilehash: 4f88d3154925ab589a8519cb9205da03e8c3dc08
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299261"
---
# <a name="sqltransact-access-driver"></a>SQLTransact (pilote Access)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Access Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Lorsque le pilote Microsoft Access est utilisé, SQL_COMMIT et SQL_ROLLBACK sont pris en charge pour *l’argument fType* dans un appel à **SQLTransact**.  
  
 Si une défaillance se produit pendant le processus de validation, la base de données affectée peut être réparée à l’aide de l’option Base de données de réparation dans la configuration du pilote Microsoft Access, ou par l’utilisation du mot clé REPAIR_DB dans la fonction **SQLConfigDataSource.**
