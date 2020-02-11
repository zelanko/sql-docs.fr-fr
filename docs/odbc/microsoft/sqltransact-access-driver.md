---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f4d4b3d8d417591bd72dde22240c81a91d80f990
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948973"
---
# <a name="sqltransact-access-driver"></a>SQLTransact (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote d’accès. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Lorsque le pilote Microsoft Access est utilisé, SQL_COMMIT et SQL_ROLLBACK sont pris en charge pour l’argument *ftype* dans un appel à **SQLTransact**.  
  
 Si une défaillance se produit pendant le processus de validation, la base de données affectée peut être réparée à l’aide de l’option réparer la base de données dans le programme d’installation du pilote Microsoft Access ou à l’aide du mot clé REPAIR_DB dans la fonction **SQLConfigDataSource** .
