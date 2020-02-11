---
title: SQLAllocConnect (pilote ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 70d48b12-def5-475c-b8e1-654a55fdfe0f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2889ef8e5c6f3a0db4e133ddf0bdd51fda338b40
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063294"
---
# <a name="sqlallocconnect-visual-foxpro-odbc-driver"></a>SQLAllocConnect (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau principal  
  
 Alloue de la mémoire pour un handle de connexion, *hdbc*, dans l’environnement identifié par *henv*. Le gestionnaire de pilotes traite cet appel et appelle le **SQLAllocConnect** du pilote à chaque appel de [SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md), **SQLBrowseConnect**ou [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) .  
  
 Pour plus d’informations, consultez [SQLAllocConnect](../../odbc/reference/syntax/sqlallocconnect-function.md) dans le *Guide de référence du programmeur ODBC*.
