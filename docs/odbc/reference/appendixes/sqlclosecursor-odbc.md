---
title: SQLCloseCursor_ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLCloseCursor function [ODBC], ODBC
ms.assetid: 5e47e3f7-e1b8-451f-bf75-daa19b7c7271
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 827f7195c5d4eb4f67cb3298b75519a5583053d1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47715117"
---
# <a name="sqlclosecursorodbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique explique comment utiliser le **SQLCloseCursor** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLCloseCursor**, consultez [SQLCloseCursor, fonction](../../../odbc/reference/syntax/sqlclosecursor-function.md).  
  
 La bibliothèque de curseurs ne prend pas en charge l’appel **SQLCloseCursor** sans un curseur ouvert. Cette tentative retourne SQLSTATE 24000 (état de curseur non valide). Appel **SQLFreeStmt** avec un *Option* de SQL_CLOSE lorsque aucun curseur n’est ouvert est pris en charge par la bibliothèque de curseurs.
