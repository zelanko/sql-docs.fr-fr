---
title: SQLCloseCursor_ODBC Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e1b61267d093e11bf7ea25158f5dc6a29ccba6a1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296299"
---
# <a name="sqlclosecursor_odbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation de la fonction **SQLCloseCursor** dans la bibliothèque de curseurs. Pour plus d’informations générales sur **SQLCloseCursor**, voir [SQLCloseCursor Function](../../../odbc/reference/syntax/sqlclosecursor-function.md).  
  
 La bibliothèque de curseurs n’appuie pas l’appel **SQLCloseCursor** sans curseur ouvert. Tentative de ce retour SQLSTATE 24000 (État de curseur invalide). Appeler **SQLFreeStmt** avec une *option* de SQL_CLOSE lorsqu’aucun curseur n’est ouvert est pris en charge par la bibliothèque de curseurs.
