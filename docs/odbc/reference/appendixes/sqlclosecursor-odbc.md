---
description: SQLCloseCursor_ODBC
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d91ce573a48602ad6dce4f0cb0759c2c8dddd3aa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466051"
---
# <a name="sqlclosecursor_odbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 Cette rubrique traite de l’utilisation de la fonction **SQLCloseCursor** dans la bibliothèque de curseurs. Pour obtenir des informations générales sur **SQLCloseCursor**, consultez [fonction SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md).  
  
 La bibliothèque de curseurs ne prend pas en charge l’appel de **SQLCloseCursor** sans curseur ouvert. Si vous tentez cette opération, SQLSTATE 24000 (état de curseur non valide) est retourné. L’appel de **SQLFreeStmt** avec une *option* de SQL_CLOSE quand aucun curseur n’est ouvert est pris en charge par la bibliothèque de curseurs.
